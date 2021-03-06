<!--
{
"name": "js-module",
"version" : "0.1",
"title" : "JavaScript Essentials for the Brightcove Player",
"description" : "Learn to use JavaScript to control the Brightcove Player",
"homepage" : "//docs.brightcove.com/en/video-cloud/index.html",
"freshnessDate" : 2015-09-26,
"license" : "CC BY 4.0"
}
-->

<!-- @section -->

# Getting Started

If you already know the basics of JavaScript, you can move right on to the next section. If you're just starting, however, there is a lot of complexity to JavaScript, and you need to learn the basic features of the language. Here's a very good tutorial for beginners:

<!-- @link, "url" : "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide", "text": "JavaScript Guide" -->

Take your time with that - practice spent on the basics will help you later on. Some basic things you need to know about are:

- declaring variables
- conditional statements (if...else)
- for loops
- defining and calling functions
- array and object data types

You also need to understand [events](https://developer.mozilla.org/en-US/docs/Web/Events), because much of the scripting you do in relation to the player will be in response to some event. You also need to feel comfortable with data structures like objects and arrays.

Take, for example, an array of objects:

```js
var items = [
    {
        "id": 4454723119001,
        "thumbnail": "https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/116/1752604059001_4454764366001_4454723119001-th.jpg?pubId=1752604059001&videoId=4454723119001"
    },
    {
        "id": 4454629913001,
        "thumbnail": "https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/1124/1752604059001_4454713920001_4454629913001-th.jpg?pubId=1752604059001&videoId=4454629913001"
    }
];
```

You can get at the properties of the videos by looping over the array:

```js
var video,
    i,
    iMax = items.length;

for (i = 0; i < iMax; i++) {
    video = items[i];
    document.write('video id: ' + video.id);
    document.write('thumbnail: ' + video.thumbnail);
}
```

In the CodePen below, you'll find the same code - try modifying it: instead of just adding &lt;br&gt; tag at the end of each line, wrap each line in a &lt;p&gt; tag.

<!-- @link, "url" : "https://codepen.io/team/bcls/pen/XmmKgq", "text": "JavaScript Exercise 1" -->

> Tip: all browsers include Developer Tools, one of which is a JavaScript console. You can dump any variable by including `console.log(variable_name)` in your code. And CodePens also include a console you can use in the same way.

<!-- @section -->

## Adding HTML Elements using JavaScript

`document.write` is a handy method of the `document` object, but it's limited. Fortunately, JavaScript has much more sophisticated ways of adding HTML content.

### [`document.createElement()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement) and [`[element].appendChild()`](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)

You can add new HTML elements to a page using the `document.createElement()`:

```js
var newEl = document.create.Element('img');
```

However, although `newEl` is part of the DOM (document object model), it won't appear on the page until you add it to some element that is already there using `appendChild()`. If you wanted to put the new element at the end of the page, you could simply use:

```js
document.appendChild(newEl);
```

In most cases though, you will want to put the new element in a specific place, The easiest way to do this is to get a reference to the tag you want to put your new element inside using [`document.getElementById()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById):

```html
<div id="myDiv"></div>

<script>
    var existingEl = document.getElementById('myDiv'),
        newEl = document.createElement('img');

    existingEl.appendChild(newEl);
</script>
```

### Adding or changing attributes

Creating new elements wouldn't be very useful if we couldn't add content and attributes to them. So of course we can add multiple layers of elements, and also add text content or modify attributes.

#### Adding text content

For our player, we don't really need to add text, but in many cases you will. The way to do it is to use `document.createTextNode('text here')` and then append the text node to your new element:

```js
var existingEl = document.getElementById('myDiv'),
    newEl = document.createElement('p'),
    newStrongEl = document.createElement('strong'),
    newText = document.createTextNode('My new text');

existingEl.appendChild(newEl);
newEl.appendChild(newStrongEl);
newStrongEl.appendChild(newText);
```

#### Adding/modifying attributes

You can [`setAttribute`](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute) for new or existing elements using:

```js
element.setAttribute('attribute name', 'value')
```

> Note that there is a companion [`getAttribute`](https://developer.mozilla.org/en-US/docs/Web/API/Element/getAttribute) method that retrieves the value of an attribute - we will need this later.

In the CodePen below, try adding an `img` tag to the `div` tag, and set the `src` attribute for the image to the CodePen below (you'll find this url in a comment in the CodePen):

<!-- @link, "url" : "https://codepen.io/team/bcls/pen/gaaMva", "text": "JavaScript Exercide 2" -->

Got it? If you don't see the image, check [the solution](https://codepen.io/team/bcls/pen/OyymwG).

<!-- @section -->
## Working with the Brightcove Player

We now have almost all the JavaScript tools we need to build our playlist dynamically - all we're lacking is the playlist data. But the player will give you that - all you have to do is assign the playlist to the player by adding a `data-playlist-id` attribute to the video tag and setting it equal to the playlist id, like this:

```html
<video style='width: 500px;height: 281px;'
    data-playlist-id="4452341376001"
    data-account="1752604059001"
    data-player="027d9de0-cb4f-4598-a1d4-0d8480d5a154"
    data-embed="default"
    class="video-js" controls>
</video>
```

Ok, so the playlist data is there, and the player provides us a nice way to get to it. But first we need to back up a little to see how we write JavaScript to interact with the player. If we try to do it too soon, errors will occur - the key is to listen for player events to know when it's ready for us.

### Player events

The player emits a bunch of events. The ones that we need to know about now are the ones that are emitted when the player is loaded on the page. The first one that matters is the `ready` event, which signifies that the basic player is ready to interact with.

To make it easy to interact with your player, add an `id` to the video tag:

```html
<video style='width: 500px;height: 281px;'
    id="myPlayerID"
    data-playlist-id="4452341376001"
    data-account="1752604059001"
    data-player="027d9de0-cb4f-4598-a1d4-0d8480d5a154"
    data-embed="default"
    class="video-js" controls>
</video>
```

Once you have added the `id`, here's how you set up your code to listen for the `ready` event:

```js
var myPlayer;

videojs('myPlayerID').ready(function(){
  myPlayer = this;
  // now I can call player methods on myPlayer
})
});
```

For a barebones player, the `ready` event is all you need to worry about. However, the Brightcove player loads some plugins and other data, and to be sure all this is finished before you start interacting with the player, you need to listen for the `loadedmetadata` event instead:

```js
var myPlayer;

videojs("myPlayerID").one('loadedmetadata',function(){
    var myPlayer = this;
});
```

> Notice the **`one`**`('loadedmetadata'...` - you can also use `on`, which will set up a permanent event listener. Using `one` instead allows you to handle the event only the first time it fires - and that is exactly what we want in this case. Be aware that a new `loadedmetadata` event will be emitted whenever new media is loaded into the player.

The player playlist object has a built-in [`playlist()`](http://docs.brightcove.com/en/video-cloud/brightcove-player/guides/playlist-api.html#playlist) method that will allow you to get playlist data:

```js
var myPlayer;

videojs("myPlayerID").on('loadedmetadata',function(){
    var myPlayer = this,
        playlistData = myPlayer.playlist();
});
```

You will find that the playlist data is an array of video objects - they contain many properties, but two of them will be useful to us here:

- `thumbnail` : the is the thumbnail url we've been using
- `name` : the video title - we could display it, but here we will just use it as the `alt` text for the thumbnail images (it's always good to include alt text for accessibility).

To create playlist items, then, we simply need to loop over the playlist items returned, and use the properties of each item to provide values for the attributes of the `img` tag:

```javascript
iMax = playlistData.length;
for (i = 0; i < iMax; i++) {
    videoItem = playlistData[i];
    // create the playlist item and set its class
    playlistItem = document.createElement('div');
    playlistItem.setAttribute('class', 'bcls-playlist-item');
    // create the thumbnail img and set its class
    thumbnailImg = document.createElement('img');
    thumbnailImg.setAttribute('class', 'bcls-thumbnail');
    // set the src for the thumbnail
    thumbnailImg.setAttribute('src', videoItem.thumbnail);
    /* set an attribute for img
     * to the loop index === playlist index
     * need this to load the video
     */
    thumbnailImg.setAttribute('data-playlist-index', i);
    // for best practice, set the alt attribute to the video name
    thumbnailImg.setAttribute('alt', videoItem.name);
    // now append the img to the item, and the item to the playlist
    playlistItem.appendChild(thumbnailImg);
    playlistWrapper.appendChild(playlistItem);
}
```

Your task now is to put this into a loop over the returned video items, generating the entire playlist HTML - try it in the CodePen below:

<!-- @link, "url" : "http://codepen.io/team/bcls/pen/Lppyvm", "text": "JavaScript Exercise - Generate the Playlist" -->

If you need to, [see the solution](https://codepen.io/team/bcls/pen/yYYpQw).

<!-- @section -->

## Handling Events

We now have the playlist built dynamically, but we still need to make it functional, so that when a viewer clicks on a thumbnail, the player plays that video.

A click is an event in JavaScript, and you can add event listeners to elements that allow you to take action when the event occurs. So we need to add an event listener to each of the playlist items. The method is `addEventListener(event, callback)` - the callback is a function that defines the actions to take.

We saw earlier how to get a reference to an element by its id: `document.getElementById()`. In this case we want a reference to a whole collection of elements, though - each of the playlist items. The `document` object has other methods that allow you to get a reference to an element collection - the key is to find one that will identify just those elements you are looking for. The one that will serve here is `document.getElementsByClassName()`, because we assigned the class `bcls-thumbnail` to each of the images, and we are not using that class anywhere else:

```js
var playlistItems = document.getElementsByClassName('bcls-thumbnail');
```

A collection of elements is a special kind of data entity in JavaScript, but for our purposes, it behave like an array, with a `length` property to tell us how many elements are in the collection. Thus we can loop over the collection like an array to add the event listeners:

```js
var iMax = playlistItems.length;
for (i = 0; i < iMax; i++) {
    playlistItems[i].addEventListener('click' function () {
        // code to handle the event here
    });
}
```

We could define the callback function somewhere else and just reference it here by name (and that's actually preferred over creating functions inside a loop), so we will do it like this:

```js
function loadPlaylistItem() {
    // code to handle event here
};
for (i = 0; i < iMax; i++) {
    playlistItems[i].addEventListener('click' loadPlaylistItem);
}
```

What we need to do in the function to handle the events is load the appropriate item from the playlist into the player, and then play it.

The player `playlist` object has a useful method for setting the current video: [`myPlayer.playlist.currentItem(item_index)`](http://docs.brightcove.com/en/video-cloud/brightcove-player/guides/playlist-api.html#currentitem). How do we get the correct item index? Easy, because we set it as the `data-playlist-index` attribute of the image tags as we were creating them.

> `data-whatever` attributes were added to HTML5 precisely for this purpose - to store bits of data so you could retrieve them via JavaScript.

So we could do something like this:

```js
var index = this.getAttribute('data-playlist-index');
myPlayer.playlist.currentItem(index);
```

> Note the `this` keyword - in JavaScript event handlers, it automatically refers to the element that *you added the event listener to*.

The only problem with the code above is that all HTML attribute values are returned as strings, but the `currentItem()` method expects an integer - `"2"` does **not** equal `2`. JavaScript has an easy fix for this, however: a [`parseInt()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt) function that automatically converts whatever you pass to in to an integer: `parseInt('2') // = 2`.

The last thing we need to do is play the selected video, and of course the player has a `play()` method. So our full event listener looks like this:

```js
function loadPlaylistItem () {
    var index = this.getAttribute('data-playlist-index');
    myPlayer.playlist.currentItem(parseInt(index, 10));
    myPlayer.play();
};
```

For your last exercise, add the code to the CodePen linked below to add click event handlers to the playlist items:

<!-- @link, "url" : "https://codepen.io/team/bcls/pen/Zbbzxp", "text": "Final Exercise" -->

The link to the final working solution is below:

<!-- @link, "url" : "https://codepen.io/team/bcls/pen/pjjzRv", "text": "Final Solution" -->

<!-- @section -->

## Challenge: Highlight the Current Item

If you completed the challenge exercise for the CSS module, you added a `style` attribute to the first playlist item that should look like this:

```
<div class="bcls-playlist-item" style="background-color: #F3951D">
```

What you now want to do is use JavaScript to apply that style to the current item in the playlist. Here are some hints:

* You don't want to just keep highlighting more and more items, so you need to set the style of all the items back to `""` and *then* change the `style` of the current item to `background-color: #F3951D`` (choose any color you like).
* You can do this at the same time that you set the `currentItem` in the playlist, but there is an advantage to creating a separate function to change the styles and calling that function after you set the current item - doing it that way allows you to call the function as soon as the playlist items are created, so that you immediately get highlighting of the first item

Have a try at this in the CodePen below:



And here is a [solution](https://codepen.io/team/bcls/pen/rOWWyr)

***
**<a id="feedbackMail" href="mailto:docs@brightcove.com?subject=Outlearn-Tutorial">Questions or comments?</a>**
