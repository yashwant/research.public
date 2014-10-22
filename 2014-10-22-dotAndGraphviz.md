---
layout: post
title: "DOT & Graphviz"
slug: "research-dot-and-graphviz"
date: 2014-10-22 13:20
comments: true
categories: [design]
tags: [visualisation, dot, graphviz, language, design, information, infoviz, infovis, dataviz, data visualisation, data visualization]
published: true
---

# DOT & Graphviz

**What is DOT?**  
DOT is a tool to generate nice-looking diagrams with a minimum of effort. It is not just another paint program, nor a vector graphics program. DOT is a scriptable, batch-oriented graphing tool; it is to vector drawing programs as LaTeX is to word processors. DOT is especially useful in repetitive and automatic tasks. You can not control the positioning of Nodes exactly – but the idea is that Graphviz does the positioning automatically so that you only have to worry about and document the Nodes and the relationships between them, so don’t get hung up on the layout too much.

**What is Graphviz?**  
Graphviz (short for Graph Visualization Software) is a package of open source tools initiated by AT&T Research Labs for drawing graphs specified in [DOT language scripts](http://en.wikipedia.org/wiki/DOT_(graph_description_language)).

**Graphviz Installation**

If you are using a Mac simply install [Homebrew](http://brew.sh). Just paste `ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"` into your terminal. Then update the package list by typing `brew update` and install Graphviz afterwards by `brew install graphviz`. Done.

## Terms

* **Nodes** (aka vertices) are the fundamental unit out of which graphs are formed
* **Edges** (directional arcs) is a line connecting two nodes
* **Graph** is a collection of nodes and edges

## Resources

* [Graphviz output formats](http://www.graphviz.org/content/output-formats) (overview)
* [Node, Edge and Graph Attributes](http://www.graphviz.org/doc/info/attrs.html) (overview)
* [Node Shapes](http://www.graphviz.org/doc/info/shapes.html) (overview)
* [Arrow Shapes](http://www.graphviz.org/doc/info/arrows.html) (overview)

## Filter

A **filter** is a layout algorithms to automatically arrange the diagram. Graphviz comes with the following filters:

* `dot` is a filter for drawing directed graphs and works well on DAGs and other graphs that can be drawn as hierarchies.
* `neato` filter for drawing undirected graphs using *spring* models. Detailed information: [Drawing graphs with NEATO](http://www.graphviz.org/pdf/neatoguide.pdf)
* `fdp` is a filter for drawing undirected graphs using a *spring* model. It relies on a force-directed approach in the spirit of [Fruchterman and Reingold](http://en.wikipedia.org/wiki/Force-directed_graph_drawing).
* `circo` is a filter for circular layout of graphs. It draws graphs using a circular layout. The tool identifies biconnected components and draws the nodes of the component on a circle. The block-cut point tree is then laid out using a recursive radial algorithm. Edge crossings within a circle are minimized by placing as many edges on the circle’s perimeter as possible. In particular, if the component is outer planar, the component will have a planar layout.
* `twopi` is a filter for radial layouts of graphs. It draws graphs using a radial layout. Basically, one node is chosen as the center and put at the origin. The remaining nodes are placed on a sequence of concentric circles centered about the origin, each a fixed radial distance from the previous circle. All nodes distance 1 from the center are placed on the first circle; all nodes distance 1 from a node on the first circle are placed on the second circle; and so forth.
* `sfdp` is a filter for drawing large undirected graphs using the *spring* model, but it uses a multi-scale approach to produce layouts of large graphs in a reasonably short time.
* `patchwork` is a filter for tree maps. It draws the graph as a squarified treemap.
* `osage` is a filter for tree maps. It draws the graph using its cluster structure. For a given cluster, each of its sub clusters is laid out internally. Then the sub clusters, plus any remaining nodes, are repositioned based on the cluster’s pack and packmode attributes.

## Layout parameter

| Parameter | Description | dot | neato | fdp | circo | twopi | Default value | Examples |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **size** | Maximum size of the diagram | XX | XX | XX | XX | XX | -- | "3,3" (small), "10.3,5.3" (fits 1024px) |
| **ranksep** | distance between hierarchical ranks | X | &nbsp; | &nbsp; | &nbsp; | XXX | 0.5 (dot), 1.5 (twopi) | 0.1 (very tiny), 0.6 (large) |
| **nodesep** | minimal distance to two hierarchical identical nodes | X | &nbsp; | &nbsp; | &nbsp; | &nbsp; | 0.25 | nodesep=0.05 (very tine) |
| **len** | preferred edge(!) length, edge attribute | &nbsp; | XXX | X | &nbsp; | &nbsp; | 1.0 (neato), 0.3 (fdp) | 0.5 |
| **mindist** | changes spaces for circos diagrams | &nbsp; | &nbsp; | &nbsp; | XXX | &nbsp; | &nbsp; | 0.5 (few nodes), 0.01 (many nodes) |
| **ratio** | favored ratio | X | X | X | X | X | -- | 2 (portrait format) |
| **start** | influences node segmentation | &nbsp; | X | XXX | &nbsp; | &nbsp; | &nbsp; | 2 |
| **overlap** | are overlaps allowed? | &nbsp; | X | X | &nbsp; | &nbsp; | true | false (otherwise edges collapse possibly) |

The more crosses (XXX), the more important is the parameter.  
cf. [Graphviz-Tutorial](http://4webmaster.de/wiki/Graphviz-Tutorial) (german)

## Terminal commands

* Simple example: `dot -Tsvg <inputfile.xx> -o <outputfile.xx>` transforms to SVG.
* [Command-line Invocation](http://graphviz.org/content/command-line-invocation)

## Tutorials

* Very good [Graphviz-Tutorial](http://4webmaster.de/wiki/Graphviz-Tutorial) (german)
* Official [General Commands Manual](http://www.graphviz.org/pdf/dot.1.pdf)
* [Drawing Graphs using Dot and Graphviz](http://www.tonyballantyne.com/graphs.html)
* Video: [Step-by-Step GraphViz Walkthrough](http://vimeo.com/7860697)
* Video: [RaumZeitLabor: Graphen coden statt zeichnen mit Graphviz](http://youtu.be/mQza_2QSIO8)

## Other interesting links

* [mdaines/viz.js](https://github.com/mdaines/viz.js) is a hack to put Graphviz on the web.
* [goinnn/jquery.graphviz](https://github.com/goinnn/jquery.graphviz/) animates a SVG generated with Graphviz.
* [gvpr](https://www.mankier.com/1/gvpr) (previously known as gpr) is a graph stream editor inspired by [awk](http://en.wikipedia.org/wiki/AWK). It copies input graphs to its output, possibly transforming their structure and attributes, creating new graphs, or printing arbitrary information.
* Official [Graphviz gallery](http://www.graphviz.org/Gallery.php)
* [A Gallery of Large Graphs](http://yifanhu.net/GALLERY/GRAPHS/index.html). A graph visualization of matrices from the University of Florida Collection. All generated with the sfdp layout engine, but colorized by postprocessing the PostScript files.
* [A Python-Markdown Extension for Embedding Graphviz](http://lethain.com/a-python-markdown-extension-for-embedding-graphviz/), Graphviz plug-in for Grunt
* [Gephi](http://gephi.github.io) is an open-source network analysis and visualization software package written in Java on the NetBeans platform, initially developed by students of the University of Technology of Compiègne (UTC) in France.
* [grunt-graphviz](https://www.npmjs.org/package/grunt-graphviz)
* [D3 gallery](https://github.com/mbostock/d3/wiki/Gallery). D3.js is a JavaScript library that uses digital data to drive the creation and control of dynamic and interactive graphical forms which run in web browsers. It is a tool for data visualization in W3C-compliant computing, making use of the widely implemented Scalable Vector Graphics (SVG), JavaScript, HTML5, and Cascading Style Sheets (CSS3) standards.
*[Interesting D3.js examples by Mike Bostock](http://bost.ocks.org/mike/example/)

## Interesting code snippets

```
digraph G { 
  compound=true; 
  ranksep=1.25; 
  label="From Past to Future..."; 

  node [shape=plaintext, fontsize=16]; 

  bgcolor=white; 
  edge [arrowsize=1, color=black]; 

  /* Nodes */ 
  subgraph cluster_Computers {label="Computers"; labelloc="b"; Computers_icon}; 
  Computers_icon [label="", shape=box, style=invis, shapefile="Computers.png"]; 

  subgraph cluster_Semantic_Web {label="Semantic Web"; labelloc="b"; Semantic_Web_icon}; 
  Semantic_Web_icon [label="", shape=box, style=invis, shapefile="Semantic_Web.png"]; 

  subgraph cluster_Cryptography {label="Cryptography"; labelloc="b"; Cryptography_icon}; 
  Cryptography_icon [label="", shape=box, style=invis, shapefile="Cryptography.png"]; 

  subgraph cluster_Automata {label="Automata"; labelloc="b"; Automata_icon}; 
  Automata_icon [label="", shape=box, style=invis, shapefile="Automata.png"]; 

  subgraph cluster_AI {label="A.I."; labelloc="b"; AI_icon}; 
  AI_icon [label="", shape=box, style=invis, shapefile="AI.png"]; 

  subgraph cluster_Chaos {label="Chaos / Fractals"; labelloc="b"; Chaos_icon}; 
  Chaos_icon [label="", shape=box, style=invis, shapefile="Chaos.png"]; 

  subgraph cluster_XML {label="XML / RDF / URI"; labelloc="b"; XML_icon}; 
  XML_icon [label="", shape=box, style=invis, shapefile="XML.png"]; 

  subgraph cluster_Ontology {label="Ontology / Clustering"; labelloc="b"; Ontology_icon}; 
  Ontology_icon [label="", shape=box, style=invis, shapefile="Ontology.png"]; 

  subgraph cluster_Biology {label="Biology / Neurons"; labelloc="b"; Biology_icon}; 
  Biology_icon [label="", shape=box, style=invis, shapefile="Biology.png"]; 

  subgraph cluster_Agents {label="Agents / Security"; labelloc="b"; Agents_icon}; 
  Agents_icon [label="", shape=box, style=invis, shapefile="Agents.png"]; 

  subgraph cluster_Small_World {label="The Small World Project"; labelloc="b"; Small_World_icon}; 
  Small_World_icon [label="", shape=box, style=invis, shapefile="Small_World.png"]; 

  subgraph cluster_Social_Networks {label="Social Networks"; labelloc="b"; Social_Networks_icon}; 
  Social_Networks_icon [label="", shape=box, style=invis, shapefile="Social_Networks.png"]; 

  subgraph cluster_Search_Engines {label="Search Engines"; labelloc="b"; Search_Engines_icon}; 
  Search_Engines_icon [label="", shape=box, style=invis, shapefile="Search_Engines.png"]; 

  subgraph cluster_Turing {label="A. Turing"; labelloc="b"; Turing_icon}; 
  Turing_icon [label="", shape=box, style=invis, shapefile="Turing.png"]; 

  subgraph cluster_Rejewski {label="M. Rejewski"; labelloc="b"; Rejewski_icon}; 
  Rejewski_icon [label="", shape=box, style=invis, shapefile="Rejewski.png"]; 

  subgraph cluster_Dertouzos {label="M. Dertouzos"; labelloc="b"; Dertouzos_icon}; 
  Dertouzos_icon [label="", shape=box, style=invis, shapefile="Dertouzos.png"]; 

  subgraph cluster_Berners_Lee {label="T. Berners-Lee"; labelloc="b"; Berners_Lee_icon}; 
  Berners_Lee_icon [label="", shape=box, style=invis, shapefile="Berners_Lee.png"]; 

  /* Relationships */ 
  Computers_icon -> Semantic_Web_icon; 
  Semantic_Web_icon -> Computers_icon; 
  Cryptography_icon -> Semantic_Web_icon; 
  Cryptography_icon -> Computers_icon; 
  Automata_icon -> Computers_icon; 
  AI_icon -> Automata_icon; 
  Automata_icon -> AI_icon; 
  Chaos_icon -> Computers_icon; 
  Chaos_icon -> AI_icon; 
  AI_icon -> Chaos_icon; 
  Computers_icon -> Chaos_icon; 
  XML_icon -> Semantic_Web_icon; 
  XML_icon -> Computers_icon; 
  Computers_icon -> XML_icon; 
  Ontology_icon -> Semantic_Web_icon; 
  Biology_icon -> AI_icon; 
  Biology_icon -> Chaos_icon; 
  Chaos_icon -> Biology_icon; 
  Chaos_icon -> Semantic_Web_icon; 
  Agents_icon -> Semantic_Web_icon; 
  Semantic_Web_icon -> Agents_icon; 
  Agents_icon -> AI_icon; 
  AI_icon -> Agents_icon; 
  Small_World_icon -> Chaos_icon; 
  Small_World_icon -> Agents_icon; 
  Small_World_icon -> Biology_icon; 
  Biology_icon -> Small_World_icon; 
  Social_Networks_icon -> Small_World_icon; 
  Social_Networks_icon -> Biology_icon; 
  Search_Engines_icon -> Semantic_Web_icon; 
  Computers_icon -> Search_Engines_icon; 
  Turing_icon -> Cryptography_icon; 
  Turing_icon -> Computers_icon; 
  Turing_icon -> Automata_icon; 
  Rejewski_icon -> Turing_icon; 
  Rejewski_icon -> Cryptography_icon; 
  Dertouzos_icon -> Computers_icon; 
  Dertouzos_icon -> Berners_Lee_icon; 
  Berners_Lee_icon -> Semantic_Web_icon; 

  { rank=same; Rejewski_icon; Turing_icon; Dertouzos_icon; Berners_Lee_icon }; 
  { rank=same; Biology_icon; AI_icon; Social_Networks_icon }; 
} 
```

Source: [How to use Graphviz to generate complex graphs](http://www.karakas-online.de/forum/viewtopic.php?t=2647)