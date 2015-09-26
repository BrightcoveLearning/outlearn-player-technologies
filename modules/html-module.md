<!--
{
"name": "html-module",
"version" : "0.1",
"title" : "HTML Essentials for the Brightcove Player",
"description" : "Learn to create HTML content around the Brightcove Player",
"homepage" : "//docs.brightcove.com/en/video-cloud/index.html",
"freshnessDate" : 2015-09-11,
"license" : "CC BY 4.0"
}
-->

<!-- @section -->

## Getting Started

We're guessing that if you got here, you already know basic HTML, but if don't, that's fine. HTML is a simple markup language for web pages, and it's easy to learn.

If you're a total beginner with HTML, go here to get the basics:

<!-- @link, "url" : "https://developer.mozilla.org/en-US/docs/Web/HTML", "text": "Getting Started with HTML" -->

Once you get the basics, go on to the next section.

<!-- @section -->

## Creating a custom playlist

Ok, you know the basics of HTML, so let's do something specific to the Brightcove Player. In this section you'll learn how to create the HTML for a simple horizontal playlist along the bottom of a video player.

As you know, the player has built-in capability to add a vertical playlist on the right side of the player, but you might prefer a more compact display of a simple row of video thumbnail images along the bottom of the player.

The HTML we're going to use is the simple `div` tag, an all-purpose container. If you're not familiar with it, you can read all about it here:

<!-- @link, "url" : "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div", "text": "The DIV Tag" -->

We will be using two levels of divs: one to wrap the whole list, and another for each item.

You will also need to use `img` tags to display the video thumbnails, so if you need to learn about that tag, go here:

<!-- @link, "url" : "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img", "text": "The IMG Tag" -->

Now let's create the HTML for playlist. Here is a list of URLs for video thumbnails (don't worry about where they are coming from - we're going to deal with that later):

```
https://bcsecure01-a.akamaihd.net/6/1752604059001/201509/116/1752604059001_4475309190001_4454723119001-th.jpg?pubId=1752604059001&videoId=4454723119001

https://bcsecure01-a.akamaihd.net/6/1752604059001/201509/1124/1752604059001_4475315633001_4454629913001-th.jpg?pubId=1752604059001&videoId=4454629913001

https://bcsecure01-a.akamaihd.net/6/1752604059001/201509/124/1752604059001_4475315192001_4454629914001-th.jpg?pubId=1752604059001&videoId=4454629914001

https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/1572/1752604059001_4454713750001_4454620114001-th.jpg?pubId=1752604059001&videoId=4454620114001

https://bcsecure01-a.akamaihd.net/6/1752604059001/201509/967/1752604059001_4511372842001_4511351172001-th.jpg?pubId=1752604059001&videoId=4511351172001

https://bcsecure01-a.akamaihd.net/6/1752604059001/201509/572/1752604059001_4475318377001_4454620113001-th.jpg?pubId=1752604059001&videoId=4454620113001

https://bcsecure01-a.akamaihd.net/6/1752604059001/201509/3441/1752604059001_4511372778001_4511340777001-th.jpg?pubId=1752604059001&videoId=4511340777001

```

Now, try it yourself - in the CodePen below, find the comment <!-- playlist items go here --> and after it add a `div` tag for each of the playlist items, and inside each of these `div` tags, add an `img` tag with the `src` attribute set equal to the thumbnail URL. The code for the list will look like this:

```html
<div id="playlistWrapper" class="bcls-playlist">
    <!-- playlist items go here -->
    <div>
        <img src="https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/116/1752604059001_4454764366001_4454723119001-th.jpg?pubId=1752604059001&videoId=4454723119001">
    </div>
    ...
</div>
```

(For convenience, the list of URLs is included in the JS Bin after the comment in the HTML.)

<!-- @link, "url" : "https://codepen.io/team/bcls/pen/meeOJx", "text": "Add the Playlist Items HTML" -->

<!-- @section -->
## Wrapping up

Did that work? When you finish, the CodePen should look like the one linked below:

[HTML Exercise Solution](https://codepen.io/team/bcls/pen/xwwRwR)

So now let's move on to CSS.

***
**<a id="feedbackMail" href="mailto:docs@brightcove.com?subject=Outlearn-Tutorial">Questions or comments?</a>**
