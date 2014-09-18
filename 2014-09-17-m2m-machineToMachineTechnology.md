---
layout: post
title: "M2M - Machine to Machine technology"
slug: "research-m2m"
date: 2014-09-17 12:55
comments: true
categories: [iot]
tags: [internet of things, mqtt, iot, m2m, machine 2 machine, machine learning, automation, smart cities]
published: true
---

# M2M

**Use cases**

| Type and public safety | Description |
| ---------------------- | ----------- |
| *Security and public safety* | surveillance systems, control of physical access (e.g. buildings), environmental monitoring (e.g., for natural desasters), backup for landlines |
| *Smart grid* | electricy, gas, water, heating, grid control, industrial metering, demand response |
| *Tracking and tracing* | order management, asset tracking, human monitoring |
| *Vehicular telematics* | fleet management, car/driver security, enhanced navigation, traffic info, tolls, pay as you drive, remote vehicle diagnostics |
| *Payment* | point of sale, ATM, vending machines, gaming machines |
| *Healthcare* | monitoring vital signs, supporting the aged or handicapped, web access telemedicine points, remote diagnostics |
| *Remote maintenance and control* | Industrial automation, sensors, lighting, pumps, vending machine control |
| *Consumer devices* | digital photo frame, digital camera, ebook, home management hubs |

Source: [http://www.iith.ac.in/~tbr/teaching/presentations/15.pdf](http://www.iith.ac.in/~tbr/teaching/presentations/15.pdf)

**Examples**

* **Vehicular telematics** – an example of a safety and security service is Automatic Crash Notification. This service utilizes various crash sensors on the vehicle to report the location and extent of damage to the vehicle in the event of a crash. It also initiates a voice call to facilitate reporting of the crash to Emergency services.  
Telematics and in-vehicle entertainment is an area of focus for M2M developers. Recent examples include Ford Motor Company, which has teamed with AT&T to wirelessly connect Ford Focus Electric with an embedded wireless connection and dedicated app that includes the ability for the owner to monitor and control vehicle charge settings, plan single- or multiple-stop journeys, locate charging stations, pre-heat or cool the car. In 2011, Audi partnered with T-Mobile and RACO Wireless to offer Audi Connect. Audi Connect allows users access to news, weather, and fuel prices while turning the vehicle into a secure mobile Wi-Fi hotspot, allowing passengers access to the Internet.

**Resources**

* http://m2m.eclipse.org

Devices must communicate with each other (D2D). Device data then must be collected and sent to the server infrastructure (D2S). That server infrastructure has to share device data (S2S), possibly providing it back to devices, to analysis programs, or to people. From 30,000 feet, the protocols can be described in this framework as:

* MQTT: a protocol for collecting device data and communicating it to servers (D2S)
* XMPP: a protocol best for connecting devices to people, a special case of the D2S pattern, since people are connected to the server
* DDS: a fast bus for integrating intelligent machines (D2D)
* AMQP: a queuing system designed to connect servers to each other (S2S)

## Ajax, Web services, RESTful

Ajax, Web services, RESTful communication protocols. These sit on top of HTTP, thus suffering from the same limitations as HTTP. Many of these protocols also require extensive processing and have a huge code size footprint. Many service providers promote the use of these protocols since their backend infrastructure is based on standard web servers that cannot handle any other type of protocol than HTTP.

## Protocols

### AllJoyn

**by AllSeen Alliance**  
The AllSeen Alliance consists of several manufacturers. Qualcomm is the star player in the alliance, but other leading members include Haier, LG Electronics, Panasonic, Sharp, Silicon Image and TP-LINK. Lower-level members include Canary, Cisco Systems, D-Link, doubleTwist, Fon, Harman, HTC, Letv, LIFX, Lite-on, Moxtreme, Musaic, Sears Brand Management Corporation, Sproutling, The Sprosty Network, Weaved and Wilocity.

A persistent publish/subscribe solution promoted by Qualcomm. This protocol has the limitation of being mainly targeted towards home electronics. This protocol includes code for marshalling and unmarshalling (encode/decode) data and suffers from the same size and proxy problems as MQTT

* [Official website](https://www.alljoyn.org)
* [Offical YouTube channel](http://www.youtube.com/user/alljoyn)
* InformationWeek article: [AllJoyn: A Common Language For Internet Of Things](http://www.informationweek.com/big-data/software-platforms/alljoyn-a-common-language-for-internet-of-things/d/d-id/1204467)
* [One standard to sync them all: AllSeen Alliance forms to accelerate Internet of Things adoption](http://www.theverge.com/2013/12/10/5194342/one-standard-to-sync-them-all-allseen-alliance-forms-to-accelerate)

### XMPP

**by XMPP Standards Foundation**  
An open source persistent publish/subscribe protocol that can also be tunneled over HTTP. Data is encoded in XML, thus it includes a huge code size footprint for the device.

* [Official website](http://xmpp.org)
* XMPP wiki: [InternetOfThings](http://wiki.xmpp.org/web/InternetOfThings)

### MQTT

**by IBM**  
MQTT is a publish/subscribe messaging system that allows clients to publish messages without concerning themselves about their eventual destination; messages are sent to an MQTT broker where they may be retained. Other clients can subscribe to these messages and get updated by the broker when new messages arrive. To allow for the variety of possible situations where MQTT can be put to use, it lets clients and brokers set a "Quality of Service" on a per-message basis from "fire and forget" to "confirmed delivery". This protocol is not suitable for environments that include a proxy, as it is not designed to work via a proxy.

* [Official website](http://mqtt.org)
* [MQTT and CoAP, IoT Protocols](http://www.eclipse.org/community/eclipse_newsletter/2014/february/article2.php)
* [Building MongoDB Into Your Internet of Things: A Tutorial](https://blog.compose.io/building-mongodb-into-your-internet-of-things-a-tutorial/)

At a glance…

* Application-layer protocol
* Runs on top TCP
* Binary-wire protocol
* No message queue albeit the name
* Publish/subscribe pattern
* Designed for resource-constrained devices
* UTF-8 encoded strings (since V3.1)
* Payload agnostic
* Keep-Alive timer
* QoS
* Port numbers: 1883 for MQTT, 8883 for MQTT over SSL

### CoAP

**by IP for Smart Objects Alliance**  
CoAP is a software protocol intended to be used in very simple electronics devices that allows them to communicate interactively over the Internet. It is particularly targeted for small low power sensors, switches, valves and similar components that need to be controlled or supervised remotely, through standard Internet networks. Source: [Wikipedia](https://en.wikipedia.org/wiki/Constrained_Application_Protocol)

* [node-coap](https://github.com/mcollina/node-coap) is a client and server library for CoAP modelled after the http module.

### DDS

**by Object Management Group**  
In contrast to MQTT and XMPP, the Data Distribution Service (DDS) targets devices that directly use device data. It distributes data to other devices. While interfacing with the IT infrastructure is supported, DDS’s main purpose is to connect devices to other devices. It is a data-centric middleware standard with roots in high-performance defense, industrial, and embedded applications. DDS can efficiently deliver millions of messages per second to many simultaneous receivers.

* [Official website](http://portals.omg.org/dds/)

### AMQP

**by AMQP working group**  
The Advanced Message Queuing Protocol (AMQP) is sometimes considered an IoT protocol. AMQP is all about queues. It sends transactional messages between servers. As a message-centric middleware that arose from the banking industry, it can process thousands of reliable queued transactions.  
AMQP is focused on not losing messages. Communications from the publishers to exchanges and from queues to subscribers use TCP, which provides strictly reliable point-to-point connection. Further, endpoints must acknowledge acceptance of each message. The standard also describes an optional transaction mode with a formal multiphase commit sequence. True to its origins in the banking industry, AMQP middleware focuses on tracking all messages and ensuring each is delivered as intended, regardless of failures or reboots.

* [Official website](http://www.amqp.org)

### Interesting articles on protocols

* [Stomp](http://stomp.github.io) by Stomp Spec Group, Thread by Thread Group, WAMP by Tavendo
* [Messaging Technologies for the Industrial Internet and the Internet of Things Whitepaper](http://www.prismtech.com/sites/default/files/documents/Messaging-Comparison-Whitepaper-July2014.pdf) – A Comparison Between DDS, AMQP, MQTT, JMS, REST and CoAP
* [Internet of Things : protocols war !](http://de.slideshare.net/paolopat/internet-ofthingsprotocolswar)

## Platforms

### Octoblu Meshblue

* the API supports the following IoT protocols: **HTTP**, **REST**, **WebSockets**, **MQTT (Message Queue Telemetry Transport)**, and **CoAP (Constrained Application Protocol)**
* every connected device is assigned a 36 character UUID and secret token that act as the device’s strong credentials. Security permissions can be assigned to allow device discoverability, configuration, and messaging.

#### Projects

* [Official website](http://www.skynet.im)
* Github: [octoblu/meshblu](https://github.com/octoblu/meshblu)
* Github: [octoblu/gateblu](https://github.com/octoblu/gateblu) – Octoblu Gateway for your LAN-based IoT devices 
http://skynet.im
* Github: [octoblu/microblu_mqtt](https://github.com/octoblu/microblu_mqtt). Microblu OS (firmware for Arduino-compatible devices) using MQTT.
* Github: [octoblu/octopi](https://github.com/octoblu/octopi) - run a private Skynet server on your Raspberry Pi and connect it to e.g. your Arduino clients
* [octoblu/skynet-docker](https://github.com/octoblu/skynet-docker/blob/master/Dockerfile)
* Github: [octoblu/examples](https://github.com/octoblu/examples). Collection of node.js arduino and npm skynet examples.
* [ElectricImp-SkyNet](https://github.com/electricimp/reference/tree/master/webservices/skynet), [electric imp](https://electricimp.com/)
* Github [Octoblu Pebble App](https://github.com/octoblu/octoblu-pebble)
* [Skynet NPM plugins](https://www.npmjs.org/search?q=skynet-plugin)


#### Tutorials

* Video: [Using @SKYNETim to track Heartbeats and Geolocation #HackIoT](https://www.youtube.com/watch?v=UVLarHyJPBY)
* [YouTube videos](https://www.youtube.com/results?search_query=meshblu)
* [Connect Hue Bulbs to SkyNet](https://medium.com/@chrismatthieu/connect-hue-bulbs-to-skynet-8d5d15511001)

### Other platforms

* [Carriots](https://www.carriots.com)
* [Xively](https://xively.com/)
* [Litmus Automation](http://litmusautomation.com/)
* [Eurotech Everyware Device Cloud](http://www.eurotech.com/en/products/software+services/everyware+device+cloud)
* [2lemetry ThingFabric](http://2lemetry.com/iot-platform/)
* [Paho](http://www.eclipse.org/paho/). The Paho project provides scalable open-source client implementations of open and standard messaging protocols aimed at new, existing, and emerging applications for Machine‑to‑Machine (M2M) and Internet of Things (IoT). [Practical MQTT with Paho](http://www.infoq.com/articles/practical-mqtt-with-paho)
* …

## Broker (for MQTT)

A broker in MQTT handles receiving published messages and sending them on to any clients who have subscribed.

### Mosquitto

C, small standalone binary, fast, standards-compliant/complete, MQTT only

* [Mosquitto](http://mosquitto.org/)
* [docker-mqtt / Dockerfile](https://github.com/ncarlier/docker-mqtt/blob/master/Dockerfile)
* [icmurray/docker-mqtt-mosquitto-server](https://github.com/icmurray/docker-mqtt-mosquitto-server/blob/master/Dockerfile)
* https://registry.hub.docker.com/search?q=mqtt&searchfield=
* OS X `brew install mosquitto`

### RabbitMQ

Erlang, enterprise quality, larger footprint, MQTT plugin to AMQP broker

* OS X `brew install rabbitmq`

### Mosca

Mosca is a node.js mqtt broker.

* Github: Dockerfile [mcollina/mosca](https://github.com/mcollina/mosca)
* Dockerfile: [matteocollina / mosca](https://registry.hub.docker.com/u/matteocollina/mosca/)
* [Official website](http://www.mosca.io/)

#### Other brokers

* [Eclipse moquette](https://projects.eclipse.org/proposals/moquette-mqtt), [Apache ActiveMQ](http://activemq.apache.org) (includes MQTT, broader set of protocols), [HiveMQ](http://www.hivemq.com) (Java, not Open Source), [GnatMQ](https://mqttbroker.codeplex.com) (.NET)

## Frameworks (for MQTT)

* [Eclipse Ponte](http://eclipse.org/proposals/technology.ponte/)
* [mihini](http://www.eclipse.org/mihini) is a set of libraries providing building blocks to develop M2M applications e.g. serial and I/O management, networking (FTP, HTTP, Email…), GPS, [Modbus](https://en.wikipedia.org/wiki/Modbus), local storage etc.
	* [Mihini/M3DA Specification](http://wiki.eclipse.org/Mihini/M3DA_Specification). M3DA is a protocol optimized for the transport of binary M2M data

## Tools (for MQTT)

* [mqtt-shell](https://github.com/pidster-dot-org/mqtt-shell)
* [fabaff/mqtt-panel](https://github.com/fabaff/mqtt-panel). A web interface for MQTT. mqtt-panel depends on a couple of additional pieces:
	* Node.js
	* MQTT
	* MQTT broker/server e.g. Mosca or Mosquitto
	* Socket.io
	* Firmata if using with an Arduino
* [Koneki](http://projects.eclipse.org/projects/technology.koneki)
* Github: [adamvr / MQTT.js](https://www.github.com/adamvr/MQTT.js). An MQTT librar for node.js.

## Events

* [OggCamp](http://www.oggcamp.org)