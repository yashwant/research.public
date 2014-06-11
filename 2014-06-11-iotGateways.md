---
layout: post
title: "Internet of Things Gateways"
slug: "research-internet-of-things-gateways"
date: 2014-06-11 16:03
comments: true
categories: [technology]
tags: [gateways, internet of things, iot, smart things, ninja blocks]
published: true
---

# Internet of Things Gateways
## Smart Things

[Smart Things]((http://www.smartthings.com/)) is a group of devices which can be monitored and controlled via hub and web services.

* SmartThings primarily use ZigBee HA (with Z-Wave also natively supported by the Smart Hub) and both of these standards use mesh-networking (every non-battery powered node is a repeater – router) for superior range (perhaps limitless range!).
* [SmartThings Apps are written in Groovy](http://build.smartthings.com/smartthings-documentation/) not Ruby

### Resources

* [Official Website](http://www.smartthings.com/)
* [SmartThings YouTube channel](http://www.youtube.com/user/mySmartThings)
* [Ubi & Smart Things](http://www.youtube.com/watch?v=0CcaK8g2rS0#t=26)

## Twine

[Twine](http://supermechanical.com/) is an inexpensive, customizable little box that can be rigged to monitor your home for various changes or actions, and alert you when they happen.

### Resources

* [Official Website](http://supermechanical.com/)
* [Twine Kickstarter project](http://www.kickstarter.com/projects/supermechanical/twine-listen-to-your-world-talk-to-the-internet)

## Electric Imp

While [Ninja Blocks](http://ninjablocks.com/) has an actual finished and usable product, Electric Imp is more of a platform to add wireless communications to devices by using a SD-card like chip. They’re targeting mainly manufacturers and geeks so they can implement cool things with it. The is an Hannah Development Board from [smARtMAKER](http://smartmaker.com/). Costs around 45 USD.

### Resources

* [Official Website](http://electricimp.com/)

## Ubi (voice control)

The ubiquitous computer, or Ubi, is a small Android powered computer with built-in sensors that is controlled and activated entirely by voice commands. Costs 215 USD.

### Resources

* [Official Website](http://theubi.com/)

## ivee (voice control)

ivee Sleek is a Wi-Fi Voice-Activated Assistant for the home that helps you manage and control your connected devices without any hands.

### Resources

* [ivee sleek](http://www.helloivee.com)
* [Kickstarter](http://www.kickstarter.com/projects/ivee/ivee-sleek-wi-fi-voice-activated-assistant)

## Ninja Blocks

Ninja Blocks is basically an Arduino compatible board packed inside a nice ninja enclosure and coupled with a bunch of external wireless sensors. You can then use their cloud-based platform to trigger events based on rules with the data collected from these sensors. Costs 199 EUR.

### Resources

* [Official Website](http://ninjablocks.com/)
* [Ninja Blocks Github](https://github.com/ninjablocks)
* [Ninja Blocks Forums](http://forums.ninjablocks.com/)
* [Ninja Blocks YouTube channel](http://www.youtube.com/user/ninjablocksinc/videos)
* [Use Dropcam with Ninja Blocks](http://dropcam.ninjablocks.com/)
* [Marcus Schappi Demos Ninja Blocks at LeWeb Paris 2012](http://www.youtube.com/watch?v=geW1rzxBp5M)
* [Ninja Blocks FAQ](http://help.ninjablocks.com/)
* [Crunchbase profile](http://www.crunchbase.com/company/ninja-blocks)

### System Overview

* Ninja Block
	* Beagle Bone
		* AM335x 720MHz ARM
		* 256MB DDR2
		* USB, Ethernet, MicroSD
		* Ubuntu 11.10
		* Dongle WiFi
	* Ninja Shield
		* Arduino
		* ATmega328@16MHz
		* 433MHz Transceiver
		* 3 RGB LEDs, 4 ports
* IP cameras
* User apps
* Ninja cloud
* Web
* Services
* Sensors
* Actuators

### Clients

* Android and iOS
* [Mac OS X](http://forums.ninjablocks.com/index.php?p=/discussion/1655/ninja-osx-client/p1)
* [Official Github client](https://github.com/ninjablocks/client)
* [Using a Raspberry Pi as a Ninja Block](http://help.ninjablocks.com/customer/portal/articles/720061-using-a-raspberry-pi-as-a-ninja-block)

### Sensors (Installation)

* Video: [Tutorial One - Unboxing and Pairing your Ninja Block](http://www.youtube.com/watch?v=nvpns0SGCkA)
	* Video: [Tutorial Two - Ninja Platform Overview](http://www.youtube.com/watch?v=o8bhYo98CIw)
	* Video: [Tutorial Three - Making all the Rules](http://www.youtube.com/watch?v=Fs17-O8nmp8)
	* Video: [Tutorial Four - Passive Infrared Sensor](http://www.youtube.com/watch?v=56HClX8EWOs)
	* Video: [Tutorial Five - Wireless Button](http://www.youtube.com/watch?v=iJajC3Y92oI)
	* Video: [Tutorial Six - Watts Clever Socket Actuator](http://www.youtube.com/watch?v=uDsgcgTBw2A)
	* Video: [Tutorial Seven - Door Sensor](http://www.youtube.com/watch?v=ot2Pislr38g)
	* Video: [Tutorial Eight - Temperature and Humidity Sensor](http://www.youtube.com/watch?v=iY8rYZJH1sg)
* Video: [Project One - Intruder Alerter](http://www.youtube.com/watch?v=LeJiDPWTcPE)
* Video: [IOTA Door & Light Automation Test with NInja Blocks and LimitlessLED](http://www.youtube.com/watch?v=N_tYeEAw15E)

### Ninja Blocks Drivers

**Modules** are now known as **Drivers**

* [Documentation](http://docs.ninja.is/module/)
	* Install them from Github
* [Dan's Light Modules](http://www.youtube.com/watch?v=O8rcMC5ayVs)
* [Installing Drivers on Your Ninja Block](http://ninjablocks.com/blogs/how-to/9555237-installing-drivers-on-your-ninja-block)
* [Wiki](http://wiki.ninjablocks.com/), e.g. compatible devices, drivers, software images

#### Interesting Ninja Blocks Drivers

* Z-Wave. Aeon Labs Z-Stick (has to be installed and enabled) + the ninja z-wave driver
	* [Z-Stick on a Mac](http://www.youtube.com/watch?v=Ee39btWYH2I), by using Indigo6
* Belkin WeMo
* Spotify
* Ninja-OpenURL
* Dropcam
* Hue

#### Z-Wave support

* Github: [ninjablocks / ninja-zwave](https://github.com/ninjablocks/ninja-zwave). Ninja Blocks driver to interface with Z-Wave devices.
* Official Ninja Blocks [fibaro support](https://github.com/ninjablocks/ninja-zwave/blob/master/lib/open-zwave/config/fibaro/fgs211.xml)
* Aeotec: [Z-Stick](http://aeotec.com/z-wave-usb-stick). The Aeotec Z-Stick Series 2 is a self-powered Z-Wave USB dongle with push button for remote network creation (independent from external power and host microprocessor). When attached to a host processor, it becomes a Z-Wave communication device, which exposes the Zensys API (SerialAPI) through integrated USB.

#### Coding

* Video: [Tutorial Nine - 'Hello Ninja' in around 60 seconds](http://www.youtube.com/watch?v=cedbZiTv0hk)
	* [Writing your first app tutorial](http://ninjablocks.com/blogs/how-to/7229758-hello-ninja-writing-your-first-ninja-app)
* Video: [helloNinja - Directors Cut](http://www.youtube.com/watch?v=m2p1rQSipXE)
* Video: [Tutorial 14 - Create and Deploy a Node App to Heroku](http://www.youtube.com/watch?v=To7kv9N2BLQ)

##### Webhooks

* NinjaBlocks allows the use of webhooks which means you can publish the results of your sensors and actions to any website or web app you may wish to configure, further expanding the possibilities.
* Video: [New Feature: Live Data Web-hooks](http://www.youtube.com/watch?v=gV7RQDzAlTs)
* Google Developers Video: [Web Hooks and the Programmable World of Tomorrow](http://www.youtube.com/watch?v=Fw8EPrIjCOc)

#### Hardware hacking

* Video: [Tutorial Ten - "EtherNinja" Connecting your Ethernet enabled Arduino to the Ninja Platform](http://www.youtube.com/watch?v=-hi9tjAnbSM)
* Video: [Tutorial Eleven - "EtherNinja" Code Explained](http://www.youtube.com/watch?v=_ByLQe4I5gQ)
* Video: [Tutorial 12 - Adding RF 433 to your Arduino](http://www.youtube.com/watch?v=MSnDrRIAEiE)
* Video: [Tutorial 13 - Unboxing and Reboxing your Ninja Block](http://www.youtube.com/watch?v=10K5Hue0ED4)
* [Tutorial 15 - Extend your Ninja Block's Wireless Range](http://www.youtube.com/watch?v=PLGyGQF4Kkc)
* [PiCrust](http://ninjablocks.com/pages/picrust)
	* [Das Raspberry Pi nimmt Ninja Blocks huckepack](http://www.golem.de/news/pi-crust-das-raspberry-pi-nimmt-ninja-blocks-huckepack-1310-102182.html)

### Ninja Cloud

* [Ninja Cloud](https://a.ninja.is/)
* [Beta Dashboard Overview](http://www.youtube.com/watch?v=1Sp8i3jHmYA)

# Connected services

* **IFTTT** If this then that – is a free service to connect and create interactions between multiple services. For example: if temperature drops below 10C, set the colour of the house light to blue (supposing you have a Philips hue bulb) . Or if a new photo is added to my Instagram, automatically back it up on my DropBox. A multitude of different channels and possibilities.
* **Sen.se** Just like IFTTT, the Sen.se can collect data from a variety of channels and trigger actions based on the processed data. They’re still in beta but apparently it’s more flexible than IFTTT, albeight more complicated to understand and get started.
* **Pushalot** The icing on the cake: Pushalot is a free app for Windows Phone which you can use to receive push notifications from any external resource. Please note that if you’re using an iPhone or Android you’ll have to find a similar app for the same purposes (I’m sure there are some).

# Other links

* [NINJA SPHERE: Next Generation Control of Your Environment](http://www.kickstarter.com/projects/ninja/ninja-sphere-next-generation-control-of-your-envir), Kickstarter project
* [Rocket Home](http://www.rockethome.de)
* RWE SmartHome
* [Fibaro Home Sensor 2](http://www.fibaro.com/de/das-system-fibaro/home-center-2)
* [Eve](http://www.kickstarter.com/projects/ciseco/eve-alpha-raspberry-pi-wireless-development-hardwa), (Kickstarter project) - based on the [IOT toolkit](http://iot-toolkit.com/)
* Rovr
* [Saphire](http://www.kickstarter.com/projects/1286098094/wirelessly-connect-all-the-things-with-sapphire), Kickstarter project (not funded)
* [Vera](http://getvera.com/)
