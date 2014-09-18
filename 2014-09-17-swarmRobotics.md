---
layout: post
title: "Swarm Robotics"
slug: "research-swarm-robotics"
date: 2014-09-18 12:55
comments: true
categories: [iot]
tags: [internet of things, iot, m2m, robotics, machine learning, automation, swarm, swarm robotics, automaton, android, golem]
published: true
---

# Swarm Robotics

## Frameworks

### theHybridGroup

#### Cylon.js

Cylon.js is a JavaScript framework for robotics, physical computing, and the Internet of Things using Node.js. Cylon.js is also supported by "[Skynet.im/Meshblu](http://skynet.im/)".

* [Official website](http://cylonjs.com/)

Cylon.js does…

* …support multiple hardware devices
* …support different hardware devices
* …support multiple & different hardware devices at the same time
* …have test-driven robotics built-in
* …have a CLI (through [Gort](http://gort.io))

##### Resources

* [Official examples](http://cylonjs.com/documentation/examples/) and [Tutorials](http://cylonjs.com/documentation/tutorials/)
* Video: [Cylon.js: The JavaScript Evolution Of Open Source Robotics - Ron Evans, Adrian Zankich](https://www.youtube.com/watch?v=AJ1VH4AqqWc) – even though the demo he is showing does not work properly.
* Video: [Ron Evans: Cylon.js: The JavaScript Evolution Of Open Source Robotics [JSConf2014]](https://www.youtube.com/watch?v=bnFWskconEg), again some of the demos fail
* Video: [Ron Evans: Cylon.js: The JavaScript Evolution Of Open Source Robotics](http://vimeo.com/96477741), this time the demo work
* [Cylon.js on RasPi tutorial - Making the LED blink](http://nemron.com/blog/cylon-js-on-raspberry-tutorial-making-the-led-blink/)
* Github: [Cylon.js for ARDrone](https://github.com/hybridgroup/cylon-ardrone)
	* Github: [Cylon.js + ARDrone example](https://github.com/hybridgroup/cylon-ardrone/tree/master/examples) e.g. Face Tracking
* [Node Rockets](https://twitter.com/NodeRockets)

##### Adaptors

* [Arduino with Cylon.js](http://cylonjs.com/documentation/platforms/arduino/)
* [RasPi with Cylon.js](http://cylonjs.com/documentation/platforms/raspberry-pi/)
* [Sphero with Cylon.js](http://cylonjs.com/documentation/platforms/sphero/)
* [Skynet with Cylon.js](http://cylonjs.com/documentation/platforms/skynet/)
	* Video: [Connecting CylonsJS to SkyNet](https://www.youtube.com/watch?v=jNta2z3dYII)
	* [Example code](https://github.com/octoblu/examples/blob/master/cylon.js)
* Github: [Cylon.js adaptor/drivers for Bluetooth LE](https://github.com/hybridgroup/cylon-ble)
* [watchbot.io](http://www.watchbot.io). A Pebble app to control robots from your wrist.

Quote 1:

> The platforms you support seems to be a mix of UI elements, pre-built hardware, software and boards. How do they interact?

> We call it “full-stack robotics,” and we have adopted several different software design patterns to integrate different layers together in a seamless way. Similar to how web developers can switch between different database engines, we allow you connect to different devices, and even switch from one platform to another with a minimum number of code changes. We also support “Test-Driven Robotics” to allow devs to write automated tests before writing code on the actual hardware.

Quote 2:

> How does Cylon.js ‘support’ something like the Arduino or the Digispark that doesn’t speak Javascript?

> Cylon.js also supports many different kinds of communication with devices, such as serial or TCP/UDP. In the case of the Arduino we communicate using the Firmata protocol, and in the case of the Digispark we support a protocol named Littlewire created by the brilliant Jenna Fox that runs on even smaller micro-controllers such as the Digispark.

#### Gobot 

Gobot is a set of Go libraries for robotics and physical computing.

* [Official website](http://gobot.io/)
* [Official blog](http://gobot.io/blog/)
* [Official documentation](http://gobot.io/documentation/getting-started/)
* [Github repository](https://github.com/hybridgroup/gobot/)
* Video: [GopherCon 2014 Gobot: Go Powered Robotics and Physical Computing by Ron Evans and Adrian Zankich](https://www.youtube.com/watch?v=Va-NE55AqBs)

#### Artoo

Artoo is a framework for robotics, physical computing, and the Internet of Things written in the Ruby programming language.

* [Official website](http://artoo.io/)
* [Official website](http://artoo.io/documentation/)

### Johnny-Five

Johnny-Five is an Open Source, JavaScript Arduino programming framework.

* Github: [rwaldron/johnny-five](https://github.com/rwaldron/johnny-five)
* [nodebot-workshop](https://www.npmjs.org/package/nodebot-workshop). A nodeschool workshop on getting your ardunio alive with johnny-five.
* [Awesome Nodebots Built with Johnny-Five](https://github.com/rwaldron/johnny-five/blob/master/awesome.md)
* Video: [Raquel Velez - LXJS 2013 - NodeBots](https://www.youtube.com/watch?v=SssnWZzLGvo)
* Presentation: [Robots... and JavaScript?! by Raquel Vélez](https://speakerdeck.com/rockbot/robots-dot-dot-dot-and-javascript)

## Further tools

* [RobotOps](http://robotops.com) – DevOps for Robotics
* [Gort](http://gort.io) is a **Command Line Interface (CLI)** for RobotOps. Gort provides tools to scan for connected devices, upload firmware, and more. You install Gort separately from any framework, which means you can use it to program Arduinos with the Firmata firmware also compatible with Cylon.js, Gobot, Artoo, & Johnny-Five.
* Github: [hybridgroup/robeaux](https://github.com/hybridgroup/robeaux). Robeaux (/rō-bō/) is a universal dashboard to your robotic devices. Like a router admin page, but for robots. It is powered by AngularJS, and provides a front-end to the API interface offered by Artoo, Cylon.js and Gobot.
* [Breakout.js](http://breakoutjs.com)

## Interesting articles & resources

* Video: [Networked mobile robots with Python or JavaScript on BeagleBone - Jason Kridner](https://www.youtube.com/watch?v=B2Sqmg5wHiE)
* [Bot & Dolly and the Rise of Creative Robots](http://www.businessweek.com/articles/2014-03-20/bot-and-dolly-and-the-rise-of-creative-robots)
* Video: [Box by Bot & Dolly](http://vimeo.com/75260457)
* Video: [Box by Bot & Dolly | Behind the Scenes](https://www.youtube.com/watch?v=y4ajXJ3nj1Q)
* [Here come the bots: meet the seven types of robot that Google has purchased](http://www.independent.co.uk/life-style/gadgets-and-tech/here-come-the-bots-meet-the-seven-types-of-robot-that-google-has-purchased-8985870.html)
* [theHybridGroup blog](http://hybridgroup.com/blog/)
* [Control Robots From Your Pebble](http://cylonjs.com/blog/2014/07/22/control-robots-from-your-pebble/#.VBmJ_mR9-Qs) with Cylon.js
* [NodeBots](http://nodebots.io)
* [Johnny-Five compared to Cylon: Hello](https://gist.github.com/rwaldron/7760342)
* Event: [Robots Conf](http://2014.robotsconf.com)
* Presentation: [Open-Source Swarm Robotics: Drones](http://slides.com/johntaborda/swarm_drones#/)
* Article: [NodeBots - The Rise of JS Robotics](http://www.voodootikigod.com/nodebots-the-rise-of-js-robotics/)