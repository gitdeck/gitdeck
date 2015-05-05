GitDeck Syntax and Parser
=========================

GitDeck creates beautiful slide decks from your GitHub repository in minutes. Your entire presentation, including a template for styling and slide generation, is organized using JSON.

Templates
---------

Templates are the bread and butter of GitDeck. Without them, your slides will be boring: white background with black text. GitDeck templates are simple HTML files with field variables instead of content. Your slides and their contents can be easily beautified by linking to an external CSS file from your HTML template. Inline CSS is *strongly* discouraged in order to promote the separation of style and content within templates.

Simple Example
--------------

The following JSON snippet defines a new presentation titled `"How to Build a Website"` by
`"John Smith"`. The title and author fields are required by GitDeck as metadata to organize
your decks.

Following the metadata fields, we define the `"slides"` field, which holds an record of
all the slides in your deck.

The first slide is called `"intro"`. This is a unique identifier for that particular slide.
All fields within a specific slide object are variable. This means that none are required by the
GitDeck parser. In the example below, we have arranged it so that the `"intro"` slide contains a title and two paragraphs.


```json
{
  "title": "How to Build a Website",
  "author": "John Smith",
  "slides": {
    "intro": {
      "title": "Where To Start",
      "paragraph": "This is the first paragraph",
      "paragraph": "This is the second paragraph"
    }
  }
}
```

Now where the template comes in. The template used for the slide(s) dictate what fields are valid and how they are displayed. If no template is specified, GitDeck uses the `"basic"` template which only defines the `"title"` and `"paragraph"` fields.

We've also made some basic templates for you to easily incorporate into your slide deck. For example, you can assign the `GitDeck::templates::complex-bee` value to the `"template"` key in order to use our `complex-bee` template. You can find the entire list of GitDeck-curated templates [here](#), as well as some user-submitted templates [here](#).


Template Example
----------------

The following is a snippet of what a simple GitDeck template might look like. It defines
a `"title"`, `"subtitle"`, and `"paragraph"` field and formats them accordingly. GitDeck includes
the latest Bootstrap release in its deck generation so bootstrap-specific tags like `"small"`
and correctly displayed.

```html
<div class="slide">
  <h1>
    <%= title %><br>
    <small><%= subtitle %></small>
  </h1>
  <% for(var i = 0; i < paragraphs.length; i++) { %>
    <p><%= paragraphs[i] %></p>
  <% } %>
</div>
```
