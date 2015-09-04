<!--
{
"name": "css-module",
"version" : "0.1",
"title" : "CSS Essentials for the Brightcove Player",
"description" : "This is only a test",
"homepage" : "https://github.com/rcrooks/outlearn-player-technologies",
"freshnessDate" : 2015-08-30,
"license" : "CC BY 4.0"
}
-->

<!-- @section -->

## Getting Started

In the last module, we covered a little bit of HTML to see how you can add content around a Brightcove player. In this module, we'll see how to use CSS (Cascading Style Sheets) to style the content.

> Remember that the player itself is just HTML, so you can also use CSS to modify the player appearance. There are some extra complexities associated with that, however, so here we'll focus on styling content around the player. Once you are comfortable with that, try [Quick Start to Customizing the Player](http://docs.brightcove.com/en/video-cloud/brightcove-player/guides/customize-quick-start.html).

CSS itself is a pretty simple language to learn. As with HTML we're going to assume here that you have some familiarity with it already, but if that's not the case, you'll find a great getting started tutorial here:

<!-- @link, "url" : "https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_started", "text": "MDN CSS Tutorial" -->

<!-- @section -->

## CSS Pitfalls

Ok, if you're comfortable with the basics of CSS, let's move on.

While CSS is a simple language, getting it to work the way you want can be tricky. Here is the most common issues and some tips on avoiding it.

### CSS collisions

Your pages generally will already have a lot of CSS in them before you do anything. There are site styles for your general site layout, and some of the elements you add to the page may come with their own CSS (the Brightcove Player, for example). These different style sheets compete with one another. Here are some basic tips for avoiding collisions with other CSS when you are adding styling to some part of the page:

- Avoid styling by HTML tag names - instead, add classes to elements you want to style:

```css
/* don't do this! */
li {
    margin: 0;
}
/* instead, do this */
.playlist-item {
    margin: 0;
}
```

This means, of course, that the `li` tags you want to style must have `class="playlist-item"` added to each tag.

- Prefix the class names - the above rule helps, but what if some other CSS has already created a `playlist-item` class? To avoid that problem, prefix all your classes with some abbreviation that no one else is likely to use:

```css
.bcls-playlist-item {
    margin: 0;
}
```

The prefix can be anything you like. The `bcls` shown here is what we use as an abbreviation for Brightcove Learning Services (and we'll use this in our sample code)

<!-- @section -->

## Add Classes to Your HTML Code

Let's begin styling our playlist by adding some classes to the HTML:

- `div` tag for the overall list: class: bcls-playlist
- `div` tags for the individual items: class: bcls-playlist-item
- `img` tags: class: bcls-thumbnail

The syntax is simple: just add the attribute `class="classname"` to the start tag. Try it in the JSBin below:

<!-- @link, "url" : "https://rcrooks.jsbin.com/vuqima/edit", "text": "Add Class Attributes" -->

You can see the finished code for this exercise here: [CSS Exercise 1](https://rcrooks.jsbin.com/romose/edit)

<!-- @section -->

## Add the Class Style Rules

Now that we've added classes to the HTML tags, we need to add the CSS that defines the way we want our playlist to look.

For the overall list, we will constrain it to match the width of the player, and height to present one row of images. We'll set the margin and padding to 0, and we don't want bullets, so we'll set `list-style-type` to `none`. Since all the thumbnails will not fit in the player width, we will also define the `overflow-x` property to allow the list to scroll horizontally, and set the `overflow-y` property to `hidden` so that the list won't scroll vertically.. By default, though, extra list items would roll over to a new row, so we'll prevent that by setting `white-space` to `nowrap`.

For the list items, first of all, we want the thumbnails to be laid out horizontally rather than vertically. To do this, we will use the `display` property, setting it to `inline-block`. We'll also set `margin` and `padding` to `0`, and set the `width` of the items to avoid white space between them.

For the images, we will add a border to set them off from one another (using the background color the player to give the list an integrated look), and resize the images using the width and height properties to fit four images across the bottom of the player.

In the JS-Bin below, go to the CSS section and add the following classes:

```css
.bcls-playlist {
    width: 500px;
    height: 74px;
    overflow-x: scroll;
    overflow-y: hidden;
    white-space: nowrap;
    margin: 0;
    padding: 0;
}
.bcls-playlist-item {
    display: inline-block;
    padding: 0;
    margin: 0;
    width: 120px;
}
.bcls-thumbnail {
    width: 118px;
    height: 66px;
    border: 4px solid #141B17;
}
```

<!-- @link, "url" : "https://jsbin.com/zudelu/edit", "text": "Add CSS Classes" -->

Got that? If you want to see what it should look like, see the JS-Bin below:

<!-- @link, "url" : "https://rcrooks.jsbin.com/putime/11/edit?html,css,output", "text": "CSS for the Playlist Finished" -->

<!-- @section -->

## Best Practices

What we did here is fine, but it has the limitation that the width of the playlist is a hard-coded value to match that of the player. So if you wanted to use this with a player that was sized differently, you would have to adjust the width of the playlist to match the new player. 

And what if you wanted to [make the player responsive](http://docs.brightcove.com/en/video-cloud/brightcove-player/samples/responsive-sizing.html)? 

A better approach would be to wrap the whole player and playlist in another `div` tag. Then you could set the width of the player and playlist to `100%` of the wrapper `div` width, and then just set the width on the wrapper.