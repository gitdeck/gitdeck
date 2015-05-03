GitDeck Syntax and Parser
=========================

GitDeck uses a combination of JSON and Markdown to create slides. Your whole presentation,
as well as templates for slide generation, is organized using JSON. Within the JSON content,
you can define paragraphs with Markdown.

Templates
---------

Templates are the bread and butter of GitDeck. Without them, your slides will be in boring
black and white. GitDeck templates are simple HTML files with field variables instead of
content. They can be accompanied by external or inline CSS.

Simple Example
--------------

The following JSON snippet defines a new presentation titled "How to Build a Website" by
"John Smith". The title and author fields are required by GitDeck as metadata to organize
your decks.

Following the metadata fields, we define the "slides" field, which holds an record of
all the slides in your deck.

The first slide is called "intro". This is a unique identifier for that particular slide.
All fields within a specific slide object are variable. Meaning, none are required by the
GitDeck parser. This is where the template comes in. The template used for the slide(s)
will dictate what fields are valid and how they are displayed. If no template is specified,
then GitDeck uses the "Default" template which defines the "title" and "paragraph" fields.


```json
{
  "title": "How to Build a Website",
  "author": "John Smith",
  "slides": {
    "intro": {
      "title": "Where To Start",
      "paragraph": "This is the first paragraph",
      "paragraph": "This is the second paragraph"
    },
  }
}
```

Template Example
----------------

The following is a snippet of what a simple GitDeck template might look like. It defines
a "title", "subtitle", and "paragraph" field and formats them accordingly. GitDeck includes
the latest Bootstrap release in its deck generation so bootstrap-specific tags like "small"
and correctly displayed.

```html
<h1 style="margin-bottom: 20px; color: #666">
  $title
  <small>$subtitle</small>
</h1>
<p>$paragraph</p>
<p>$paragraph</p>
```
