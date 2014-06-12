---
layout: post
title: "Using bots for automatization"
slug: "research-using-bots-for-automatization"
date: 2014-06-07 11:34
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

* [github / hubot, Adapter: Gtalk](https://github.com/github/hubot/wiki/Adapter:-Gtalk): available in different versions as NPM.
* [markstory / hubot-xmpp, Adapter XMPP](https://github.com/markstory/hubot-xmpp/wiki): available in different as NPM.
* [github / hubot, Adapter: IRC](https://github.com/github/hubot/wiki/Adapter:-IRC): available in different versions as NPM.
* [github / hubot, Adapter: Twitter](https://github.com/github/hubot/wiki/Adapter:-Twitter): available in different versions as NPM.

There are a couple more [adapters available](https://github.com/github/hubot/wiki/) e.g. Twilio, Skype, Yammer etc.

### Heroku and Node.js

Available versions of Node.js and npm on Heroku

* [Node.js version manifest](http://heroku-buildpack-nodejs.s3.amazonaws.com/manifest.nodejs)
	* 0.8.2
	* 0.8.1
	* 0.8.0
	* 0.6.20
	* 0.6.18
	* 0.6.17
	* 0.6.16
	* 0.6.15
	* 0.6.14
	* 0.6.13
	* 0.6.12
	* 0.6.11
	* 0.6.10
	* 0.6.8
	* 0.6.7
	* 0.6.6
	* 0.6.5
	* 0.6.3
	* 0.4.10
	* 0.4.7
* [npm version manifest](http://heroku-buildpack-nodejs.s3.amazonaws.com/manifest.npm)
	* 1.1.41
	* 1.1.40
	* 1.1.39
	* 1.1.36
	* 1.1.35
	* 1.1.32
	* 1.1.9
	* 1.1.4
	* 1.1.1
	* 1.0.106
	* 1.0.94

### Deploying Hubot onto Heroku w/ IRC

#### Environment

* Node version: 0.6.14  
* npm version: 1.1.12  
* Hubot 2.2.0

#### Installation

* `sudo npm install -g snvm` installed in `/usr/local/bin/snvm -> /usr/local/lib/node_modules/snvm/bin/snvm`

**or**

* Install [nvm](https://github.com/creationix/nvm/) `git clone git://github.com/creationix/nvm.git ~/nvm`
* Activate nvm `. ~/nvm/nvm.sh`
* Install a specific Node.js version `nvm install v0.6.14`
* Download the lastest version of Hubot (look up the lastest URL at the [Hubot repository](https://github.com/github/hubot/downloads)) `wget https://github.com/downloads/github/hubot/hubot-2.2.1.tar.gz`
* untar `tar -xzvf hubot-2.2.1.tar.gz`
* remove tar file `rm hubot-2.2.1.tar.gz`
* `cd hubot`
* `vim package.json`

        …
        dependencies": {
          "hubot-irc": ">= 0.0.1",
          "hubot": ">= 2.0.0",
          …
        }
        …

add the specific engines use local to the package.json file

        …
        "hubot-scripts": ">=2.0.8",
        "nodepie": "0.5.0",
        "optparse": "1.0.3"
      },

        "engines": {
          "node": "0.6.14",
          "npm": "1.1.32"
          }
      }

* `vim Procfile`  
* `web: bin/hubot -a irc -n Hubot`
* delete the `"redis-brain.coffee"` line in `vim hubot-scripts.json`
* it should look like this `["tweet.coffee", "shipit.coffee"]`
* install all defined packages in package.json `npm install` (you could test the install by using `npm install test` in advance)
* Initialize the directory as a git repository `git init`
* Ignore .DS_Store files `vim .gitignore`
* Add line `DS_Store` and `node_modules`
* Add all the files in the directory to the git repository (except the ones defined in .gitgnore) `git add .`  
* Commit the added file to the git repository `git commit -m "Initial commit."`
* `git log`
* Create a new Heroku application `heroku create --stack cedar`
* This should add a remote to the git repository called heroku, push the git repository to Heroku. (Please note that Heroku expects your code to be on the "master" branch.) `git push heroku master`
* start Heroku with one "Dyno" `heroku ps:scale web=1`
* `heroku logs`
* `nvm use v0.6.14`
* `git clone git://github.com/github/hubot.git`
* `cd hubot`
* `npm install`
* `bin/hubot --create ../daemon`
* `cd ../daemon`
* `vim package.json`

        "dependencies": {
          "hubot": "2.3.0",
          "hubot-scripts": ">= 2.1.0",
           "optparse": "1.0.3",
           "hubot-irc": "0.0.6"
         },

         "engines": {
            "node": "0.6.14",
            "npm": "1.0.x"
          }

* `vim Procfile`
* add the line `app: bin/hubot -a irc`
* `git init .`
* `git add .`
* `git commit -m "My Hubot initial commit"`
* `heroku create daemon --stack cedar`
* `git push heroku master`
* `heroku addons:add redistogo:nano`
* `heroku config:add HUBOT_IRC_NICK="daemon"`
* `heroku config:add HUBOT_IRC_ROOMS="#your-id"`
* `heroku config:add HUBOT_IRC_SERVER="irc.Prison.NET"`
* `heroku ps:scale app=1`
* `heroku ps`
* `heroku logs`
* deploying to heroku and testing hubot with irc `heroku run ./bin/hubot -a irc -n nickname`

### Deploying Hubot onto Heroku w/ Jabber
`heroku config:add HUBOT_GTALK_USERNAME="your.id@your.server.de" HUBOT_GTALK_PASSWORD="johndoe"`  

### Deploying Hubot onto Heroku w/ Gtalk

tbd

### Deploying Hubot onto Heroku w/ Twitter

tbd

### Interesting scripts

* [hackernews.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/hackernews.coffee)  
	* `hubot hn top <N>` - get the top N items on hacker news (or your favorite RSS feed)  
	* `hn.top` - refer to the top item on hn
	* `hn[i]` - refer to the ith item on hn
* [heroku-status.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/heroku-status.coffee), Show current Heroku status and issues
	* `hubot heroku status` - Returns the current Heroku status for app operations and tools
	* `hubot heroku status issues <limit>` - Returns a list of recent <limit> issues (default limit is 5)
	* `hubot heroku status issue <id>` - Returns a single issue by ID number
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
* [sms.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/sms.coffee), Allows Hubot to send text messages using Twilio API
	* `hubot sms <to> <message>` - Sends <message> to the number <to>
	* **Configuration** HUBOT_SMS_SID, HUBOT_SMS_TOKEN, HUBOT_SMS_FROM
* [sosearch.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/sosearch.coffee), Search stack overflow and provide links to the first 5 questions
	* `sosearch me <query>` - Search for the query
	* `sosearch me <query>` with tags `<tag list sperated by ,>` - Search for the query limit to given tags
* [spotify.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/spotify.coffee), Metadata lookup for spotify links
	* `<spotify link>` - returns info about the link (track, artist, etc.)
* [tvshow.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/tvshow.coffee)
	* `hubot tvshow me <show>` - Show info about <show>
* [tumblr.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/tumblr.coffee), Display photos from a Tumblr blog
	* `hubot show me tumblr <count>` - Shows the latest <count> tumblr photos (default is 1)
	* Configuration: HUBOT_TUMBLR_BLOG_NAME, HUBOT_TUMBLR_API_KEY
* [twitter.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/twitter.coffee), gets tweet from user
	* `hubot twitter <twitter username>` - Show last tweet from <twitter username>
* [uptime-robot.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/uptime-robot.coffee), gets tweet from user
	* `hubot twitter <twitter username>` - Show last tweet from <twitter username>
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
* [google-reader.coffee](https://github.com/github/hubot-scripts/blob/master/src/scripts/google-reader.coffee), Subscribe to a feed in Google Reader
	* `hubot subscribe <domainname>` - returns whether you've subscribed succesfully
	* Configuration: GOOGLE_USERNAME, GOOGLE_PASSWORD

There are far more scripts available at the [Hubot Script Catalog](http://hubot-script-catalog.herokuapp.com/)

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

* [Deploying Hubot to Heroku like a boss](http://martinciu.com/2011/11/deploying-hubot-to-heroku-like-a-boss.html)
* [hubot Scripts Explained](http://theprogrammingbutler.com/blog/archives/2011/10/28/hubot-scripts-explained/)
* [IRC Log Viewer Using Hubot, CouchDB and Ember.js](http://code418.com/blog/2012/03/04/irc-log-viewer-using-hubot-couchdb-emberjs/)
* [Awesome Bot Factory](https://awesomebotfactory.com/), similar project to Hubot from Railsove done in Ruby
* [Hubot Deploy](http://www.travisberry.com/2012/02/hubot-deploy/) w/ Capistrano
* [Hubot Minecraft](http://blog.minefold.com/post/15425926505/hubot-minecraft)