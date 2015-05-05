GitDeck Template Development
============================

GitDeck has a large database of ready templates for you to use in your decks. However, making
your own is a very easy process.

- Create a file called `[template-name].template.ejs` somewhere in the world
- Make sure the template is wrapped in a `div` with the class `slide` like so:
```html
<div class="slide">
    <!-- your template code -->
</div>
```
- Use standard EJS syntax to include the slide contents into your template. For example, if you have a template that looks like this:
```html
<div class="slide">
  <h1><%= title %></h1>
</div>
```
  that means that users of the template will be able to define a few slides like so:
```json
"slides": {
  "intro": {
    "title": "An Introduction"
  },
  "table-of-contents": {
    "title": "Table of Contents"
  }
}
```
