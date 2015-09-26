<!--
{
"name": "css-module",
"version" : "0.1",
"title" : "CSS Essentials for the Brightcove Player",
"description" : "Learn to style content around the Brightcove Player using CSS",
"homepage" : "//docs.brightcove.com/en/video-cloud/index.html",
"freshnessDate" : 2015-09-11,
"license" : "CC BY 4.0"
}
-->

<!-- @section -->

## Getting Started

In the last module, we covered a little bit of HTML to see how you can add content around a Brightcove player. In this module, we'll see how to use CSS (Cascading Style Sheets) to style the content.

> Remember that the player itself is just HTML, so you can also use CSS to modify the player appearance. There are some extra complexities associated with that, however, so here we'll focus on styling content around the player. Once you are comfortable with that, try [Quick Start to Customizing the Player](http://docs.brightcove.com/en/video-cloud/brightcove-player/guides/customize-quick-start.html).

CSS itself is a pretty simple language to learn. As with HTML we're going to assume here that you have some familiarity with it already, but if that's not the case, you'll find a great getting started tutorial here:

<!-- @link, "url" : "https://developer.mozilla.org/en-US/docs/Web/CSS", "text": "MDN CSS Tutorial" -->

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

Let's begin styling our playlist by adding some classes to the HTML (you will notice that the `div` that wraps the playlist already has a class):

- `div` tags for the individual items: class: bcls-playlist-item
- `img` tags: class: bcls-thumbnail

The syntax is simple: just add the attribute `class="classname"` to the start tag. Try it in the CodePen linked below:

<!-- @link, "url" : "https://codepen.io/team/bcls/pen/qOORog", "text": "Add Class Attributes" -->

You can see the finished code for this exercise here: [CSS Exercise 1 Solution](https://codepen.io/team/bcls/pen/OyyWZN)

<!-- @section -->

## Add the Class Style Rules

Now that we've added classes to the HTML tags, we need to add the CSS that defines the way we want our playlist to look.

For the overall list, we will constrain it to match the [`width`](https://developer.mozilla.org/en-US/docs/Web/CSS/width) of the player, and [`height`](https://developer.mozilla.org/en-US/docs/Web/CSS/height) to present one row of images. We'll set the [`margin`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin) and [`padding`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) to 0. Since all the thumbnails will not fit in the player width, we will also define the [`overflow-x`](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow-x) property to allow the list to scroll horizontally, and set the [`overflow-y`](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow-y) property to `hidden` so that the list won't scroll vertically.. By default, though, extra list items would roll over to a new row, so we'll prevent that by setting [`white-space`](https://developer.mozilla.org/en-US/docs/Web/CSS/white-space) to `nowrap`. Finally, we'll set the ([`background-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-color) to match the player background color (`#141B17`).

For the list items, first of all, we want the thumbnails to be laid out horizontally rather than vertically. To do this, we will use the [`display`](https://developer.mozilla.org/en-US/docs/Web/CSS/display) property, setting it to `inline-block`. We'll also set [`margin`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin) and [`padding`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) to `0`, and set the `width` of the items to avoid white space between them.

For the images, we will add [`padding`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) on all sides let the list background color show through and "frame" the images, and resize the images using the `width` and `height` properties to fit four images across the bottom of the player. Finally we'll add the [`cursor`](https://developer.mozilla.org/en-US/docs/Web/CSS/cursor) property, setting it to `pointer` so that it's more obvious that clicking on the images will do something.

In the CodePen below, go to the CSS section and add the following classes:

```css
.bcls-playlist {
    width: 500px;
    height: 74px;
    overflow-x: scroll;
    overflow-y: hidden;
    white-space: nowrap;
    margin: 0;
    padding: 0;
    background-color: #141B17;
}
.bcls-playlist-item {
    display: inline-block;
    padding: 0;
    margin: 0;
    width: 122px;
}
.bcls-thumbnail {
    width: 118px;
    height: 66px;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 2px;
    padding-right: 2px;
    cursor: pointer;
}
```

<!-- @link, "url" : "https://codepen.io/team/bcls/pen/OyyWZN", "text": "Add CSS Classes" -->

Got that? If you want to see what it should look like, see [CSS Exercise 2 Solution](https://codepen.io/team/bcls/pen/ZbbLjx)

<!-- @section -->

Challenge: Highlight an Item

If you'd like to practice your HTML and CSS skills, go back to the CodePen and add another class called `bcls-selected-item` that is identical to the `bcls-playlist-item` class except that it has its own `background-color` image (choose something light). Also modify the `div` for the first playlist item and give it this class. This is how you would highlight the currently loaded video. Try it here:



<!-- @section -->

## Best Practices

What we did here is fine, but it has the limitation that the width of the playlist is a hard-coded value to match that of the player. So if you wanted to use this with a player that was sized differently, you would have to adjust the width of the playlist to match the new player.

And what if you wanted to [make the player responsive](http://docs.brightcove.com/en/video-cloud/brightcove-player/samples/responsive-sizing.html)?

A better approach would be to wrap the whole player and playlist in another `div` tag. Then you could set the `width` of the player and playlist to `100%` of the wrapper `div` width, and then just set the `width` on the wrapper, like the example in the CodePen below:

<!-- @link, "url" : "http://codepen.io/team/bcls/pen/pjjROd", "text": "Video Player and Playlist in DIV Wrapper" -->

***
**<a id="feedbackMail" href="mailto:docs@brightcove.com?subject=Outlearn-Tutorial">Questions or comments?</a>**
