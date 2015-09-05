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
        "id": 987934797,
        "thumbnail": "http://somepath/image987934797.png"
    },
    {
        "id": 83623726,
        "thumbnail": "http://somepath/image83623726.png"
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

<!-- @link, "url" : "https://rcrooks.jsbin.com/lifoko/2/edit?html,js,output", "text": "JavaScript Exercise 1" -->

<!-- @section -->

## Adding HTML Elements using JavaScript

`document.write` is a handy method of the `document` object, but it's limited. Fortunately, JavaScript has much more sophisticated ways of adding HTML content.

### `appendChild()`