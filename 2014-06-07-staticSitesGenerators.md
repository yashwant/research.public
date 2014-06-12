---
layout: post
title: "Using Static Site Generators for web development"
slug: "research-using-static-site-generators-for-web-development"
date: 2014-06-07 11:47
comments: true
categories: [devops]
tags: [frank, greendog, jekyll, mercury, middleman, nanoc, serve, staticmatic]
published: false
---

# Using Static Site Generators for web development

## Static Site Generators

If you want to find out more on the term "Static Site Generators" read this very helpful article: "[An Introduction to Static Site Generators](http://www.mickgardner.com/2011/04/27/An-Introduction-To-Static-Site-Generators.html)".  
I personally tend to use **Jekyll** or **Middleman** but let me give you an overview:

* [frank](https://github.com/blahed/frank) uses Tilt, so it comes with support for Haml & Sass, LESS, Builder, ERB, and Liquid.
* [greendog](https://github.com/greendog99/greendog-rails-template) is a Rails 3 template with HTML5 Boilerplate in Haml and Sass, plus other goodies
* [jekyll](https://github.com/henrik/jekyll) is a blog-aware, static site generator in Ruby
	* [Octopress](http://octopress.org/) is a framework designed by Brandon Mathis for Jekyll, the blog aware static site generator powering Github Pages. To start blogging with Jekyll, you have to write your own HTML templates, CSS, Javascripts and set up your configuration. But with Octopress All of that is already taken care of.
	* [Example for a Jekyll RSS/Atom feed](http://coyled.com/2010/07/05/jekyll-templates-for-atom-rss/)
	* [Jekyll and live feeds update with pubhubsubbub](http://www.rfc1149.net/blog/2010/11/28/jekyll-and-live-feeds-update/)
	* [Jekyll RSS feeds](https://github.com/snaptortoise/jekyll-rss-feeds)
* [mercury](https://github.com/jackhq/mercury) to quickly create Haml, Sass, JQuery Web Sites. Technology used Haml, Sass, Coffee Script, Markdown
	* [**mercury stacks**](https://github.com/jackhq/mercury/wiki/Mercury-Stacks)
* [**Middleman**](http://middlemanapp.com/) is a static site generator based on Sinatra. Providing dozens of templating languages (Haml, Sass, Compass, Slim, CoffeeScript, and more). Makes minification, compression, cache busting, Yaml data (and more) an easy part of your development cycle.
	* [**breakfast**](https://github.com/jeffjewiss/breakfast), start your project with a healthy diet — Slim, Sass, HTML5BP, **GGS** (runs on Middleman). 
* [nanoc](https://github.com/ddfreyne/nanoc) is a web publishing system written in Ruby. It operates on local files, and therefore does not run on the server. nanoc “compiles” the local source files into HTML (usually), by evaluating eRuby, erb, Markdown, Haml, Sass etc.
* [serve](https://github.com/jlong/serve) is a small Rack-based web server and rapid prototyping framework for Web applications (specifically Rails apps). It is designed to compliment web application development and enforce a strict separation of concerns between designer and developer. Using Serve allows the designer to work in a separate prototype project, while the developer can work on the actual application and utilize resources from the prototype as needed. This allows the designer to focus on presentation and flow, while the developer can focus on implementation
* [StaticMatic](http://staticmatic.rubyforge.org/)
	* [Compass StaticMatic integration](https://github.com/chriseppstein/compass/wiki/staticmatic-integration)
	* [StaticMatic Bootstrap](https://github.com/adamstac/staticmatic-bootstrap) with support for Haml, Sass, Compass and jQuery
* [tinySite](http://tinysite.heroku.com/) is a small static site engine with Heroku and Dropbox in mind. The idea is to host the app for a site on Heroku and take advantage of their awesome application stack and provide the static content via Dropbox. Works with **Middleware** and naturally supports Haml files.

| *Criteria* | **frank** | **greendog** |  **jekyll** | **mercury** | **Middleman** | **nanoc** | **serve** | **StaticMatic** |
| ---------- | --------- | ------------ | ----------- | ----------- | ------------- | --------- | --------- | --------------- |
| *Language* | Ruby | Ruby | Ruby | Ruby | Ruby | Ruby | Ruby | Ruby |
| *Template support* | Haml, Sass, Less, Erb, Liquid, Markdown by using Tilt (frank) | Haml, Sass, HMTML5 Boilerplate (green dog) | Compass, Liquid, Markdown, Haml, Sass (jekyll) | Haml, Sass, Less, Erb, Liquid, Markdown by using Tilt (mercury) | Haml, Sass, Less, Erb, Liquid, Markdown by using Tilt (Haml by extension) (middleman) | Markdown (everything else can be added manually) (nano) | Compass, Haml, Sass, Less, Erb, Liquid, Markdown by using Tilt (serve) | Haml, Sass, Compass (staticMatic) |
| *Packages* | / (frank) | Rails, Builder (greendog) | Foreman (jekyll) | / (mercury) | Bundler, Sprockets (middleman) | / (nanoc) | Coffee Script (serve) | / (staticmatic) |
| *Webserver* | Mongrel, Rack, Tilt (frank) | Rack (greendog) | Thor (jekyll) | Rack (mercury) | Rack, Thor (middleman) | has to be compiled (nanoc) | Rack, Tilt (serve) | Rack (staticmatic) |
| *last updated (checked August 29th, 2011)* | August 4th, 2010 (frank) | July 27th, 2011 (greendog) | July 16th, 2011 (jekyll) | June 29th, 2011 (mercury) | August 22th, 2011 (Middleman) | August 15th, 2011 (nanoc) | August 11th, 2011 (nanoc) | November 15th, 2010 (staticMatic) |

#### Frank
##### Installation
	rvm create gemset <name>
	rvm use 1.9.2@<name>
	gem install frank
	# create a project
	frank new <projectName>
	# start server
	frank server
	# frank supports Haml/Sass out of the box

1. Edit setup.rb to set your server options, folder names for static/dynamic content, and layouts for your views.
2. Stash your static files (images, flash movies, etc) in the folder that you set as `[static_folder]`.
3. Frank will look for files in the `[dynamic_folder]` first and try to compile them. Example: a request for `/css/johndoe.css` will look for a file in `[dynamic_folder]/css/` named `johndoe`. Frank uses the file extension to determine the correct compiler.

#### Greendog
Greendog is just a template that enables Rails to support HTML5 Boilerplate, Haml, Sass etc.. It will be kinda outdated when Rails 3.1 comes out because of its natural support for those formats. Therefore I did not see any need to test.

#### Jekyll
Jekyll comes really, really basic first. You have to create your own skeleton (or use one from Github). Supports migrating from other platforms like Movable Type, Drupal, WordPress, Marley and Typo. It supports Pagination, Permalinks, Tagging etc.. Therefore if you want i.e. build a blog Jekyll seems to be perfect.

* [Octopress](http://octopress.org/), a blogging framework for Hackers (based on Jekyll)

##### Installation
`rvm create gemset <name>`  
`rvm use 1.9.2@<name>` 
`gem install jekyll`  
get a jekyll skeleton  
`jekyll html5-boilerplate skeleton`  
`git clone https://github.com/ericdfields/HTML5-Boilerplate-Jekyll-Template.git`  
**alternative**, but way older `git clone https://github.com/philippbosch/jekyll-skeleton.git`  
**alternative**, but more complex `git clone https://github.com/robbevan/jekyll-skeleton.git`  
install foreman for process management `gem install foreman`  
`touch Procfile`  
add those lines  
`jekyll:  jekyll --server`  
`compass: compass watch`  
start the process `foreman start`

#### Work Environment
change .scss to .Sass syntax  
`vim config.rb`  
uncomment this line `preferred_syntax = :sass`  
update all files to .sass and delete the .scss files  
`sass-convert -R --from scss --to sass scss scss && rm -rf sass && mv scss sass`  
to auto compile the files I generated a Procfile, but you first have to install Foreman  
`gem install foreman`  
`touch Procfile`  
`vim Procfile`  
add  
`jekyll:  jekyll --server`  
`compass: compass watch`  
one of the biggest disadvantage is that jekyll does not work with Haml files though, I didn't manage to get a workaround/hack.

##### Configuration example

	url: http://localhost:4000 #XXX
	title: Site Name #XXX
	description: Tag line #XXX
	author: A. U. Thor #XXX
	email: a.u.thor@example.com #XXX
	analytics_id: #Google Analytics ID : UA-xxx-xxx  
	
	auto: false
	lsi: false
	pygments: false
	server_port: 4000
	markdown: maruku
	
	maruku:
	  use_tex: false
	  use_divs: false
	  png_dir: img/tex
	  png_url: /img/tex

[Source](https://github.com/btbytes/jekyll_960/blob/master/_config.yml)

##### Templating
* [YAML Front Matter](https://github.com/mojombo/jekyll/wiki/YAML-Front-Matter)
* [Liquid](https://github.com/Shopify/liquid/wiki)
* [Liquid Extensions](https://github.com/mojombo/jekyll/wiki/liquid-extensions)
* [Liquid for Designers](https://github.com/shopify/liquid/wiki/liquid-for-designers)
* [Liquid Markup](http://www.liquidmarkup.org/), Ruby library for rendering safe templates which cannot affect the security of the server they are rendered on.
* [Kismetik](http://www.kismetik.com/journal/)

More sites can be found [here](https://github.com/mojombo/jekyll/wiki/sites).

##### Deployment
* [Capistrano Recipe for Deploying a Blog Using Jekyll and Compass](http://forrst.com/posts/Capistrano_Recipe_for_Deploying_a_Blog_Using_Jek-z5l)

##### Documentation
* [Jekyll Wiki](https://github.com/mojombo/jekyll/wiki)
* [Weblog example](https://github.com/valo/valentinmihov.com), really worth checking out. Using a couple of extensions

##### Articles
* [Building Static Sites with Jekyll](http://net.tutsplus.com/tutorials/other/building-static-sites-with-jekyll/)
* [How to use Haml and Compass with Jekyll](http://martinciu.com/2011/06/blogging-like-a-hacker-using-jekyll-compass-and-foreman.html)
* [How To: WordPress to Jekyll](http://paulstamatiou.com/how-to-wordpress-to-jekyll)
* [Jekyll on Heroku using Sinatra](http://devart.org/jeykll-on-heroku-with-sinatra), *important* afaik it is possible to run Jekyll on Heroku without Sinatra
* [jekyll vs. hyde - a comparison of two static site generators](http://philipm.at/2011/0507/)
* [Migrating from WordPress 3.0 to Jekyll](http://rubenlaguna.com/wp/2010/08/05/migrating-from-wordpress-to-jekyll/)
* [Publishing a Blog with GitHub Pages and Jekyll](http://blog.envylabs.com/2009/08/publishing-a-blog-with-github-pages-and-jekyll/)

##### Extensions/Plugins
* [jekyll_and_hyde](https://github.com/jingweno/jekyll_and_hyde), a HTML presentation generator that generates a basic Jekyll scaffold with Slippy hooking up
* [Blogging with Jekyll, Haml, Sass, and Jammit](http://mikeferrier.com/2011/04/29/blogging-with-jekyll-haml-sass-and-jammit/)
* [the_minimum](http://www.layouts-the.me/), a Jekyll theme
* [AliasGenerator, FlickrSetTag](http://thomasmango.com/2011/08/26/generated-by-jekyll-and-open-source-plugins/)

##### Example sites
* [mojombo.github.com (Source)](https://github.com/mojombo/mojombo.github.com)
* [git ready (Source)](https://github.com/gitready/gitready)
* [rebase (Source)](https://github.com/rebase/rebase.github.com)
* [qrush (Source)](https://github.com/qrush/qrush.github.com)
* [… more Jekyll powered sites](https://github.com/mojombo/jekyll/wiki/Sites)
* [litany against fear](http://quaran.to/blog/2009/05/07/railsconf-2009-webrat-rails-testing-evolved/)

#### Mercury
Mercury is last updated June, 29th 2010. It seems a little outdated and the documentation has quite some bugs.  
[Middleman Getting Started Tutorial](http://middlemanapp.com/guides/getting-started/)

##### Installation

`gem install mercury`  
create a new folder for your project `mercury <projectName>`  
create your Haml files  
`cd <projectName>`  
`touch wwwroot/index.haml`  
i.e. <name.haml> will not be recognized  
run the webserver  
cd back to the root directory and start by typing… `mercury`  
the web server runs on `http://localhost:9292`

#### Middleman
##### Installation

`rvm create gemset <name>`  
`rvm use 1.9.2@<name>`  
`gem install middleman`  
start a new site `middleman init <projectName>`  
**alternative** with config.ru `middleman init <projectName> --rack`  
**alternative** with config.ru and GEMFILE `middleman init <projectName> --rack --bundler`  
alternative with HTML5 boilerplate `middleman init <projectName> --template=html5`  
show help `middleman init --help`

##### Exporting

Exporting to i.e. Heroku
`middleman build`

##### Structure
If you are using i.e. Haml you have to generate and use `layout.html.haml` and `index.html.haml` files they could look like this (otherwise your site will not be rendered)

##### More Commands
`middleman init`  
`middleman server`  
`middleman build`

##### Templates
* [Middleman Bootstrap](https://github.com/nathos/middleman-bootstrap) is a clean project starting point for the Middleman static site generator. It includes HTML5 boilerplate, your choice of grid systems, and lots of best practices.

##### Example sites
* [EURUcamp website (Source)](https://github.com/myabc/eurucamp_website)
* [Services Informatiques (Source)](https://github.com/OyoKooN/Services-informatiques)
* [kpricorn.org (Source)](https://github.com/sdecastelberg/kpricorn.org)
* [Award Winning Fjords (Source)](https://github.com/tdreyno/awardwinningfjords)
* [Estudio Nacar (Source)](https://github.com/jbarreneche/Estudio-Nacar)
* [Susanne Theisen (Source)](https://github.com/mguth/susanne-theisen)

#### nanoc

`gem install nanoc`  
`nanoc create_site <projectName>`  
`nanoc compile`  
add markdown support `gem install kramdown`  
compile the site `nanoc compile`  
run the webserver `nanoc view`  
open the url `http://localhost:3000/`

#### Serve
Serve is quite complex. It has a similar "Views" part just like Rails (Views, Partials & Layouts). Sass and Compass are already built-in, content can also be delivered static or dynamic.

##### Installation

`gem install serve`
start the webserver `serve`
the webserver is available at `http://localhost:4000`  
create a new project in the project directory `serve create <projectName>`  
to enable Haml, Sass etc. you have to edit the "Gemfile" `vim Gemfile`  
to install the missing Gems you have to install "Bundler" `gem install bundler`  
and install the missing Gems `bundle install`

#### statis
I still have to **test** [stasis](http://stasis.me/)

#### StaticMatic
StaticMatic comes really *plain*. Haml and Sass support worked out of the box.

##### Installation

`gem install staticmatic`  
`staticmatic setup <projectName>`  
start the webserver `staticmatic preview .`  
the webserver runs on `http://localhost:3000`

##### Articles
* [Haml, Compass, Front-end development](http://boban.jovanoski.net/posts/5-haml-compass-front-end-development)

### Cookbooks
* [37Signals Cookbooks](https://github.com/37signals/37s_cookbooks)
* [laptop](https://github.com/thoughtbot/laptop), Laptop is a set of scripts to get your laptop set up as a development machine.