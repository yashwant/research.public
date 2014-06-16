---
layout: post
title: "Scenarios for Apple HomeKit"
slug: "research-scenearios-for-apple-home-kit"
date: 2014-06-16 14:45
comments: true
categories: [design]
tags: [apple, home kit, homekit, iot, internet of things, home automatisation, home automatization, smart home]
published: true
---

# Scenarios for Apple HomeKit

## Go to sleep

When I go to sleep then check if nobody is in the living room, turn off the lights & tv in the living room, fade out my bedside light and set my alarm clock.

### Turn off the lights & tv in the living room

**Given nobody** is in the living room  
  **When** I activate the sleep mode on my \<fitbit>  
  **Then** turn off the lights in the living room  
  **And** turn off the tv  
  **And** fade out my bedside light  
  **And** set my alarm clock on my \<fitbit>

## Leave home

When I leave home then turn off all lights, my TV, adjust the heater and make sure I have my keys and wallet with me.

### Turn off the lights if nobody is home

**Given** nobody is home  
  **When** I leave the geofence \<Home>  
  **Then** turn off the lights  
  **And** adjust the heater  

### Get notified to take your keys & wallet with you

**Given** my keys  
  **And** wallet are still within your apartment  
  **When** I am \<1 meter> close to the front-door  
  **Then** send me  a notification that I should take my keys  
  **And** wallet with me

## Lighting & conservation

When there is no one in the room and/or it is dawn then turn off the lights.

### Turn off lights if there is nobody in the room

**Given** the lights are on  
  **When** there is nobody home since \<2> minutes  
  **Then** turn off the lights

### Turn on \<room> lights at dusk

**Given** the sun is at dusk  
  **When** there somebody home  
  **Then** turn on the lights in the \<room>

### Turn off \<room> lights at dawn

**Given** the sun is at dawn  
  **When** the sun rises  
  **Then** turn on off the lights in the \<room>

## Mobility

When I am ready to leave HOME then make sure I arrive on time and notify me to buy A ticket.

### Take public transport

**Given** I am ready to leave home  
  **And** set my destination  
  **When** I am \<1 meter> close to the front-door  
  **Then** check if there are any mobility problems  
  **And** say "Please do not forget to buy a ticket."  
  **And** say "You will arrive at \<time>“

### Go by car

**Given I am ready to leave home**  
  **And** set my destination  
  **When** I am \<1 meter> close to the front-door  
  **Then** check if there are any mobility problems  
  **And** say "Do not forget your car keys. You can find them at \<location>.“  
  **And** check if there is a parking spot close to the destination and send me a notification on any issues

## System health

When there is any error with the system then inform me.

### System not reachable from outside my firewall

**Given** the system is not reachable from outside my firewall  
  **When** the system is not reachable for more then \<60 seconds>  
  **Then** send me a notification

### No internet access (from inside the firewall)

**Given** there is no internet access from inside the firewall  
  **When** there is no access longer then \<60 seconds>  
  **Then** reset the power connection to my modem, router and switch  
  **And** test the connection again

### Server temperature is too high

**Given** the server temperature is too high  
  **When** the temperature is higher then \<XX> celsius
  **Then** send me a notification

### Power failure or the power is restored

**Given** there is a power failure or the power is restored  
  **When** there is power failure or the power is restored  
  **Then** send me a notification


## Wake Up

When I wake up then turn on my bedside lights and inform me on latest news.

### Turn on bedside lights

**Given** I set my \<fitbit> alarm  
  **When** my \<fitbit> alarm is vibrating  
  **Then** turn on the bedside lights to \<40%>  
  **And** fade it to \<60%> within \<5> minutes

### Watch \<Tagesschau> and send the sound through \<AirFoil>

**Given** I set my \<fitbit> alarm  
  **When** my \<fitbit> alarm is vibrating  
  **Then** wait \<5> minutes  
  **And** start my television  
  **And** start my AppleTV  
  **And** play the latest \<Tagesschau> podcast

### After I woke up inform me how many new Emails I received and let me know about my daily tasks

**Given** I set my \<fitbit> alarm  
  **When** my \<fitbit> alarm is vibrating  
  **Then** say how many Emails I received  
  **And** say my daily tasks through \<Airfoil>

## Watch TV

When I watch TV with \<Plex> then turn on the lights in the living room, adjust the volume level and TURN every disturbing noise off.

### Turn on the lights when I watch TV with \<Plex>

**Given** it is dark outside  
  **When** I turn on \<Plex>  
  **Then** turn on the \<movie lights> in the living room  
  **And** adjust the volume level

### Turn off every disturbing noise

**Given** I turn on \<Plex>  
  **Then** turn off any other light then the \<movie lights>  
  **And** set the \<music network> off

## Arrive Home

When I arrive at home then turn on the lights, send a welcome message and check-in on \<foursquare>.

### Turn on the lights if nobody is home and it is dark outside

Given nobody is home   
  **And** it is dark outside  
  **When** I enter the geofence \<Home>  
  **Then** turn on the lights in the hallway  
  **And** living room

### Do a check-in and send a welcome message

**Given** you have not been home within the last \<24 hours>  
  **When** I enter the geofence \<Home>  
  **Then** do a check-in on \<foursquare>  
  **And** send me a notification „Welcome home!“

## Weather and irrigation

When it is spring or summer time then run the sprinkler on regular schedules.

### Run sprinklers on regular schedules

**Given** it is spring or summer time  
  **When** it is has not rained within the last \<4 hours> as detected by the local weather station  
  **Then** run the sprinklers every \<24 hours>

### Do not run sprinklers when the windows are open and notify me

**Given** the sprinkler variable toggles to "run"  
  **When** windows are open  
  **Then** set the sprinklers to "off"  
  **And** send me a notification

## Alerts

When I leave home then turn on the security alert and report problems with the washing machine, fridge and dishwasher.

### Turn on the security system

**Given** nobody is home  
  **When** I leave the geofence \<Home>  
  **Then** turn on the security system

### Turn off the security system

**Given** the security system is on  
  **When** I enter the geofence "Home"  
  **Then** turn off the security system

### Randomly cycle lights to simulate occupancy

**Given** the security system is on  
  **When** the security system is since \<30 minutes>  
  **Then** turn on the lights randomly between \<30 minutes> and \<90 minutes>  
  **And** turn off the lights randomly after \<5 minutes> to \<15 minutes>

### Lock all desktop screens

**Given** the security system is on  
  **When** the security system is on since \<5 minutes>  
  **And** nobody is at home  
  **Then** lock all computers

### Security system notification

**Given** the security system is on  
  **When** it is \<10pm>  
  **Then** send me a notification summarizing the status of the system

### Notify me on problems with the washing machine

**Given** I am not in the bathroom  
  **When** moisture control reports a problem  
  **Then** send me a notification

### Notify me on problems with the fridge

**Given** I am not in the kitchen  
  **When** moisture control reports a problem  
  **Then** send me a notification

### Notify me on problems with the dishwasher

**Given** I am not in the kitchen  
  **When** moisture control reports problems  
  **Then** send me a notification

### Notify me if I have to take out the waste bin or recycling bin

**Given** you have the actual dataset to take out the waste bin and recycling bin  
  **When** I have to take out the trash
  **Then** send me a notification
  **And** tell me which trashcan I have to take out

### Log my alerts as bot events

**Given** a new alert happened  
  **When** the security system armed, disarmed, triggered or fridge and dishwasher reported any problems
  **Then** log \<zero minutes> events on my \<bot events> calendar

### Send notification when security system is armed

**Given** the security system toggles status to activated  
  **When** the security system is activated
  **Then** send me a notification

### Send notification when security system is disarmed

**Given** the security system toggles status to deactivated  
  **When** the security system is deactivated  
  **Then** send me a notification

### Send notification when a motion alert is triggered

**Given** the security system is activated  
  **When** there is motion detected  
  **Then** send me a notification

### Send notification when a window is left open and nobody is home

**Given** the security is activated  
  **When** there is a window left open  
  **Then** send me a notification  
  **And** deactivate the security system

### When the postman delivers the mail send me a notification

**Given** there is enough energy for the sensors  
  **When** the postman delivers the mail  
  **Then** send me a notification

### When the dryer is finished send me a notification

**Given** the dryer is turned on  
  **When** the dryer is finished  
  Then send me a notification

## Food

When there is any issue in relation to food then make sure I get informed, e.g. food is expired or I need to buy new food.

### Food is out of stock

**Given** the fridge is on  
  **When** there is any food that needs to be replaced  
  **Then** send me a notification message with the name of the product

### Fruits are ripe

**Given** I bought fruits  
  **When** they are ripe  
  **Then** send me a notification that I should eat them

### Food shelf life has already expired

**Given** I bought food  
  **And** it is at least \<24 hours> old  
  **When** the food is expired  
  **Then** send me a notification that I should assure if I still want to eat it