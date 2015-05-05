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
- Use standard EJS syntax to include the slide contents into your template.

A Simple Example
----------------

Here's an example of using fields with single strings as template parameters. It would generate
two slides with `h1` elements corresponding to the `title` fields defined in the slides file.

**Template**
```html
<div class="slide">
  <h1><%= title %></h1>
</div>
```

**Slides**
```json
{
  "title": "How to Build a Website",
  "author": "John Smith",
  "slides": {
    "intro": {
      "title": "Where To Start"
    },
    "table-of-contents": {
      "title": "What We're Going To Cover"
    }
  }
}
```

Using Arrays
------------

EJS allows for the parsing of simple arrays. GitDeck supports this configuration and it can be
used to define paragraphs in each slide. Let's extend the simple example from above to include
an array of paragraphs.

**Template**
```html
<div class="slide">
  <h1><%= title %></h1>
  <% for(var i = 0; i < paragraphs.length; i++) { %>
    <p><%= paragraphs[i] %></p>
  <% } %>
</div>
```

**Slides**
```json
{
  "title": "How to Build a Website",
  "author": "John Smith",
  "slides": {
    "intro": {
      "title": "Where To Start",
      "paragraphs": [
        "A small demo presentation from John Smith"
      ]
    },
    "table-of-contents": {
      "title": "What We're Going To Cover",
      "paragraphs": [
        "How to create HTML files",
        "Adding style to your pages with CSS",
        "Implementing frontend logic with Javascript"
      ]
    }
  }
}
```

In this example, the template looks for a field called `paragraphs` and expects it to be
an array. It then parses each element of the array and displays it in its own `<p>` element.
