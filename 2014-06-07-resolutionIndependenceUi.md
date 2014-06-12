---
layout: post
title: "Resolution independence"
slug: "research-resolution-independence"
date: 2014-06-07 12:04
comments: true
categories: [technology]
tags: [ipad, hd, resolution, responsive]
published: true
---

# Resolution independence

## Devices

* **iPhone:** 320x480, 3.5 in,164ppi
* **Palm Pre:** 320x480, 3.1 in 186ppi
* **Palm Pixie:** 320x400, 2.63 in, 194ppi
* **T-Mobile G1:** 320x480, 3.2 in, 180ppi
* **MyTouch 3G:** 320x480, 3.2 in, 180ppi
* **HTC Hero:** 320x480, 3.2 in, 180ppi
* **Motorola Droid:** 480x854, 3.7 in, 264ppi
* **Nexus One:** 480x800, 3.7 in, 252ppi
* **HTC Desire:** 480x800, 3.7 in, 252ppi
* **Nokia N97:** 360x640, 3.2 in, 229ppi
* **Nokia N900:** 800x480, 3.5 in, 266ppi
* **Apple iPhone 4:** 960x640, 3.5 in, 326ppi
* **the new iPad**
* e.g. the current 27" iMac is 109ppi

## Resolution-responsive techniques

* CSS 3 ([CSS Hat](http://csshat.com/) for e.g. gradients etc.), CSS to render UI Elements 
* Use vectors or "Smart Objects"" in Photoshop
* SVG
	* [Resolution Independence With SVG](http://coding.smashingmagazine.com/2012/01/16/resolution-independence-with-svg/)
	* [Using SVG For Flexible, Scalable, and Fun Backgrounds, Part I](http://www.alistapart.com/articles/using-svg-for-flexible-scalable-and-fun-backgrounds-part-i/)
	* [SVG resize problem](http://simurai.com/post/19895985870/icon-sharpness-limbo)
	* [Browser Support](http://caniuse.com/#search=svg)
* @media queries (e.g. target HD/Retina Displays @2x)
* @font face or icon kits
	* [Icon Fonts](http://css-tricks.com/examples/IconFont/)
	* [Fontello](http://fontello.com/) alternative [IcoMoon](http://keyamoon.com/icomoon/)	
* detect network speed
* Images
	* [Responsive & Retina Content Images Redux using Media Queries & a base64 spacer GIF](http://www.mattstow.com/responsive-and-retina-content-images-redux.html)
	* [Responsive Images Chart](https://docs.google.com/spreadsheet/ccc?key=0Al0lI17fOl9DdDgxTFVoRzFpV3VCdHk2NTBmdVI2OXc#gid=0)
	* [Compass/SASS Mixins for Simple Retina Images on Websites](http://blog.joelambert.co.uk/2012/03/09/compass-sass-mixins-for-simple-retina-images-on-websites/)
	* [Retina.js](http://retinajs.com/) is an open source script that makes it easy to serve high-resolution images to devices with retina displays
	* [Foresight.js](https://github.com/adamdbradley/foresight.js) gives webpages the ability to tell if the user's device is capable of viewing high-resolution images

## Things to consider

* If you want your applications and web sites to look beautiful on the iPhone 4's new retina screen, you are going to have to create high-resolution versions of your bitmaps and/or use vectors.
* You basically have to design liquid interfaces (and interface elements) for your apps.
* SVG can help in creating resolution-independent designs.
* Since browsers do not currently have automatic support for loading high-resolution versions of image and video assets, we can use a combination of CSS media queries and JavaScript for the same effect.  
With CSS3 media queries you can then build Web sites with completely different CSS files based off the pixel-ratio of CSS pixels to device pixels, including higher res artwork as necessary.  
This approach also degrades gracefully, since you can specify the lowres CSS file and then higher res CSS files inside media queries that will be ignored by browsers that don’t understand them.

## What "true" Apple Retina Displays would look like…

| Model | Screen Size (Inches) | Average Distance | Retina Res (Apple) | True Retina Res | PPI |
| ----- | -------------------- | ---------------- | ------------------ | --------------- | --- |
| iPhone | 3.5 | 12 | 960x640 | 2772 x 1848 | 952 |
| iPad | 9.7 | 15 | 2048 x 1536 | 5968 x 4486 |769 |
| 11-inch MacBook Air | 11.6 | 22 | 2732 x 1536 | 5184 x 2916 | 513 |
| 13-Inch MacBook Air | 13.3 | 22 | 2880 x 1800 | 5872 x 3670 | 520 |
| 15-Inch MacBook Pro | 15.4 | 24 | 2880 x 1800 | 6096 x 3810 | 467 |
| 21-Inch iMac | 21.5 | 28 | 3840 x 2160 | 7408 x 4168 | 395 |
| 27-Inch iMac | 27 | 28 | 5120 x 2880 | 9120 x 5130 | 388 |

Source: [Cult of Mac](http://www.cultofmac.com/173702/why-retina-isnt-enough-feature/)

## Helpful tools

* [iPhone 4 GUI PSD (Retina Display)](http://www.teehanlax.com/blog/iphone-4-gui-psd-retina-display/)