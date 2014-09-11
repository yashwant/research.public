---
layout: post
title: "Using bots for automatization"
slug: "research-using-bots-for-automatization"
date: 2014-09-11 15:34
comments: true
categories: [coding]
tags: [bots, automatisation, hubot]
published: true
---

# Using bots for automatization

## Jabber 

[Group chat (chat room) in ichat using google talk](http://amitparekh.wordpress.com/2011/01/05/group-chat-chat-room-in-ichat-using-google-talk/)  

These are the steps:

1. Generate a UUID, by the command-line `uuidgen` in Terminal or by a web generator.
2. In iChat, `File` > Go to `Chat Room` and as room name enter `private-chat-UUID@groupchat.google.com` where UUID is the UUID you just generated. An example for a possible room name: `private-chat-ff089070-ddd8-11df-85ca-0800200c9a66@groupchat.google.com`
3. You can also check the autojoin checkbox when adding a chat room which will automatically open the group chat when you sign into ichat

### Jabber Bots

* [Jabberwacky](http://www.jabberwacky.com), [Wikipedia](http://de.wikipedia.org/wiki/Jabberwacky)
* [morpheus](http://www.theuniversesolved.com/morpheusgreatesthits.htm)

## Hubot

* [Hubot](http://hubot.github.com/) was an almost mythical GitHub campfire bot. They use it for deploying, automate a lot of tasks, and to be a source of fun in the company.

### Adapter

Adapters are the interface to the service you want your hubot to run on.

* Github: [Overview on available adapters](https://github.com/github/hubot/blob/master/docs/adapters.md) or at the [Hubot Script Catalog](https://hubot-script-catalog.herokuapp.com/)
* Github: [Adapter: Gtalk](https://github.com/atmos/hubot-gtalk/): available in different versions as NPM.
* Github: [Adapter XMPP](https://github.com/markstory/hubot-xmpp/wiki): available in different as NPM.
* Github: [Adapter: IRC](https://github.com/nandub/hubot-irc): available in different versions as NPM.
* Github: [Adapter: Twitter](https://github.com/mathildelemee/hubot-twitter): available in different versions as NPM.

There are a couple more [adapters available](https://github.com/github/hubot/wiki/) e.g. Twilio, Skype, Yammer etc.

### Interesting scripts

* [hackernews.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/hackernews.coffee)  
	* `hubot hn top <N>` - get the top N items on hacker news (or your favorite RSS feed)  
	* `hn.top` - refer to the top item on hn
	* `hn[i]` - refer to the ith item on hn
* [play.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/play.coffee), Play music. At your office. Like a boss. [Github Page](https://github.com/play/play)
	* `hubot play` - Plays music.
	* `hubot play next` - Plays the next song.
	* `hubot play previous` - Plays the previous song.
	* `hubot what's playing` - Returns the currently-played song.
	* `hubot I want this song` - Returns a download link for the current song.
	* `hubot I want this album` - Returns a download link for the current album.
	* `hubot play <artist>` - Queue up ten songs from a given artist.
	* `hubot play <album>` - Queue up an entire album.
	* `hubot play <song>` - Queue up a particular song. This grabs the first song by playcount.
	* `hubot play <something> right [fucking] now` - Play this shit right now.
	* `hubot where's play` - Gives you the URL to the web app.
	* `hubot volume?` - Returns the current volume level.
	* `hubot volume [0-100]` - Sets the volume.
	* `hubot be quiet` - Mute play.
	* `hubot say <message>` - `say` your message over your speakers.
	* `hubot clear play` - Clears the Play queue.
* [pomodoro.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/pomodoro.coffee), Hubot's pomodoro timer
	* `hubot start pomodoro` - start a new pomodoro
	* `hubot start pomodoro` <time> - start a new pomodoro with a duration of <time> minutes
	* `hubot stop pomodoro` - stop a pomodoro
	* `hubot pomodoro?` - shows the details of the current pomodoro
	* `hubot total pomodoros` - shows the number of the total completed pomodoros
* [rubygems.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/rubygems.coffee), Find a rubygem from rubygems.org
	* `hubot there's a gem for <that>` - Returns a link to a gem on rubygems.org
* [sosearch.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/sosearch.coffee), Search stack overflow and provide links to the first 5 questions
	* `sosearch me <query>` - Search for the query
	* `sosearch me <query>` with tags `<tag list sperated by ,>` - Search for the query limit to given tags
* [spotify.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/spotify.coffee), Metadata lookup for spotify links
	* `<spotify link>` - returns info about the link (track, artist, etc.)
* [tvshow.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/tvshow.coffee)
	* `hubot tvshow me <show>` - Show info about <show>
* [uptime.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/uptime.coffee), show uptime status of sites monitored by UptimeRobot.
	* `hubot what is the uptime of the monitored sites?` - Show the status of the monitored sites
	* `hubot start monitoring the http uptime of <url>` - Instructs uptime robot to monitor the <url>
	* Configuration: HUBOT_UPTIMEROBOT_APIKEY
* [weather.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/weather.coffee), Returns weather information from Google
	* `hubot weather <city>` - Get the weather for a location
	* `hubot forecast <city>` - Get the forecast for a location
	* Configuration: HUBOT_WEATHER_CELSIUS - Display in celsius
* [wikipedia.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/wikipedia.coffee)
	* `hubot wiki me <query>` - Searches for <query> on Wikipedia.
* [aws.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/aws.coffee), Queries for the status of AWS services
	* `hubot sqs status` - Returns the status of SQS queues
	* `hubot ec2 status` - Returns the status of EC2 instances
	* Configuratin: HUBOT_AWS_ACCESS_KEY_ID, HUBOT_AWS_SECRET_ACCESS_KEY, HUBOT_AWS_SQS_REGIONS, HUBOT_AWS_EC2_REGIONS
* [git-help.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/git-help.coffee), Show some help to git noobies
	* `git help <topic>`
* [github-activity.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/github-activity.coffee), hubot repo show <repo> - shows activity of repository
	* Configuration: HUBOT_GITHUB_TOKEN, HUBOT_GITHUB_USER
* [github-commiters.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/github-commiters.coffee), Show the commiters from a repo
	* `hubot repo commiters <repo>` - shows commiters of repository
	* `hubot repo top-commiters <repo> - shows top commiters of repository
	* Configuration: HUBOT_GITHUB_TOKEN

### Hubot commands

#### Standards

* `hubot <keyword> tweet` - Returns a link to a tweet about `<keyword>`
* `ship it` - Display a motivation squirrel
* `<user> is a badass guitarist` - assign a role to a user
* `<user> is not a badass guitarist` - remove a role from a user
* `animate me <query>` - The same thing as `image me`, except adds a few
* `convert me <expression> to <units>` - Convert expression to given units.
* `help` - Displays all of the help commands that Hubot knows about.
* `help <query>` - Displays all help commands that match `<query>`.
* `image me <query>` - The Original. Queries Google Images for `<query>` and
* `map me <query>` - Returns a map view of the area returned by `query`.
* `math me <expression>` - Calculate the given expression.
* `mustache me <query>` - Searches Google Images for the specified query and
* `mustache me <url>` - Adds a mustache to the specified URL.
* `pug bomb N` - get N pugs
* `pug me` - Receive a pug
* `show storage` - Display the contents that are persisted in redis
* `show users` - Display all users that hubot knows about
* `translate me <phrase>` - Searches for a translation for the `<phrase>` and then
* `translate me from <source> into <target> <phrase>` - Translates `<phrase>` from `<source>` into `<target>`. Both `<source>` and `<target>` are optional
* `who is <user>` - see what roles a user has
* `youtube me <query>` - Searches YouTube for the query and returns the video

### Interesting articles

* [Automate Your Development Activities with Hubot](http://www.icicletech.com/blog/automate-your-development-activities-with-hubot)
* [hubot Scripts Explained](http://theprogrammingbutler.com/blog/archives/2011/10/28/hubot-scripts-explained/)

#### Deployments

* Github: [atmos/hubot-deploy](https://github.com/atmos/hubot-deploy). GitHub Flow via hubot. Chatting with hubot creates deployments on GitHub and dispatches Deployment Events.
* Github: [hubot-auto-deploy](https://github.com/atmos/hubot-auto-deploy). GitHub Flow via hubot. Chatting with hubot configures auto-deployment on GitHub and dispatches Deployment Events when criteria is met.
* Github: [github/janky](https://github.com/github/janky). Continuous integration server built on top of Jenkins and Hubot.
* [Team Management with Hubot](http://blog.dobt.co/2014/01/28/team-management-with-hubot/)
* [Hubot Deploy](http://www.travisberry.com/2012/02/hubot-deploy/) w/ Capistrano