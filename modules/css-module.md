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

The prefix can be anything you like. The `bcls` shown here is what we use as an abbreviation for Brightcove Learning Services (and we'll use this in our sample code)

## Using Markdown
You may have already used Markdown. It's an awesome format for technical publishing. If you need a refresher, GitHub has a great overview.

<!-- @link, "url" : "https://help.github.com/articles/markdown-basics/", "text": "I know enough about Markdown." -->

GitHub-flavored markdown will work just fine, and you can preview your files in your favorite text editor or Markdown preview tool before uploading them to Outlearn for final proof-reading.

If you want to enrich your content with more features, this sample module has a few examples, including the Unfurled Link above, and the interactive features described in the next section.

> Block quotes get special styling on Outlearn. They turn into highlight boxes.

<!-- @section -->

# Images and videos
You can include images using Markdown syntax.

![sea](https://raw.githubusercontent.com/outlearn-content/outlearn-modules/master/assets/sea.jpg)

# Let's make our module Fancy
If you want to get your audience to practice what you preach, give them a task.

```python
# Transpose a matrix:
>>> l = [[1, 2, 3], [4, 5, 6]]
>>> zip(*l)
[(1, 4), (2, 5), (3, 6)]

# Divide a list into groups of n:
>>> l = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5, 8]
>>> zip(*[iter(l)] * 3)
[(3, 1, 4), (1, 5, 9), (2, 6, 5), (3, 5, 8)]
```

<!-- @task, "text" : "Go and run these clever code examples on your own machine, lazy bones!"-->

And if they are making something worth sharing, why not let them share it with you?  

<!-- @task, "hasDeliverable" : true, "text" : "Write and submit a haiku about your favorite compiler."-->

Then go ahead and test how much they know.

<!-- @multipleChoice -->

You can add a matrix and its transpose together only if
- [ ] The elements of the matrix are integers
- [ ] The matrix has an inverse
- [X] The matrix is a square matrix

Remember that two matrices can be added if they have the same number of rows and columns.

<!-- @end -->

If you need more details on how to author, please visit the [Outlearn Publishing Guide](https://pilot.outlearn.com/learn/outlearn/outlearn-publishing), where you'll find more examples along with the full specification for the format used by this sample module.
