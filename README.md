# discord-example
What Will I Learn?
you will learn how to create a super simple discord bot and keep it connected to your discord server 24/7 for free.

Requirements
a Discord Account.
a GitHub Account.
a Heroku Account.
Difficulty
Basic.
Tutorial Contents
Creating your Bot on Discord:

Open the following link and login using your discord account: https://discordapp.com/developers/applications/me

Create a New Application.

U5dstok2nEdDdkYqmieZdfGAMMjktSG_1680x8400.png

Follow this instruction and Create a new application - Name Your App, Select an Avatar/Icon, and click "Create App."

2.png

Once the App is created, select it and Click on "Create a Bot User." Confirm and Choose "Yes. Do It!" on the box that pops up.

3.png

Make sure to take Note of the Client ID and Token. You will need these later when you begin programming your bot. Do not share this information!

Next you need to invite the Bot to your Discord Server using the following link:
https://discordapp.com/oauth2/authorize?&client_id=YOUR_CLIENT_ID_HERE&scope=bot&permissions=0

Replace YOUR_CLIENT_ID_HERE with the Client ID from your created Bot.

For a detailed walkthrough of this section, you can follow the following link:
https://github.com/reactiflux/discord-irc/wiki/Creating-a-discord-bot-&-getting-a-token

creating the script

Go with the following link to GitHub to create the repository: https://github.com/new

Then we will create 3 scripts within that repository, which are these three
github1.png

bot.js

const Discord = require('discord.js');

const client = new Discord.Client();

 

client.on('ready', () => {

    console.log('I am ready!');

});

 

client.on('message', message => {

    if (message.content === 'ping') {

       message.reply('pong');

       }

});

 

// THIS  MUST  BE  THIS  WAY

client.login(process.env.BOT_TOKEN);//where BOT_TOKEN is the token of our bot
package.json

{

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
Procfile

worker: node bot.js
the scripts should appear like thisimagenGithub.png

Note: if when copying the files or finishing the entire tutorial you have an error, try copying directly the GitHub script: https://github.com/Carlososuna11/discord-example

Uploading the Script to Heroku:
descarga.png

Heroku is a platform as a cloud computing service that supports different programming languages.

we will take advantage of that Heroku service to keep our bot activated

we will create a new board where the script will be uploaded here the link: https://dashboard.heroku.com/apps

heroku2.png

let's go to the resources section and select github

![herokux.png](

Here we select our GitHub repository
we will select enable automatic desploy

deployx.png

now we have to select what script we are going to work on, for that we go to resources and in free dynos we deselect the web and activate the worker

image.png

and our script would be online and working, but now we need to tell the script which bot is the one that is going to be linked to the script, that's why we go for settings

then we will find an option called config variables,
add a new variable whose key will be BOT_TOKEN and the value of that variable will be the token of our bot

settings.png

then that would be everything, and the script knows what the bot is going to look for, here is a picture with the result of the tutorial we just made
ping.png

and that would be all friends, the possibilities are endless when creating a discord bot, I will show you, a tutorial at the same time!

Curriculum
This is my first project.
