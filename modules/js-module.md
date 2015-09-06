<!--
{
"name": "js-module",
"version" : "0.1",
"title" : "JavaScript Essentials for the Brightcove Player",
"description" : "Learn to use JavaScript to control the Brightcove Player",
"homepage" : "https://github.com/rcrooks/outlearn-player-technologies",
"freshnessDate" : 2015-08-30,
"license" : "CC BY 4.0"
}
-->

<!-- @section -->

# Getting Started

If you already know the basics of JavaScript, you can move right on to the next section. If you're just starting, however, there is a lot of complexity to JavaScript, and you need to learn the basic features of the language. Here's a very good tutorial for beginners:

<!-- @link, "url" : "http://www.referencedesigner.com/tutorials/js/js_1.php", "text": "JavaScript Tutorial" -->

Take your time with that - practice spent on the basics will help you later on. In particular, you need to understand events, because much of the scripting you do in relation to the player will be in response to some event. You also need to feel comfortable with data structures like objects and arrays.

Take, for example, an  array of simple video objects:

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

In the JS-Bin below, you'll find the same code - try modifying it: instead of just adding &lt;br&gt; tag at the end of each line, wrap each line in a &lt;p&gt; tag.

<!-- @link, "url" : "https://rcrooks.jsbin.com/lifoko/4/edit?html,js,output", "text": "JavaScript Exercise 1" -->

<!-- @section -->

## Adding HTML Elements using JavaScript

`document.write` is a handy method of the `document` object, but it's limited. Fortunately, JavaScript has much more sophisticated ways of adding HTML content.

### `createElement()` and `appendChild()`

You can add new HTML elements to a page using the [document.createElement()](http://www.w3schools.com/js/js_htmldom_nodes.asp):

```js
var newEl = document.create.Element('img');
```

However, although `newEl` is part of the DOM (document object model), it won't appear on the page until you add it to some element that is already there using [appendChild()](http://www.w3schools.com/js/js_htmldom_nodes.asp). If you wanted to put the new element at the end of the page, you could simply use:

```js
document.appendChild(newEl);
```

In most cases though, you will want to put the new element in a specific place, The easiest way to do this is to get a reference to the tag you want to put your new element inside using