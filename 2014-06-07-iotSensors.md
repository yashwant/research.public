---
layout: post
title: "Internet of Things Sensors & Mapping"
slug: "research-sensors"
date: 2014-06-12 08:07
comments: true
categories: [coding]
tags: [zigbee, iot, internet of things, ble, bluetooth 4.0, ibeacon, apple]
published: true
---

# Internet of Things Sensors & Mapping

## Wireless Personal-Area Networks

Bluetooth and ZigBee have much in common. Both are types of IEEE 802.15 "wireless personal-area networks," or WPANs. Both run in the 2.4-GHz unlicensed frequency band, and both use small form factors and low power.

* Modulation technique
	* **Bluetooth:** Frequency Hopping Spread Spectrum (FHSS)
	* **ZigBee:** Direct Sequence Spread Spectrum (DSSS)
* Protocol stack size
	* **Bluetooth:** 250K bytes
	* **ZigBee:** 28K bytes
* Battery
	* **Bluetooth:** Intended for frequent recharging
	* **ZigBee:** Not rechargeable (one reason batteries will last for up to 10 years)
* Maximum network speed:
	* **Bluetooth:** 1M bit/sec
	* **ZigBee:** 250K bit/sec
* Network range:
	* **Bluetooth:** 1 or 100 meters, depending on radio class
	* **ZigBee:** Up to 70 meters
* Typical network join time
	* **Bluetooth:** 3 seconds
	* **ZigBee:** 30 milliseconds

Article:  [Bluetooth and ZigBee: Their similarities and differences](http://www.networkworld.com/newsletters/2005/0228wireless1.html)

| | NFC | Bluetooth 2.1 (EDR) | Bluetooth Low Energy | ANT+ | WiFi 802.11 b/g | WiFi 802.11n |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Standard by  | ISO/IEC | Bluetooth SIG | Bluetooth SIG | Garmin | Wi-Fi Alliance | Wi-Fi Alliance |
| Network Standard | ISO 13157 etc. | | | | | |
| Network Type | Point to Point | WPAN | WPAN | WPAN | WPAN | WPAN |


## Trilateration

* [Definition](http://en.wikipedia.org/wiki/Trilateration)
* [Dynamic localization with hybrid trilateration for mobile robots in intelligent space](http://link.springer.com/article/10.1007/s11370-007-0012-1), (with costs)
* [Indoor Localisation Using a Context-Aware Dynamic Position Tracking Model](http://www.hindawi.com/journals/ijno/2012/293048/)
* [A Beacon System for the Localization of Distributed Robotic Teams](http://www.cs.cmu.edu/~cyberscout/publications/FSR99.pdf)
* [Trilateration Localization for Multi-Robot Teams](http://homepages.ius.edu/suhettia/papers/icinco.pdf)
* [Quality of Trilateration: Confidence based Iterative Localization](http://www.cse.ust.hk/~liu/QoT.pdf)
* [Auto-localization algorithm for local positioning systems](http://www.car.upm-csic.es/lopsi/static/publicaciones/Revista%20SCI/Jorge2012Adhocnetworks.pdf)

### Nodes

Beacon Nodes are usually positioned at the ceiling or on walls.

### Mobile Nodes

A mobile node is attached to the person or object to locate.

### Positioning

In order to locate the mobile node using the trilateration method the position of the beacons must be known in advance. The determination of the beacons position is usually done manually by measuring the distance to the two closest walls of the building using measuring tapes or ultrasonic/laser rangers. This method is cumbersome and error prone, therefore different techniques have been proposed to address the problem of obtaining automatically the position of the beacons, also known as the **auto-calibration** or **auto-localization** problem.

## Google

* [Google Maps | Indoor](http://maps.google.com/help/maps/indoormaps/)
	* [A new frontier for Google Maps: mapping the indoors](http://googleblog.blogspot.de/2011/11/new-frontier-for-google-maps-mapping.html)
	* [Indoor Google Maps help you make your way through museums](http://googleblog.blogspot.de/2012/07/indoor-google-maps-help-you-make-your.html)
	* [Google I/O 2013 - The Next Frontier: Indoor Maps](http://www.youtube.com/watch?v=oLOUXNEcAJk)
* Android support since 4.3

### Remote Application Framework (similar to AirPlay)

* [Android Remote Application Framework Provides True Multi-Screen Experiences For Mobile](http://techcrunch.com/2013/09/30/android-remote-application-framework-provides-true-multi-screen-experiences-for-mobile/)

## OSM et al

* [OpenStreetmap | Indoor](http://wiki.openstreetmap.org/wiki/Indoor_Mapping)
	* [IndoorOSM](http://wiki.openstreetmap.org/wiki/IndoorOSM)
* [CloudMade Indoor Map](http://cloudmade.com/technologies/indoor-maps)
* [OpenBeacon](http://www.openbeacon.org/)
	* [Sputnik](https://vimeo.com/1170680#), CCC Congress, 24C3 indoor mapping project

# Bluetooth 4.0

## Bluetooth SMART

* Bluetooth Smart Ready indicates a dual-mode device,typically a laptop or smartphone, whose hardware is compatible with both Classic and LE Bluetooth peripherals.
* Bluetooth Smart indicates an LE-only device, typically a battery-operated sensor, which requires either a SMART Ready or another SMART device in order to function.


## Bluetooth low energy (BLE, Bluetooth LE)

* [Wikipedia definition](http://de.wikipedia.org/wiki/Bluetooth_Low_Energy)

## Apple support for BLE in Bluetooth 4.0

In mid 2011, Apple joined the board of directors of the Bluetooth Special Interest Group, which also includes Intel, Microsoft, Motorola, Nokia, Toshiba and Lenovo. 

Apple also added support for dual mode Bluetooth 4.0 in its mid-2011 MacBook Air and Mac mini, and subsequently added support to the iPhone 4S, making it the first Bluetooth 4.0 compliant smartphone. 

Subsequent 2012 iOS devices, including the "New" iPad 3, iPhone 5 and the late 2012 iPad 4 and iPad mini also support Bluetooth 4.0. Apple also added Bluetooth 4.0 support to the mid-2012 MacBook Pros and the late-2012 iMac. Earlier Macs can add Bluetooth 4.0 support via a third party USB dongle.

Microsoft has not yet added general support for Bluetooth 4.0 and BLE in Windows 8 or Windows Phone 8. Microsoft has added custom support for BLE to the Surface Pro, but not its Surface RT. Nokia's newest Lumia WP8 phones include BLE hardware, as do new Blackberry Z10 and Q10 models and recent higher-end models of HTC and Samsung smartphones.

According to WWDC 2013

> You can buy this third party program, program them to emit whatever Bluetooth signal but also, your iOS devices can be beacons.

> So your iPads, your iPhones with the new iOS 7 SDK, Public SDK, you can program them to emit whatever signal you want and you can do that dynamically and programatically and vary depending on what's happening.

> So, imagine at the museum, the painting or the statue has a sign like an iPad is the sign, like a smart sign, like we have in our retail stores maybe, and you could tell the information about the painting but if it's crowded, it's still emitting Bluetooth LE in on your app, we can detect that and show them whatever UI.

### iOS 7

**iBeacons** is a new feature of iOS7 that allows mobile devices to be accurately located inside buildings.

This opens up the possibility of creating a new generation of location-based learning content.

In practice, this means that when a user is near a "beacon" content can be "pushed" to their iPhone or iPad.  
Because "beacons" are small, low cost and low power devices it is now possible to trigger "learning events" anywhere in your workplace.

### Why did Apple go with iBeacon and not NFC
There are a few reasons why it makes sense for Apple to go with iBeacon and not NFC. The first is that range and affordability.

In a detailed piece Hari Gottipati, writing for GigaOm, has outline just how important this is: “The average area occupied by a Macy’s store is 175,000 square feet, which is 16,258 square meters. iBeacon’s range is 50 meters (typical Bluetooth range), or 2,500 square meters. So a typical Macy’s store would need 7 iBeacons. If Macy’s wanted to add NFC tags (each at 10 cents) to all its products to send information to phones, it would cost $1,000 for 10,000 products, $10,000 for 100,000 products and $100,000 for 1 million products. NFC may not be needed on all products, but this will give a rough idea on how much it could cost.”

### AirDrop does the file transfer

There’s also the fact that Apple doesn’t really need, or perhaps, want NFC. It has AirPlay and Airdrop to handle the transfer of files, music and video clips. And NFC comes pre-loading with assumptions that Apple may not be able to fulfill, such as mobile payments. iBeacon is a new technology that offers a blank slate for Apple to make of it what it will in association with shopkeepers.

And NFC is used by Google. And Google vs Apple is still very much a thing to consider. This is also  the downside of iBeacons compared to NFC. Because it only works with Apple devices, shopkeepers have to pay to target iPhones and not Android phones. We’re pretty sure shopkeepers want a marketing system with universal support; a payment system without universal support is simply out of the question.

### The Promise Of QR Codes Just Without The QR Code

The premise for the modern, non industrial QR Code is to form a link between the real world and the Internet world.  The QR code is actually far more popular then most come to understand.  It even forms the basis of the most successful mobile wallet in the US, the Starbucks App.

The reason Starbucks has had this success with QR codes is because they use the technology in reverse.  That being they control the imager and the customer displays the QR code on their device.  This is in stark contrast to the way most startups and legacy companies have used this technology.  That being the consumer controls the imager, a built-in camera and the QR code is usually a static printed image.  The user’s phone must have many things in place for this to be a successful interaction.  And iOS devices require a separate general purpose app to decode the QR code and hopefully act on the requirements and purpose of the QR code correctly.

### Testing

* [Virtual iBeacon](http://developer.radiusnetworks.com/ibeacon/). Use Virtual Box to turn your computer into a fully functional iBeacon device.

### Articles

* [Can an iOS7 device act as an iBeacon?](http://stackoverflow.com/questions/19274286/can-an-ios7-device-act-as-an-ibeacon)
* [Turn Macbook into iBeacon](http://stackoverflow.com/questions/19410398/turn-macbook-into-ibeacon/19741615#19741615)
* [Mavericks as an iBeacon](http://www.blendedcocoa.com/blog/2013/11/02/mavericks-as-an-ibeacon/)
* [Apple's home automation tech taps iPhone, Mac hardware for intelligent user tracking](http://appleinsider.com/articles/13/11/05/apples-home-automation-tech-taps-iphone-mac-hardware-for-intelligent-user-tracking)

## Features

* Region monitor
* Ranging and micro-locations
* Awake your app by push notifications
* In app notification when user the customized region
* Third-party Bluetooth LE (Low Energy) or iOS device can be iBeacons
* One beacon ID can cover multiple locations
* Accuracy and range awareness

## Usage scenario

* **Proximity marketing.** Large scale retail outlets can invest in Beacon devices with their app store offering. SuperDry, for example, could place Beacon Devices around its store and shoppers could use the SuperDry app to gain information as they shop.
* **Micro Location-based notification.** A store can transmit information direct to an iPhone device as the user walks around. Whether this requires a compatible app to be installed, or can work with Notification Centre remains to be seen. But essentially a Beacon can transmit customized coupons to a customer as they walk around a store.
* **Customised marketing.** Essentially iBeacon can transmit customized coupons (designed specifically for you) when you enter a certain region. Perhaps if you’ve been to look at an item a number of times it could offer a discount to convince you.
* **Specific directions.** Because Beacons provide micro location support they can be used to direct customers to specific items. This could actually be tremendously useful in large department stores, where iBeacon technology could provide the ability to search for an item using a store app, and find directions to that item in the store.
* **Indoor mapping.** Because Beacons can provide micro location information indoors they can be used to dramatically improve indoor mapping. For US department stores and malls this is a much larger issue than we imagine here in the UK, accurate indoor mapping is very much on the agenda.
* **Contactless payment.** This is the big one. Beacons and iBeacon enable contactless payment systems to be developed. Although it’s worth noting that there isn’t this system set-up already, and as far as we know there isn’t one planned. Even so, iBeacons ability to track a specific phone, linked to an Apple ID and user account opens the door for an Apple-based payment system. This in itself opens up a whole raft of questions: would Apple want its traditional 30 per cent (way too high compared to Visa or MasterCard); how secure would it be; what kind of service would Apple offer. And would shopkeepers be interested? These are the kind of questions that are wholly speculative in nature. What’s important is that we can see here Apple laying the groundwork.
* **Give apps & services more context** - Beacons could be used to give our apps and services more context, so they can adapt to our surroundings. Imagine, for example, that you manage both a personal and a work Twitter account. You could set up a beacon at work that would automatically log you into your work Twitter account when you’re nearby. As soon as you’re out of range, you’re automatically switched into your personal account.
* **Home automation** - BLE is ideal for home automation, especially because most of us now carry our phones around with us most of the time. Because BLE knows how far you are away from beacons, triggers can be set to only go off when you’re a certain distance away. This is ideal for things like lighting and electronics. BLE can also be used to trigger warnings when you try to do things like leave the house while your oven is on.
* **Never lose anything again (apart from your phone)** - Beacons don’t have to be attached to static objects. You can add beacons to your keys, bags, laptops, tablets, or anything else you wouldn’t want to lose. They do cost a reasonable amount (about $20 for this type of tag), but could end up saving you more. You could get a warning when your tagged item is more than a certain distance from you, then get directions to where it is. This is ideal for when your keys are somewhere in the house, but nowhere to be seen.
* **Extra security for your car** - You could add a beacon to your car to stop it from starting unless it’s you who’s driving. For a less extreme approach, you could set your beacon up so that anytime the car is driven and you’re not near it, you get notified. That way, you can still drive it when you forget your phone, but you know if someone else is driving it while you’re not around.
* **Smarter notifications** - Push notifications are nearly as annoying as emails. Beacons could solve that issue by making them smarter. You could set up a “notification free zone” or areas where you only receive certain types of messages.

### Brands

* **PayPal** [Introducing PayPal Beacon: Shopping made seamless](http://www.youtube.com/watch?v=P0QCRRsuqAo)
* [PayPal Beacon](https://www.paypal.com/webapps/mpp/beacon)

## Products

### iBeacons

* [Aeotec](http://aeotec.com/homeautomation)
* [Geofency](http://www.geofency.com/)

#### Geohopper

* [Geohopper](http://geohopper.com/)
* Geohopper & IFTTT: [Geohopper turns the lights on and off](https://vimeo.com/60788399)
* **Inofficial** [Geohopper blog](http://blog.twocanoes.com/)
* IFTTT: [Geohopper turns the lights on and off](https://vimeo.com/60788399)
* IFTTT: [Geohopper Office Departure Notification](https://vimeo.com/62390656)
* IFTTT: [Geohopper goes to the coffee shop](https://vimeo.com/60788707)	* [Blog entry on Bleu station](http://dev.vunet.us/index.php/iphone-development/twocanoes-releases-bleu-station-for-ibeacon-and-new-ibeacon-aware-apps/)
* [Beacon Finder](http://beaconfinder.com/)
* [Bleu Setup](https://itunes.apple.com/us/app/bleu-setup/id723028950), iPhone App
* [hrshukla / gh-nb-webhook](https://github.com/hrshukla/gh-nb-webhook). A webservice for GeoHopper to track "home" state and actuate Ninja Blocks webhooks.
* [Geohopper actions](http://geohopper.com/actions)

##### IFTTT

* [Log all of my departures from work in Google Drive](https://ifttt.com/recipes/127196)
* [Greet me with awesome music, when I arrive.](https://ifttt.com/recipes/133265)
* [Turn off my lights when I leave home.](https://ifttt.com/recipes/133332)
* [If you exit an area, then turn off All Switches](https://ifttt.com/recipes/133318)
* [Full House me! (spoken word edition)](https://ifttt.com/recipes/133029)
* [When I hit the gym, log it in Google Drive.](https://ifttt.com/recipes/133209)
* [Arrive home > Turn on Hue lights](https://ifttt.com/recipes/133323)
* [When you get home, turn on the holiday lights.](https://ifttt.com/recipes/133036)
* [Make a grand entrance with Philips Hue + IFTTT](https://ifttt.com/recipes/127496)
* [Log all of my arrivals at work in Google Drive](https://ifttt.com/recipes/127194)

#### Tools (Sniffer)

* [Particle Detector](https://itunes.apple.com/ca/app/particle-detector/id724226138?mt=8)
* [LightBlue - Bluetooth Low Energy](https://itunes.apple.com/nl/app/lightblue-bluetooth-low-energy/id557428110?l=en&mt=8)
* [BLExplr](https://itunes.apple.com/nl/app/blexplr/id524018027?l=en&mt=8)

#### B2C

* [iBeacons: Apple TV mit iOS 7 einrichten](http://www.mactechnews.de/news/article/iBeacons-Apple-TV-mit-iOS-7-einrichten-156789.html)
* [Sensor Tag](http://www.ti.com/ww/de/wireless_connectivity/sensortag/index.shtml?INTC=SensorTag&HQS=sensortag&DCMP=PPC_Google_TI&k_clickid=144867df-25de-df48-732c-00001a9ccc35&247SEM=) by Texas Instruments
	* Hardware device that is both transmitter and receiver of data
	* Comes with BLE chip, transmitter, battery and sensors of your choice (Temperature, humidity, pressure, accelerometer, gyroscope, magnetometer, etc)
	* Batterytime up to one year
	* Supersmall technology
	* Triggs smartphones and mobile devices to communicate with it, when in range
	* Cheap, getting cheaper
	* Time to market or at least – RND.
* [FOBO tag](http://www.my-fobo.com/product_bluefobo_front.html)
* [iBitz](http://ibitz.com/) PowerKey and Unity activity trackers by GeoPalz are physical activity based wireless devices that connect to apps that unlock games and track fitness data.
* [Oakley Airwave](http://de.oakley.com/airwave)

#### B2B

* [Adomaly](https://adomaly.com/), 1st Mobile Ad Network to Reach Consumers In-Store @ Shelf
* [aisle 411](http://aisle411.com/)
	* [Indoor Map Apps On the Rise as Aisle411 Raises $6.3M](http://blogs.wsj.com/venturecapital/2013/09/04/indoor-map-apps-on-the-rise-as-aisle411-raises-6-3m/)
	* [Aisle411 Overview plus Estimote](http://www.youtube.com/watch?v=o4wPr-daFZE)
* [beaconmaker](http://www.beaconmaker.com/)
* [Estimote Beacons](http://estimote.com/)
	* [Playing With iBeacon and Estimote in iOS 7](http://joris.kluivers.nl/blog/2013/09/27/playing-with-ibeacon/)
	* [Estimote Wins Best Hardware Startup At TechCrunch Disrupt SF](http://techcrunch.com/2013/09/11/estimote-wins-best-hardware-startup-at-techcrunch-disrupt-sf/)
	* [Y Combinator company, Estimote, shows why Low Energy Bluetooth](http://www.youtube.com/watch?v=VfJch1XpCOw)
	* **Video** [Estimote Bluetooth Smart Beacon - iBeacon-compatible](http://www.youtube.com/watch?v=sUIqfjpInxY)
	* [Locating users inside a room with iBeacons](http://www.youtube.com/watch?v=dMWEl6GBGqk)
* [Roximity Beacon](http://buyibeacons.com/)
* [kontakto.io](http://kontakt.io/)
* [bytelight](http://www.bytelight.com/)

#### Wireless key locators

* [Overview](http://postscapes.com/wireless-key-locators)
* [ElGato Smart Key](http://www.elgato.com/de/smart/smart-key)
* [Kensington proximo](http://www.kensington.com/kensington/de/de/p/2818/K39565EU/proximo%E2%84%A2-start-set.aspx)
* [hipkey](http://www.hippih.com/hipkey)
* [Hone](http://gethone.com/)
* [tile](http://www.thetileapp.com)
* [StickNFind](https://www.sticknfind.com/)
* [chippolo](http://www.kickstarter.com/projects/1015015457/chipolo-bluetooth-item-finder-for-iphone-and-andro)

### Bluetooth Smart (Bluetooth LE)

* [KS-800-scale from Beurer](http://www.beurer.com/web/de/produkte/gewicht/kuechenwaagen.php?pid=8091)

### Bluetooth 3.0

* [PWS - PACKABLE WIRELESS SYSTEM](http://grainaudio.com/collections/grain-audio-products/products/pws)

### Bluetooth 2.1

* [Tivoli](http://tivoliaudio.de/products/bluetooth.html/)

## Raspberry Pi

* [KST productions](http://www.kstechnologies.com/collections/all)
* [Redbear Lab](http://redbearlab.com/ibeacon/), Shield
* [coin](http://blog.onlycoin.com/posts/2013/10/3/coin-arduino-ble-dev-kit)
* [Turn a Raspberry Pi into an iBeacon](http://www.ioncannon.net/programming/1603/turn-a-raspberry-pi-into-an-ibeacon/)

## Articles

* [MLB demos using Apple’s iBeacon technology to deliver personalised, interactive stadium experiences](http://9to5mac.com/2013/09/27/mlb-demos-using-apples-ibeacon-technology-to-deliver-personalised-interactive-stadium-experiences/)
* [Apple's home automation tech taps iPhone, Mac hardware for intelligent user tracking](http://appleinsider.com/articles/13/11/05/apples-home-automation-tech-taps-iphone-mac-hardware-for-intelligent-user-tracking)
* [Apple iWatch is actually a home automation play, not a smartphone companion (analyst)](http://venturebeat.com/2013/10/10/apple-iwatch-is-actually-a-home-automation-play-not-a-smartphone-companion-analyst/)
* **reddit discussion:** [Will iBeacons become Apple's biggest disruptive innovation EVER? The potential is there.](http://www.reddit.com/r/apple/comments/1mjzba/will_ibeacons_become_apples_biggest_disruptive/)

## Slides

* [iBeacons - five learning concepts](http://de.slideshare.net/LearnerLab/i-beacons-five-learning-concepts)
	* Just in time learning
	* Targeted learning on-demand
	* Dynamic content-updates
	* Find real-world assistance
	* Location-based reminders
* [Bluetooth Low Energy Unveiled](http://de.slideshare.net/ggindele/btle-unveiled-01)

# Wi-Fi Direct

* [Wikipedia definition](http://en.wikipedia.org/wiki/Wi-Fi_Direct)

Apple’s forthcoming AirDrop in its iOS 7 mobile operating system will employ Wi-Fi Direct to be able to share files between two devices anywhere. Google’s Android operating system has had Wi-Fi Direct support since version 4.0 Ice Cream Sandwich and has enabled various functions that users may be familiar with from Samsung Galaxy smartphone commercials (such as sharing pictures with your friends or the gimmicky All Share feature).

* Apple, AirDrop
	* AirDrop from Activity Sheet (iOS 7) - Apps will be able to incorporate AirDrop support, giving users the ability to share photos, documents and more with friends from within an app. 
* Chromecast by Google, Standard Wi-Fi
* Miracast, Mirrorlink
* Samsung, S Beam & All Share

# Airplay

* [Raspberry Pi Hack Turns The Ultra-Affordable Computer Into An AirPlay Receiver](http://techcrunch.com/2012/12/28/raspberry-pi-hack-turns-the-ultra-affordable-computer-into-an-airplay-receiver/)

# Zigbee

* [Device Positioning Using Smart Zigbee Beacons](http://www.simondobson.org/softcopy/nap-zigbee-open-day-20080124.pdf)
* [ZigBee wants to be the Bluetooth of the internet of things. Too bad everyone hates it.](http://gigaom.com/2013/08/30/zigbee-wants-to-be-the-bluetooth-of-the-internet-of-things-too-bad-everyone-hates-it/)

## Companies

* [Green Peak](http://www.greenpeak.com/)

## Products

* [Almond Router](http://www.securifi.com/almondplus)
* [Revolv](http://revolv.com/)
* [Philips Hue Connected Lamp BR30](http://www.zigbee.org/DesktopModules/ZigbeeDisplayCategoryProducts/ProductDetails.aspx?ProductID=818&Ctrl=ViewProducts)

### Sensors

* [Iris Indoor Door and Window Sensor](http://www.youtube.com/watch?v=LV3lRWkeP78) by Lowe
* [NYCE control Door / Window Sensor](http://nycecontrol.com/products/ncz3011c4/)

# Z-wave

Z-Wave is a wireless communications protocol designed for home automation, specifically to remotely control applications in residential and light commercial environments. The technology uses a low-power RF radio embedded or retrofitted into home electronics devices and systems, such as lighting, residential access control, entertainment systems and household appliances.

Z-Wave requires a master controller and a Z-Wave device. The most useful type of master controller is a USB stick, as it will allow you to control your devices using your smart phone or computer.

A Z-Wave device can be a light switch, a light dimmer, an outlet -- for controlling things like TV's, DVD's and plugin-lamps -- a motion sensor, a thermostat, or even a deadbolt lock.

## Setup

1. Install [Firmware Driver for Z-Stick](http://aeotec.com/partner/z-wave-firmware/viewcategory/9-firmware-update-driver)
2. [Home Automation (UK) - Z-Wave Aeon Labs Z Stick Series 2 - Unboxing and set-up](http://www.youtube.com/watch?v=Ee39btWYH2I)
3. [How to set-up the Fibaro Door Sensor with Indigo on your Mac](http://www.youtube.com/watch?v=P8UeKUjPjQ4)
4. Pair. [Hardware Manual for the Z-Stick](http://www.fibaro.com/files/instrukcje/eng/DoorWindowSensor%20FGK-101-107%20ENG_v21-v23.pdf), [Pairing Manual](http://aeotec.com/z-wave-usb-stick/913-z-stick-manual-instructions.html)

## Products

### Control

* [Aeotec Z-stick](http://aeotec.com/z-wave-usb-stick)
* [Z-troller](http://aeotec.com/z-wave-usb-stick)
* [Z-Stick driver for OS X](http://aeotec.com/partner/z-wave-firmware/viewcategory/9-firmware-update-driver)

# 433MHz

* [Protocol](http://www.fhemwiki.de/wiki/RFXtrx)
* [RFXtrx433 USB 433.92 MHz Transceiver (RFXCOM)](http://www.hans-hats.de/rfxtrx433-43392-transceiver-rfxcom-p-7242.html)
* [RFXCOM Indigo Plugin](http://www.perceptiveautomation.com/userforum/viewforum.php?f=28)

## Products

* [HomeEasy](http://www.homeeasy.eu/)
* [Chacon](http://www.chacon.be/)
* [LightwaveRF](http://www.lightwaverf.com/)
* [ByeByeStandBy](http://www.byebyestandby.com/)
* X10 RF transmission
* [KlikAanKlikUit](http://www.klikaanklikuit.nl/home/)
* [COCO](http://coco-technology.com/)
* [Düwi](http://www.duewi.de/) (their proprietary devices)
* [ebode](http://www.ebodeelectronics.eu/index.php?option=com_content&view=article&id=6&Itemid=7&lang=en)
* [ELRO](http://www.elro.eu/) (AB400, AB600)
* [Intertechno](http://www.intertechno.at/)
* [NEXA](http://www.nexa.se/)

### Software (Mac)

#### Indigo

* [indigo](http://www.perceptiveautomation.com/indigo/index.html)
* [indigo plugins](http://www.perceptiveautomation.com/wiki/doku.php?id=plugins:wish_list)
* [Official Indigo Wiki](http://www.perceptiveautomation.com/wiki/doku.php)
* [Official Indigo Forum](http://www.perceptiveautomation.com/userforum/)
* [Indigo Touch](http://www.perceptiveautomation.com/indigo/touch.html)
* [Built-in Home Automation Hardware Support](http://www.perceptiveautomation.com/devices/)
* [Common Home Automation Tasks](http://www.perceptiveautomation.com/wiki/doku.php?id=common_ha_tasks)
* [How to set-up the Fibaro Door Sensor with Indigo on your Mac](http://www.youtube.com/watch?v=P8UeKUjPjQ4)
* [User Contribution Library](http://www.perceptiveautomation.com/filelib/index.php)
* Indigo Forums: [Indigo & Z-Wave](http://www.perceptiveautomation.com/userforum/viewforum.php?f=58)
* **Video:** [Part 1: Mac Home Automation Ingido Software In Detail](http://www.youtube.com/watch?annotation_id=annotation_1695135499&feature=iv&src_vid=gY5_Xe2x_SY&v=33rR6SlZN6I)
* **Video:** [Part 2: Mac Home Automation Ingido Software In Detail](http://www.youtube.com/watch?annotation_id=annotation_3966266895&feature=iv&src_vid=33rR6SlZN6I&v=gY5_Xe2x_SY)

##### Plugins

* [Netatmo](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=22&t=9948)
* [Google Voice SMS Plugin](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=65&t=7438)
	* [Github](https://github.com/IndigoDomotics/google-voice-sms)
	* **Attention** I could not manage to find out my (German) SMS number. Though the plugin needs a 10-digit number (more digits are not allowed). Therefore I expect it to be US only?
* [Roomba](http://www.perceptiveautomation.com/userforum/viewtopic.php?p=71477#p71477)
	* [Pictures](https://www.dropbox.com/sh/3dz6mbrwyw9nlyu/HqSKh_b_YY#/)
	* Video: [Roomba 500 + RooWifi + Home Automation System - Dock Action](http://www.youtube.com/watch?v=UNcNb3zHb6U)
	* [RooWIFI](http://www.roomba-wifi-remote.com/)
	* [Roomba Wifi Remote YouTube channel](http://www.youtube.com/channel/UCqqFfy31jJd7Hy5HDp2FWbA?feature=watch)
	* [RooWIFI&Indigo&plugin (PDF)](https://www.dropbox.com/s/9ghepfwbxdaw0o1/RooWIFI%20Indigo%20plugin.pdf)
* [Indigo for Plex](http://wiki.plexapp.com/index.php/Indigo_for_Plex). Control your system through Plex.
	* [Mac Home Automation on your TV with Indigo and Plex](http://www.automatedhome.co.uk/reviews/mac-home-automation-on-your-tv-with-indigo-and-plex.html)
* [SQL Logger Plugin](http://www.perceptiveautomation.com/wiki/doku.php?id=plugins:sql_logger)
	* PostgreSQL for Mac: [Postgres.app](http://postgresapp.com/)
		* [Documentation](http://postgresapp.com/documentation)
		* [How to Install PostgreSQL on a Mac With Homebrew and Lunchy](http://www.moncefbelyamani.com/how-to-install-postgresql-on-a-mac-with-homebrew-and-lunchy/)
		* GUI: [induction](http://inductionapp.com/)
		* GUI: [PG Commander](https://eggerapps.at/pgcommander/)
		* GUI: [pgAdmin](http://www.pgadmin.org/)
	* SQLite
		* GUI: [Liya](https://itunes.apple.com/dk/app/liya/id455484422?mt=12) (free)
		* GUI: [Base 2](http://menial.co.uk/base/)
		* GUI: [SQLite Professional](http://www.sqlitepro.com/)
		* GUI: [RazorSQL](http://razorsql.com/screen_shots.html)
		* [Overview of GUIs](http://www.barefeetware.com/sqlite/compare/?mlp)
		* [SQLite, shell script, CSV, google Spreadsheet, Ducksboard](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=9&t=10611)
* SiriProxy
	* [siriproxy-violet](https://github.com/msreynolds/siriproxy-violet). A plugin for SiriProxy that allows you to control your Indigo home automation server with Siri on your iOS devices.
	* [more Siri Proxy Home automation plugins](https://github.com/plamoni/SiriProxy/wiki/Plugins)
* [Airfoil - official website](http://rogueamoeba.com/airfoil/mac/)
	* [Airfoil plugin](http://www.perceptiveautomation.com/wiki/doku.php?id=plugins:airfoil)
* [Aircontrol plugin](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=11&t=11225)
	* [Github](https://github.com/IndigoDomotics/aircontrol). Use Indigo to control your jailbroken AppleTV with FireCore's AirControl extension in AppleTVFlash.
	* [ATV flash](http://firecore.com/atvflash-black)
	* [ATV Aircontrol](http://support.firecore.com/entries/21375902-3rd-Party-Control-API-AirControl-beta-)
	* DACP as used by Apple is encrypted now with RSA keys and unlikely to be cracked in the near future.
	* iTunes can handle unencrypted requests (legacy I guess) though I couldn't get the functionality to work well in this way
	* Firecore have recently (02 May 2012) released Air Control (Beta) that offers complete network control to Apple TV's 
	* Apple TV's have to be jail broken - which currently means ATV2's only (which explains why they cost more on eBay than a a new one from Apple).
	* You have to install Firecore's aTV Flash ($29.95). (and then Air Control (Beta)) which is a pretty good functional addition.
	* Then Perry the Cynic's wonderful plugin Cynical Network and use it to control the devices.
	* Air Control can retrieve a raft of information about what's playing.
* [iCal Alarm Processor](http://www.perceptiveautomation.com/wiki/doku.php?id=plugins:icalalarmprocessor)
* [Pushover Plugin](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=70&t=11207)
* [Backing up or Uninstalling Your Indigo Configuration](http://www.schollnick.net/wordpress/home-automation/backing-up-your-indigo-configuration/)
* [Indigo Survey Plugin](http://www.schollnick.net/wordpress/home-automation/indigo-v5-plugins/indigo-survey-plugin/)
* [Timers and Pesters](http://www.perceptiveautomation.com/wiki/doku.php?id=plugins:timersandpesters)
* Tracking
	* **NOT WORKING WITH TIME CAPSULE ANYMORE** [Smartphone Radar - Information and Installation](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=55&t=10281)
		* [Apple Forums: SNMP + TimeCapsule remove](https://discussions.apple.com/thread/5101886?start=15&tstart=0)
	* [Find my iDevice (latest)](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=33&t=8804)
		* [Find my iDevice Manual](http://www.schollnick.net/wordpress/home-automation/indigo-v5-plugins/find-my-idevice-for-indigo-v5/)
* openURL Schemes
	* openURL schemes are used to link to/open an app on your device, and you can use them on your Indigo control pages by selecting "Link To External URL" and typing in the openURL for the app you want.
	* [Indigo forums](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=13&t=11079)
	* [Database on openURL schemes](http://handleopenurl.com/scheme?page=25)
* Caller ID
	* [Amego](http://www.sustworks.com/pa_guide/index.html)
	* [Caller ID](http://www.callerid.com/)
	* [Phone Amego - auto dialer with sms software functionality and caller id lookup](http://www.youtube.com/watch?v=hc4Xwhr1K48)
	* [Record Phone Calls From Your iPhone or Android Smartphone to your Mac Through Bluetooth Tutorial](http://www.youtube.com/watch?v=57PpFE_penA)

##### Scripts

* Twitter
	* IFFFT: [Email to Twitter](https://ifttt.com/recipes/4288) recipe
* Pushover
	* [Github](http://updates.pushover.net/post/20021501163/new-pushover-app-plugins-for-github-weechat-and)
	* [Pushover action for Growl](http://jedda.me/projects/pushover-action-growl/)
* Variables
	* [Variables for Growl Plugin](http://www.perceptiveautomation.com/wiki/doku.php?id=plugins:growl_1)
	* [Variable Substitution](http://www.perceptiveautomation.com/wiki/doku.php?id=plugins:variable_substitution)
* [Apple script to send temperature (or others) to pachube.com](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=11&t=5347&hilit=csv)
	* [Using Pachube with Insteon/Indigo software](http://www.dial911anddie.com/weblog/2009/12/using-pachube-with-insteonindigo-software/)
* [IndigoPebble](https://github.com/bnazari/IndigoPebble). Indigo control with HTTPebble.
* [IndigoWidget](https://github.com/ajturner/IndigoWidget). Mac OS X Dashboard Widget for controlling home automation system with Perception Automation Indigo.
* [indigo-client](https://github.com/discgolfer1138/indigo-client). simple node client for Indigo home automation server.
* [Alfred-Indigo-Workflow](https://github.com/mlamoure/Alfred-Indigo-Workflow)
* Twilio
	* [Using Siri with Twilio For Home Automation](https://www.twilio.com/blog/2011/10/guest-post-using-siri-with-twilio-for-home-automation.html)
	* [Voice Controlled Garage Door](http://rumsey.org/blog/2011/11/voice-controlled-garage-door/)
	* [Feature Request - Make a Phone Call](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=3&t=7954&hilit=twilio)

##### Control pages

**Ratios**

* iPhone Portrait Retina, 640x832
* iPhone Landscape Retina, 960x536
* iPad Portrait Retina, 1408x1760
* iPad Landscape Retina, 2048x1408

**Flat UIs**

* [20+ Free Flat User Interface Templates and Designs](http://designrshub.com/2013/04/free-flat-user-interface-templates.html)
* [Flat UI Kit (free download!)](http://www.webdesignerdepot.com/2013/05/flat-ui-kit-free-download/)
* [Psd Flat UI Kit Template Vol1](http://www.pixeden.com/psd-web-elements/psd-flat-ui-kit-template-vol1)
* [Pinterest example](http://www.pinterest.com/pin/309622543102081827/)
* [Pinterest example](http://www.pinterest.com/pin/10414642860883899/)
	* [Samsung Smart Home on Behance](http://www.behance.net/gallery/Samsung-Smart-Home-App-Concept/8532441)
* [Very nice Pinterest example from Heima](http://www.pinterest.com/pin/212513676139571632/)
	* [Heima on Behance + Video](http://www.behance.net/gallery/HEIMA-Smart-Home-Automation-UI/9080423)
* [Home Automation Examples from FastCo](http://www.fastcodesign.com/1671048/the-home-automation-panel-thats-as-good-as-art#1)
* [Pearl Mobile App on Behance](http://www.behance.net/gallery/PEARL-Mobile-APP-GUI/8303691)
* [not so special interface on Behance](http://www.behance.net/gallery/Smart-Home-App/2983913)

**Prism**

* [Indigo Prism Reflectors](http://www.perceptiveautomation.com/wiki/doku.php?id=reflector:about)
* [prism official website](http://goprism.com/)

**Tutorials**

* [Using Control Pages](http://www.perceptiveautomation.com/indigo/help/html/01850_controlPages.html)
* [Control pages](http://www.perceptiveautomation.com/wiki/doku.php?id=indigo_5_documentation:overview#control_pages_pro_only)
* [Custom Images on Control Pages](http://www.perceptiveautomation.com/wiki/doku.php?id=cp_custom_images)
* Forum: [Post Pics of Your Control Pages HERE!](http://www.perceptiveautomation.com/userforum/viewtopic.php?f=3&t=1506&start=105)

##### Hacks

* [Direction. Walking up the sidewalk toward the house, or away from it?](http://www.perceptiveautomation.com/indigo/hacks/traffic_direction.html)
* Infrared
	* [iRTrans](http://www.irtrans.de/en/)
		* [iRed2](http://www.tinbert.com/iRed2/). iRed itself can be controlled from commandline, by TCP sockets and by AppleScript.
	* **BEST SOLUTION** [Global Cache](http://www.globalcache.com/)
		* [Global Cache IP2IR](http://www.globalcache.com/products/itach/ip2irspecs/)
		* [Global Cache plugin](https://github.com/IndigoDomotics/global-cache)
		* Better plugin: [Cynical Cache plugin](http://www.cynic.org/indigo/plugins/online/gcnet.html)
		* [iRed2](http://www.tinbert.com/iRed2/). iRed itself can be controlled from commandline, by TCP sockets and by AppleScript.
	* [Iguanworks USB IR Transceiver](http://iguanaworks.net/products/usb-ir-transceiver/)
		* [IRControl](https://www.macupdate.com/app/mac/31369/ircontrol)
	* Article: [Hide Your Components By Using Remote Control Extenders](http://www.apartmenttherapy.com/remote-control-extenders-for-a-140052)

#### Other

* [XTension](http://www.machomeautomation.com/doku.php/index)

### Sensors

* [GE 45601 Z-Wave® LED Handheld Remote](http://www.amazon.com/dp/B0013V58CU/ref=sr_1_2?ie=UTF8&qid=1366153413&sr=8-2)
* [GE 45600 Z-Wave Basic Handheld Remote](http://www.amazon.com/dp/B0013V6RW0/ref=sr_1_1?ie=UTF8&qid=1366153413&sr=8-1)
* [Fibaro Wall Plug 2500 Watt](https://www.google.de/shopping/product/2878010600144358385?q=fibaro&es_sm=91&biw=1280&bih=705&sa=X&ei=qXiLUrPyKMrGtAae5YCADg&ved=0CGQQ8wIwAg)
	* [Product video](http://www.youtube.com/watch?v=hl1O6_fKuik&list=UURTX4A0btp062eRjcqmoEdg)
* Fibaro Dimmer
	* [Product video](http://www.youtube.com/watch?v=xpuBE2GQVvs&list=UURTX4A0btp062eRjcqmoEdg)
* [Fibaro Door Window Sensor](http://www.fibaro.com/de/das-system-fibaro/door-window-sensor)
* [Philio - Z-Wave 4 in 1 Sensor (Tür, Bewegung, Helligkeit, Temperatur)](http://store.zwaveeurope.com/product_info.php?products_id=12452)
* [Fibaro Flood Sensor](http://www.fibaro.com/de/the-fibaro-system/flood-sensor)
	* [Product video](http://www.youtube.com/watch?v=8JRxUoHbEN8&feature=c4-overview&list=UURTX4A0btp062eRjcqmoEdg)
* [Everspring: Control Sensors](http://www.everspring.com/ControlSensors.aspx)
* [Everspring: Smart Lightning](http://www.everspring.com/SmartLighting.aspx)
* [Home Automation](http://www.everspring.com/HomeAutomation.aspx)
* [Security System](http://www.everspring.com/SecuritySystem.aspx)
* [NortQ](http://northq.com/category/z-wave/) e.g. power consumption
	* [Homemanager.tv](homemanager.tv). NorthQ has developed a portal where users can observe their consumption status and manager their budget. By creating a free account on the portal you can also set and receive alarms, control devices and take advantage of all the features and services that NorthQ products can offer.
* [Aeotec](http://aeotec.com/homeautomation) e.g. door/window sensor, garage controller, home energy meter, key fob, led bulb, remote, multisensor, panic button, range extender, siren & doorbell, smart strip, smart switches, touch panels, water sensor, z-stick

### Shops

* [Z-Wave24.com](http://www.z-wave24.com/)
* [z-wave shopping](http://www.zwave-shopping.com/de/)
* [z-wave yeah](http://www.zwave-yeah.com/de/)
* [zwave4u](http://www.zwave4u.com/)

## Other

### Insteon
INSTEON is a protocol developed by SmartLabs, parent company of Smarthome.com, which is widely used in North America and is moving into other markets as well. There are a few 3rd party vendors that make INSTEON hardware but most devices are made by SmartLabs. INSTEON is a combination RF and power line-based protocol. It is also said to support communicating over USB and Ethernet connections, and it can be intermixed with X10 devices for backward compability.

#### Links

* [Thinking Home](http://www.alwaysthinking.com/thinkingHome.html)
* [Insteon hacking guides](http://efundies.com/guides/)
	
### X10

X10 is a legacy technology that works primarily over the power line though some devices are wireless (using the X10 RF protocol). X10 can not be recommended anyone that starts a new home automation system because of it's poor reliability.

#### Mac Software

* [Thinking Home](http://www.alwaysthinking.com/thinkingHome.html)
* [Mister House](http://misterhouse.sourceforge.net/)

### DECT Ultra Low Energy

* [DECT ULE (Ultra Low Energy)](http://de.wikipedia.org/wiki/Digital_Enhanced_Cordless_Telecommunications#DECT_ULE_.28Ultra_Low_Energy.29)
* [DECT Ultra Low Energy sagt ZigBee und Bluetooth den Kampf an](http://www.elektroniknet.de/kommunikation/sonstiges/artikel/82162/)
* [Gigaset elements](https://www.gigaset-elements.com)
* [Gigaset elements: Nicholas Ord's keynote at BITKOM BIG DATA SUMMIT 2013](http://www.youtube.com/watch?v=ebxiSTMoJWU)

### UPB (Universal Powerline Bus)

* [UPB](http://www.pcslighting.com) transmits over the power line as X10 does, but with a much stronger and faster signal. It also supports having more devices, and it will retransmit commands if the recpipient does not aknowlege them

### WiFi

* Belkin WeMo
	* A dry-contact switch is a common type of switch; it works by opening or closing a circuit.
* Withings Scale

#### Misc.
* Modbus, SBUS

# Protocol overview

| Protocol | Power Line | Radio-Frequencey | Available API | Open Source | Needs Neutral Wire? |
| --- | ---| --- | --- | --- | --- |
| OpenHAB | either | either | yes | yes | no |
| C-Bus | no | yes | yes | no | no (uses category-5 UTP) |
| Insteon | yes | yes | yes | no | usually |
| KNX | yes | yes | yes | no | no |
| UPB | yes | no | no | no | no |
| X10 | yes | yes | yes | no | no |
| Zigbee | no | yes | yes | no | no |
| Z-wave | no | yes | no | no | Usually |
| BLE | | | | | |
| 433 RF | | | | | |

# Definition of Things

* **Thing Class #1:** Single-purpose device with limited state, CPU, and connectivity capabilities. Not directly addressable (requires a “hub” or the like to communicate with the outside world). No UI.   
**Examples:** Z-Wave switch or 1-Wire sensor or a Philips Hue lightbulb.
* **Thing Class #2:** Single-purpose device with  TCP/IP connectivity (including DHCP support), with support via some protocol for control API (ideally, REST) and “content” as necessary. May have UI.  
**Example:** a smart thermostat (such as a Nest).
	* **Thing Class #2A:** A subclass of #2, consisting of “hub”-type device whose main function is to orchestrate, and provide access to, a network of Class #1 devices.  Example: a 1-Wire hub or a proprietary sensor hub or a Philips Hue controller). The hub will likely support a protocol for discovering / browsing / adding / removing / initializing the devices it manages.
* **Thing Class #3:** I think the main distinguishing factor here is that devices in these classes are capable of accepting and executing general-purpose code (“apps”) on a dynamic basis… in other words, these are small “computers” in the classic sense, and, as such, can be deployed to function as instances of other classes of devices (such as a Class #2A “hub” or as a Class #2 thermostat). Examples: An Arduino or Beagle board, or even a 5 year old used PC that you bought for $25 at a used computer store and installed Ubuntu on and are using for your home automation project.
* **Thing Class #4:** I feel like it’s important to identify the class of things that includes “Connected TVs”, smart A/V receivers, or Sonos music players. These are high-function devices that would seem to be just Class 2 things. Yet, more and more, these kinds of things include a set of apps (for, say, viewing Amazon or Netflix content, or even browsing the web), they would seem to be Class #3 things. But somehow they don’t feel that way… they seem to be single-purpose (show video content or play audio content) and are sandboxed (restricted) with regard to which apps can be installed on them.

# Other

* [Homee (Indiegogo)](http://www.indiegogo.com/projects/homee-your-home-remote--2)
	* [Homee (Website)](http://hom.ee/)
* [Contiki: The Open Source OS for the Internet of Things](http://www.contiki-os.org/)
	* [Wikipedia](http://en.wikipedia.org/wiki/Contiki)
	* [Building the tools to build the Internet of Things](http://www.computerworld.com.au/article/527441/building_tools_build_internet_things/)
	* **Alternative to Contiki** [RiotOS](http://www.riot-os.org/)
* [thingsquare](http://thingsquare.com/)
* [Mozilla Location](https://wiki.mozilla.org/Services/Location)
* Complete Home automation website from a private person from the Netherlands: [Bwired.nl](http://www.bwired.nl/)
* [Newsgroup on Home Automation](https://groups.google.com/forum/?hl=en#!forum/comp.home.automation)

# Sensor Products

## Wi-Fi

* [LimitlessLED](http://www.limitlessled.com/)
* iRobot
	* [Roomba Wifi Remote](http://www.roomba-wifi-remote.com/)