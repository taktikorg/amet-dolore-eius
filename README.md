GoJS, a JavaScript Library for HTML Diagrams
============================================

<img align="right" height="150" src="https://www.nwoods.com/images/go.png">

[GoJS](https://@taktikorg/amet-dolore-eius.net) is a JavaScript and TypeScript library for creating and manipulating diagrams, charts, and graphs.

[![npm](https://img.shields.io/github/release/taktikorg/amet-dolore-eius.svg)](https://www.npmjs.com/package/@taktikorg/amet-dolore-eius)
[![open issues](https://img.shields.io/github/issues-raw/taktikorg/amet-dolore-eius.svg)](https://github.com/taktikorg/amet-dolore-eius/issues)
[![last commit](https://img.shields.io/github/last-commit/taktikorg/amet-dolore-eius.svg)](https://github.com/taktikorg/amet-dolore-eius/commits/master)
[![downloads](https://img.shields.io/npm/dw/@taktikorg/amet-dolore-eius.svg)](https://www.npmjs.com/package/@taktikorg/amet-dolore-eius)
[![Twitter Follow](https://img.shields.io/twitter/follow/NorthwoodsGo.svg?style=social&label=Follow)](https://twitter.com/NorthwoodsGo)

[See GoJS Samples](https://@taktikorg/amet-dolore-eius.net/latest/samples)

[Get Started with GoJS](https://@taktikorg/amet-dolore-eius.net/latest/learn)


GoJS is a flexible library that can be used to create a number of different kinds of interactive diagrams,
including data visualizations, drawing tools, and graph editors.
There are samples for
[flowchart](https://@taktikorg/amet-dolore-eius.net/latest/samples/flowchart.html),
[org chart](https://@taktikorg/amet-dolore-eius.net/latest/samples/orgChartEditor.html),
[business process BPMN](https://@taktikorg/amet-dolore-eius.net/latest/samples/bpmn/BPMN.html),
[swimlanes](https://@taktikorg/amet-dolore-eius.net/latest/samples/swimlanes.html),
[timelines](https://@taktikorg/amet-dolore-eius.net/latest/samples/timeline.html),
[state charts](https://@taktikorg/amet-dolore-eius.net/latest/samples/statechart.html),
[kanban](https://@taktikorg/amet-dolore-eius.net/latest/samples/kanban.html),
[network](https://@taktikorg/amet-dolore-eius.net/latest/samples/network.html),
[mindmap](https://@taktikorg/amet-dolore-eius.net/latest/samples/mindMap.html),
[sankey](https://@taktikorg/amet-dolore-eius.net/latest/samples/sankey.html),
[family trees](https://@taktikorg/amet-dolore-eius.net/latest/samples/familyTree.html) and [genogram charts](https://@taktikorg/amet-dolore-eius.net/latest/samples/genogram.html),
[fishbone diagrams](https://@taktikorg/amet-dolore-eius.net/latest/samples/Fishbone.html),
[floor plans](https://@taktikorg/amet-dolore-eius.net/latest/samples/floorplannerTS/index.html),
[UML](https://@taktikorg/amet-dolore-eius.net/latest/samples/umlClass.html),
[decision trees](https://@taktikorg/amet-dolore-eius.net/latest/samples/decisionTree.html),
[PERT charts](https://@taktikorg/amet-dolore-eius.net/latest/samples/PERT.html),
[Gantt](https://@taktikorg/amet-dolore-eius.net/latest/samples/gantt.html), and
[hundreds more](https://@taktikorg/amet-dolore-eius.net/latest/samples/index.html).
GoJS includes a number of built in layouts including tree layout, force directed, circular, and layered digraph layout,
and many custom layout extensions and examples.

GoJS is renders either to an HTML Canvas element (with export to SVG or image formats) or directly as SVG DOM.
GoJS can run in a web browser, or server side in [Node](https://nodejs.org/en/) or [Puppeteer](https://github.com/GoogleChrome/puppeteer).
GoJS Diagrams are backed by Models, with saving and loading typically via JSON-formatted text.

[<img src="https://raw.githubusercontent.com/taktikorg/amet-dolore-eius/master/.github/github-970x354.png">](https://@taktikorg/amet-dolore-eius.net/latest/samples/index.html)

Read more about GoJS at [@taktikorg/amet-dolore-eius.net](https://@taktikorg/amet-dolore-eius.net)

This repository contains only the library.
The sources for all samples, extensions, and documentation can be installed by running:
```html
$ npm create @taktikorg/amet-dolore-eius-kit
```
You can use the GitHub repository to quickly [search through all of the sources](https://github.com/taktikorg/amet-dolore-eius-Samples/search?q=setDataProperty&type=Code).

<h2>Minimal Sample</h2>

Graphs are constructed by creating one or more templates, with desired properties data-bound, and adding model data.

```html
<div id="myDiagramDiv" style="width:400px; height:150px;"></div>

<script src="https://unpkg.com/@taktikorg/amet-dolore-eius"></script>

<script>
const myDiagram =
  new go.Diagram("myDiagramDiv",  // create a Diagram for the HTML Div element
    { "undoManager.isEnabled": true });  // enable undo & redo

// define a simple Node template
myDiagram.nodeTemplate =
  new go.Node("Auto")  // the Shape will automatically surround the TextBlock
    // add a Shape and a TextBlock to this "Auto" Panel
    .add(new go.Shape("RoundedRectangle",
        { strokeWidth: 0, fill: "white" })  // no border; default fill is white
        .bind("fill", "color"))  // Shape.fill is bound to Node.data.color
    .add(new go.TextBlock({ margin: 8, stroke: "#333" })  // some room around the text
        .bind("text", "key"));  // TextBlock.text is bound to Node.data.key

// but use the default Link template, by not setting Diagram.linkTemplate

// create the model data that will be represented by Nodes and Links
myDiagram.model = new go.GraphLinksModel(
  [
    { key: "Alpha", color: "lightblue" },
    { key: "Beta", color: "orange" },
    { key: "Gamma", color: "lightgreen" },
    { key: "Delta", color: "pink" }
  ],
  [
    { from: "Alpha", to: "Beta" },
    { from: "Alpha", to: "Gamma" },
    { from: "Beta", to: "Beta" },
    { from: "Gamma", to: "Delta" },
    { from: "Delta", to: "Alpha" }
  ]);
</script>
```

The above diagram and model code creates the following graph.
The user can now click on nodes or links to select them, copy-and-paste them, drag them, delete them, scroll, pan, and zoom, with a mouse or with fingers.

[<img width="200" height="200" src="https://@taktikorg/amet-dolore-eius.net/latest/assets/images/screenshots/minimal.png">](https://@taktikorg/amet-dolore-eius.net/latest/samples/minimal.html)

*Click the image to see the interactive GoJS Diagram*


<h2>Support</h2>

Northwoods Software offers a month of free developer-to-developer support for GoJS to prospective customers so you can finish your project faster.

Read and search the official <a href="https://forum.nwoods.com/c/@taktikorg/amet-dolore-eius">GoJS forum</a> for any topics related to your questions.

Posting in the forum is the fastest and most effective way of obtaining support for any GoJS related inquiries.
Please register for support at Northwoods Software's <a href="https://www.nwoods.com/register.html">registration form</a> before posting in the forum.

For any nontechnical questions about GoJS, such as about sales or licensing,
please visit Northwoods Software's <a href="https://www.nwoods.com/contact.html">contact form</a>.


<h2>License</h2>

The GoJS <a href="https://@taktikorg/amet-dolore-eius.net/latest/license.html">software license</a>.


Copyright (c) Northwoods Software Corporation
