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

The HTML we're going to use is the unordered list element, so if you're not familiar with it, you can read all about it 

<!-- @link, "url" : "http://learn.shayhowe.com/html-css/creating-lists/", "text": "here" -->

Now let's create the HTML for playlist. Here is a list of video ids and URLs for video thumbnails (don't worry about where they are coming from - we're going to deal with that later):

```
[
  {
    "id": "4454723119001",
    "thumbnail": "https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/116/1752604059001_4454764366001_4454723119001-th.jpg?pubId=1752604059001&videoId=4454723119001"
  },
  {
    "id": "4454629913001",
    "thumbnail": "https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/1124/1752604059001_4454713920001_4454629913001-th.jpg?pubId=1752604059001&videoId=4454629913001"
  },
  {
    "id": "4454629914001",
    "thumbnail": "https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/124/1752604059001_4454713878001_4454629914001-th.jpg?pubId=1752604059001&videoId=4454629914001"
  },
  {
    "id": "4454620115001",
    "thumbnail": "https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/2572/1752604059001_4454713729001_4454620115001-th.jpg?pubId=1752604059001&videoId=4454620115001"
  },
  {
    "id": "4454620114001",
    "thumbnail": "https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/1572/1752604059001_4454713750001_4454620114001-th.jpg?pubId=1752604059001&videoId=4454620114001"
  },
  {
    "id": "4454620113001",
    "thumbnail": "https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/572/1752604059001_4454712159001_4454620113001-th.jpg?pubId=1752604059001&videoId=4454620113001"
  },
  {
    "id": "4454620112001",
    "thumbnail": "https://bcsecure01-a.akamaihd.net/6/1752604059001/201508/3572/1752604059001_4454712084001_4454620112001-th.jpg?pubId=1752604059001&videoId=4454620112001"
  }
]
```

Now, try it yourself - in the JS-Bin below, find the comment <!-- insert list here --> and after it add the following tag:

<!-- @link, "url" : "http://rcrooks.jsbin.com/hobada/edit", "text": "JS Bin" -->