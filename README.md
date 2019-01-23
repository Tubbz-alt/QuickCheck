# QC QuickCheck

* Webex Teams Bot to perform Quick Check of Cisco CE endpoints *

---

## Motivation

There are many fine tools for managing Cisco Video Endpoints that do so much more than **QuickCheck**.  But, on occasion, you get a call saying "All the video units are down." Are they?  Are they ALL down or just some of them?  With QuickCheck, you could query the QC bot in a webex teams space with "QC getStatus" and the bot would query the status of every video unit you manage and respond with a quick, concise report right back to you in the same Webex Teams space. Maybe follow that with "QC getDiags" to see a report of current Diagnostic Alerts generated by each of your managed endpoints.  Quick and Simple with valuable results.

## Show Me!

Are all my endpoints running the same code?  Use QuickCheck!

You1:23 PM
QC getVersion

QC1:23 PM
Cisco Berry Farms at Kellers DX70 on webex sandbox at home office is:
	 ce9.7.0 54ac0f80a97 2018-12-19
MX800 Test at Kellers MX800 on webex sandbox at home office is:
	 ce9.7.0 54ac0f80a97 2018-12-19

## Features

### Welcome to QuickCheck ###

Here are the actions supported by QuickCheck:
- **help** - This help menu
- **list** - print endpoints from [endpoints.json](./endpoints.json) list.
- **getStatus** - Currently provides Standby Status.
- **getDiags** - List any diagnostic alerts.
- **getVersion** - List current software version.
- **sipStatus** - List SIP registration Status.
- **getLoss** - List Packet Loss values.
- **getLast** - List Last Call Details.
- **getPeople** - List number of people in room.

## Technologies & Frameworks Used

This is Cisco Sample Code!  What Cisco and third-party technologies are you working with?  Are you using a coding framework or software stack?  A simple list will set the context for your project.

**Cisco Products & Services:**

- This Cisco Webex Teams bot uses Webex Teams API to send/receive JSON formatted webhooks.  The bot also sends/receives XML formatted xAPI commands to/from Cisco CE code based Video Endpoints.


**Third-Party Products & Services:**

- Product
- Service

**Tools & Frameworks:**

- Framework 1
- Automation Tool 2

## Usage

If people like your project, they will want to use it.  Show them how.

## Installation

This code is written for **Python 3**... if you have a Mac, it comes with **Python 2**... you will need to upgrade to Python 3 or do a whole lot of changes to many of the methods for it to work.

### Pre-Requisites for QuickCheck ###
  - Create a webex teams bot - I created QC@webex.bot starting from the "How to create a webex teams bot (using python)":
  https://developer.webex.com/blog/spark-bot-demo
  - Invite your bot to a webex teams space or 1-1 direct space.
  - Create a webex teams webhook that will listen for messages to your bot and forward them to a public address for your bot handling app.(this app)
    HowTo:
  - Get an account on ngrok which gives you a tunnel from ngrok to your laptop and a public address at ngrok for your webhook to send http messages to.  *** ngrok is sometimes considered a security risk by corporate security services, so check with IT before loading ngrok client on your laptop.
    - Launch ngrok client on laptop
- Edit endpoints.json file to include endpoints you want to manage.
- Edit config.json with your names and bearer tokens
- Run main.py from terminal on laptop
    main.py will
      - launch local HTTP server on port 10010
        (You can change port number in config.json)
      - check your local ngrok client and get public uri
      - edit your webex teams webhook with current ngrok target
     - HTTP server will then wait for incoming webhooks and send them to the intent method for action.

## Useful links
- **Edit Webex Teams Webhook:**  https://developer.webex.com/my-apps/
- **How to Create a Webex Teams Bot**  https://developer.webex.com/blog/spark-bot-demo
- **ngrok dashboard**  https://dashboard.ngrok.com/status



## Authors & Maintainers

People responsible for the creation and maintenance of this project:

- Keller McBride <kelmcbri@cisco.com>
- Trey George <ergeorge@cisco.com>
- Joe Bourne <jbourne@cisco.com>

## Credits

The HTTP server code and the send get/post to webex teams methods were inspired by the code in the "How to create a webex teams bot" tutorial at:  https://developer.webex.com/blog/spark-bot-demo
The original python 2 code for this tutorial can be found at "tahanson's" repository at https://github.com/webex/SparkBotDemo/blob/master/bot_demo.py


We pulled from Steve Sfartz Postman Collection Github Repository at https://github.com/CiscoDevNet/postman-xapi to create actions/intents, i.e. commands you can execute with QuickCheck bot.

## License

This project is licensed to you under the terms of the [Cisco Sample
Code License](./LICENSE).
