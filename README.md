# discord-example
<p align="center">
  <img src="https://steemitimages.com/p/7ohP4GDMGPrUMp8dW6yuJTR9MKNu8P8DCXDU9qmmjZuTBVms9T3TUL1FMwfVyGcixRpw2CmDvLuAwnPpT65X9wuQnkwsSE21Z1T2?format=match&mode=fit">
</p>

What's up friends, with my most recent publication about [Navi](https://steemit.com/utopian-io/@anonym0us/tutorial-create-our-own-discord-button-part-1-upload-it-to-a-web-server-1537571612222#), many people have asked me, "Anonym0us, How can I make my own bot for my discord community?", So I decided to upload this simple, but essential tutorial about our own Discord bot, which will be adding more functions to these weeks, but for now we will do something simple: How to upload it to a server, and how to make it run simple function.

### What Is a Discord Bot?
If you do not know what a Discord bot is, friend let me tell you that you do not live in the 21st century or have never used Discord. The definition of a bot is simple
> A Discord bot is like a phones Siri.
It’s not necessary to do what you need to do, but it provides functionality and various tools that enable your server to be more lightweight, and streamlined. For example, in order to ban someone from your server, you’d need to go to their profile, scroll down and find the ban @name option. Whereas a discord bot could allow you to do that by inputting a short command in to the chat line, e.g. *.Ban name — this reduces the hassle required to find and scroll. It's quicker, not necessarily better.

### What Will I Learn?
You will learn the essential basis of the construction of our first bot, which is like starting (it always turns out to be the most difficult thing because you are creating something), added to this we will have a small script that will have a simple function and, we will learn how to keep active that bot every day at any time.

The programming language we will use is JS, which does not need to be a professional to program this bot, and you will see that if you take the pleasure of the thing, you will add more functions to your discord server and everything will be more simplified thanks to our bot.

### Requirements
⋅⋅* A [Discord](https://discordapp.com/) Account.
⋅⋅* A [GitHub](https://github.com/) Account.
⋅⋅* A [Heroku](https://www.heroku.com/) Account.
⋅⋅* Basic knowledge of JavaScript.
⋅⋅* Some patience.

### Difficulty
⋅⋅* Easy

### Creating your Bot on Discord
Open the following link and login using your discord account:
https://discordapp.com/developers/applications/me

We will create a new application, in this application we will have all the data of our bot once created, in if we can change the name to make the bot public or not.

Create a New Application.
![create](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmNZ6jCCzszrJPPGdrusu1r416P4EBeGN4eQY5RToQQspQ)

Follow this instruction and Create a new application - Name Your App, Select an Avatar/Icon, and click "Create App."

![](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmXQDWQRRfRZxMtK3UVHNTH5vhoPqCA6jYsS7cQzA29h9J)

Once the App is created, select it and Click on "Create a Bot User." Confirm and Choose "Yes. Do It!" on the box that pops up.

![](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmTWTPUqJHVbdrhd6jXt3AxWrPwoWpBKfPBdrgWxh73jot)

Make sure to take Note of the Client ID and Token. You will need these later when you begin programming your bot. Do not share this information!

Next you need to invite the Bot to your Discord Server using the following link:
https://discordapp.com/oauth2/authorize?&client_id=YOUR_CLIENT_ID_HERE&scope=bot&permissions=0

#### Replace YOUR_CLIENT_ID_HERE with the Client ID from your created Bot.

For a detailed walkthrough of this section, you can follow the following link:
https://github.com/reactiflux/discord-irc/wiki/Creating-a-discord-bot-&-getting-a-token

Once the first part is ready, we start with what some call the most difficult or strong part, the script. The script will allow you as a programmer or owner of the bot to decide what to do and what not to do, in a few words, the script will allow you to program all the operation of your bot.

Creating the Script
Once created our GitHub account, go with the following link to GitHub to create the repository: https://github.com/new

For this tutorial, it is necessary to use 3 scripts, the main one, so to speak, which will contain both the bot's information and everything that can be programmed to it.

![](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmZeg6Um9d9x6UPCCpbToYfqTEAcs9Ye5Pr6eAUEEQpe5P)

This is our main script, whose name is `bot.js.`

`bot.js`

```javascript
const Discord = require('discord.js');

const client = new Discord.Client();

 

client.on('ready', () => { // know if our bot is online

    console.log('I am ready!');

});

 

client.on('message', message => { // When the message a message is executed

    if (message.content === 'ping') { // if that message matches ping

       message.reply('pong'); // 

       }

});

 

// THIS  MUST  BE  THIS  WAY

client.login(process.env.BOT_TOKEN);//where BOT_TOKEN is the token of our bot
```

You will ask, what does that script mean? the script contains two functions, the first is to know when the bot is connected, in our console it will tell us that it is online within the server, and the other is just a small one of many functions that a bot can have, when any user send a message through the discord server where our bot is hosted and that message or command matches the script, execute the function. In this tutorial and in that script, when the user executes the command (or saying it colloquially, "when the user sends a message") whose information is "ping", our bot will process it and will respond to us, as simple as it expresses it in the script.

The package.json, which contains a list of packages with which to compile it in heroku, or the pc, or any other compiler, will export all the packages that our bot needs for its optimal compilation, if you want to expand your knowledge about the .json files, you can google here

`package.json`

```json

  "name": "Test",

  "description": "Test",

  "version": "0.0.0",

  "main": "bot.js",

  "scripts": {

    "start": "node bot.js"

  },

  "dependencies": {

    "discord.js": "11.1.0",

    "request": "2.81.0"

  }

}
```

And last but not least the Procfile, you'll wonder what the hell is that, well, Heroku apps (Application that we'll work with too) include a Procfile that specifies the commands that are executed by the app's dynos. You can use Procfile to declare a variety of process types, including:

-Your app's web server
-Multiple types of worker processes
-A singleton process, such as a clock
-Tasks to run before a new release is deployed
-Each dyno in your app belongs to one of the declared process types, and it executes the command associated with that process type.

`Procfile`
`worker: node bot.js`

![](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmVLZUX2ZdYtviU26MQmR3r7xfUa9pBtL6YLQ4LqkwfNNa)

Our git structure, should appear like this, do not worry if you notice different or feel that this something bad, it can always happen, err is human and is part of our learning, if you want, go directly to the repository link and take as reference that.

### Uploading the Script to a Server
Heroku is a platform as a cloud computing service that supports different programming languages.

![](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmQp4bm3TzjqDnaRiSFP9uK7kjeE889qPXDx47jv4YWS8T)
We will take advantage of that Heroku service to keep our bot activated

We will create a new board where the script will be uploaded here the link:
https://dashboard.heroku.com/apps

![](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmWTKXaJZxherxpU5gYaRzxM5JcyTetr4K94fiNTNudjZf)

Let's go to the resources section and select github.

![](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmVG2RJ4hk7wzNZJhkNNyZcwvQB7eCKvTrh3naoNeGSCUv)

Here we select our GitHub repository.
We will select enable automatic desploy.

![](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmaPyPKthUKcjPDgTSR5kvYFatVHGtfoqpizZBvgUKtpH6)

Now we have to select what script we are going to work on, for that we go to resources and in free dynos we deselect the web and activate the worker

![](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmSFSb9ti7jR3CSbFuULiDyeufoEW3PDw8W6HxevMPqZTg)

And our script would be online and working, but now we need to tell the script which bot is the one that is going to be linked to the script, that's why we go for settings

Then we will find an option called config variables,
add a new variable whose key will be `BOT_TOKEN` and the value of that variable will be the token of our bot.

![](https://steemitimages.com/640x0/https://ipfs.busy.org/ipfs/QmaSJUpdS9qzpbqPqqf49tnVuVCAFY4zPCEapse4HesQHf)

Then that would be everything, and the script knows what the bot is going to look for, here is a picture with the result of the tutorial we just made.

I do not add proof of work, because the same repository is our proof of work, which is associated with my heroku account. This was our first part of the tutorial, there are still many more functions to add to our bot so that one day it resembles Navi, but all to its calm.

Curriculum
This is my first Tutorial, but you can go through my [profile](https://steemit.com/@anonym0us) to see other publications of other categories approved by [@utopian](https://steemit.com/@utopian).
