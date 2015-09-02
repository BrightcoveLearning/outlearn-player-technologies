<!--
{
"name": "html-module",
"version" : "0.1",
"title" : "HTML Essentials",
"description" : "This is only a test",
"homepage" : "https://github.com/rcrooks/outlearn-player-technologies",
"freshnessDate" : 2015-08-30,
"license" : "CC BY 4.0"
}
-->

<!-- @section -->

# Getting Started

We're guessing that if you got here, you already know basic HTML, but if don't, that's fine. HTML is a simple markup language for web pages, and it's easy to learn.

If you're a total beginner with HTML, go here to get the basics:

<!-- @link, "url" : "http://www.htmldog.com/guides/html/beginner/", "text": "Getting Started with HTML" -->

Once you get the basics, go on to the next module.

<!-- @section -->

# Creating a custom playlist

Ok, you know the basics of HTML, so let's do something specific to the Brightcove Player. In this section you'll learn how to create the HTML for a simple horizontal playlist along the bottom of a video player.

As you know, the player has built-in capability to add a vertical playlist on the right side of the player, but you might prefer a more compact display of a simple row of video thumbnail images along the bottom of the player.

Here we will create the HTML for playlist.

```html
<video ...
    <track kind="chapters" srclang="en" src="http://path-to-file/chapter.vtt" label="Chapters">
</video>
```
You can read about the details of the &lt;track&gt; attributes here:

<!-- @link, "url" : "http://www.sitepoint.com/comprehensive-look-html5-track-element/", "text": "The Track Tag" -->

> Note: in principle, the track tag can refer to `src` files in various formats, but for Video Cloud you need to use the WebVTT format.



Now, try it yourself - in the CodePen below, find the comment <!-- add playlist here --> and after it add the following tag:

```html
<track src="http://learning-services-media.brightcove.com/chaptered-video/vtt/sea-marvels-chapters.vtt" kind="chapters" srclang="en" label="Chapters">
