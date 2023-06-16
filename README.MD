
# Zoom Meeting SDK JavaScript sample

Use of this sample app is subject to our [Terms of Use](https://explore.zoom.us/en/legal/zoom-api-license-and-tou/).

This repo contains an HTML/CSS/JavaScript website that utilizes the [Zoom Meeting SDK](https://developers.zoom.us/docs/meeting-sdk/web/) with a Node.js Express backend and the Chrome Headless browser to join Zoom meetings and request recording permission. The frontend is built with Vanilla JS to demonstrate the capabilities of headless browsers for bot development. It also serves as reference implementation for:

* Headless MeetingBot Join Meeting & Computer Audio Flow 
* Generate Metting SDK JWT Signature from the backend
* Zoom OAuth access token request
* Zoom REST API calls and retrieving user information
  * Get User Meeting Detail
  * Request permission as participant to record

Tech stack: js, node.js, express, docker (optional)

____

Requirements:
* Node
* Docker (optional)

____

## Installation

To get started, clone the repo : https://github.com/zoom/meetingsdk-web-bot-sample.git

## Setup

1. Once cloned, navigate to the meetingsdk-sample-javascript directory:

$ cd meetingsdk-web-bot-sample-javascript

2. Then install the dependencies:
```
$ npm install
```
3. Create an environment file to store your Meeting SDK credentials:

```
$ touch .env

```

4. In the frondend directory, open the client-view.js file, and enter values for the variables:


   | Variable                   | Description |
   | -----------------------|-------------|
   | authEndpoint          | Required, your Meeting SDK auth endpoint that secuerly generates a Meeting SDK JWT. [Get a Meeting SDK auth endpoint here.](https://github.com/zoom/meetingsdk-sample-signature-node.js) |
   | sdkKey                   | Required, your Zoom Meeting SDK Key or Client ID for Meeting SDK app type's created after February 11, 2023. [You can get yours here](https://developers.zoom.us/docs/meeting-sdk/developer-accounts/#get-meeting-sdk-credentials). |
   | meetingNumber                   | Required, the Zoom Meeting or webinar number. |
   | passWord                   | Optional, meeting password. Leave as empty string if the meeting does not require a password. |
   | role                   | Required, `0` to specify participant, `1` to specify host. |
   | userName                   | Required, a name for the user joining / starting the meeting / webinar. |
   | userEmail                   | Required for Webinar, optional for Meeting, required for meeting and webinar if [registration is required](https://support.zoom.us/hc/en-us/articles/360054446052-Managing-meeting-and-webinar-registration). The email of the user starting or joining the meeting / webinar. |
   | registrantToken            | Required if your [meeting](https://developers.zoom.us/docs/meeting-sdk/web/client-view/meetings/#join-meeting-with-registration-required) or [webinar](https://developers.zoom.us/docs/meeting-sdk/web/client-view/webinars/#join-webinar-with-registration-required) requires [registration](https://support.zoom.us/hc/en-us/articles/360054446052-Managing-meeting-and-webinar-registration). |
   | zakToken            | Required to start meetings or webinars on external Zoom user's behalf, the [authorized Zoom user's ZAK token](https://developers.zoom.us/docs/meeting-sdk/auth/#start-meetings-and-webinars-with-a-zoom-users-zak-token). |
   | leaveUrl                   | Required for Client View, the url the user is taken to once the meeting is over. |

   Example:

   ```js
   var authEndpoint = 'http://localhost:4000'
   var sdkKey = 'abc123'
   var meetingNumber = '123456789'
   var passWord = ''
   var role = 0
   var userName = 'Web Bot'
   var userEmail = ''
   var registrantToken = ''
   var leaveUrl = 'https://zoom.us'

   ```

6. Launch a development local Server or open index.html in your browser ([or serve over localhost](https://www.npmjs.com/package/http-server)). 


7. Start the server:


```
npm run start
```

## Usage

1. Navigate to index.html in your browser ([or serve over localhost](https://www.npmjs.com/package/http-server)) and click "Join Meeting".

2. Join Meeting Via Client

3. In terminal, run node : npm run start

4. Meeting Bot should enter Meeting

# Self-signed certificate 

With every launch on Mac OS, the Firewall setting causes mac os to ask the following question: "Do you want to the application Chromium.app to accept incoming network connections?" To resolve on Mac, you will need to self-signed certificate with following command: 

global chromium
```
sudo codesign --force --deep --sign - ~/Library/Caches/ms-playwright/chromium-*/chrome-mac/Chromium.app

```
Local project chromium

```
sudo codesign --force --deep --sign - ./node_modules/puppeteer/.local-chromium/mac-*/chrome-mac/Chromium.app

```

## Need help?

If you're looking for help, try [Developer Support](https://devsupport.zoom.us)   or our [Developer Forum](https://devforum.zoom.us). Priority support is also available with [Premier Developer Support](https://zoom.us/docs/en-us/developer-support-plans.html) plans.

