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

- `ol` tag: class: bcls-playlist
- `li` tags: class: bcls-playlist-item

The syntax is simple: just add the attribute `class="classname"` to the start tag. Try it in the JSBin below: