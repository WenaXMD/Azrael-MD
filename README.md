<svg width="300" height="300" viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="grad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="#00ff41"/>
      <stop offset="50%" stop-color="#00b3ff"/>
      <stop offset="100%" stop-color="#b400ff"/>
    </linearGradient>
  </defs>

  <!-- Dragon swirl body -->
  <path d="M150 40
           C 220 40, 260 120, 200 160
           C 170 180, 160 200, 190 230
           C 140 220, 120 180, 140 150
           C 90 160, 60 130, 80 100
           C 100 70, 130 70, 150 90"
        fill="none"
        stroke="url(#grad)"
        stroke-width="8"
        stroke-linecap="round"/>

  <!-- Head -->
  <circle cx="155" cy="85" r="6" fill="#00ff41"/>

  <!-- Eye -->
  <circle cx="157" cy="83" r="2" fill="black"/>

  <!-- Binary accents -->
  <text x="40" y="280" font-family="monospace" font-size="18" fill="#00ff41">
    01001011 01000001 01001100 01001001
  </text>
</svg>

📁 GitHub Repo Structure:
```
whatsapp-bot/
├── .env
├── index.js
├── package.json
```

---

📦 package.json
```json
{
  "name": "whatsapp-bot",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "twilio": "^4.3.0",
    "dotenv": "^16.0.3"
  }
}
```

---

⚙️ .env (Keep secret)
```
TWILIO_AUTH_TOKEN=your_auth_token
TWILIO_ACCOUNT_SID=your_account_sid
```

---

🧠 index.js (Core Bot Logic)
```js
require('dotenv').config();
const express = require('express');
const { MessagingResponse } = require('twilio').twiml;

const app = express();
app.use(express.urlencoded({ extended: false }));

app.post('/webhook', (req, res) => {
  const twiml = new MessagingResponse();
  const incomingMsg = req.body.Body || '';

  let reply = 'Hello! This is Wena AutoBot.';
  if (incomingMsg.toLowerCase().includes('hello')) {
    reply = 'Hi there! How can I assist you today?';
  } else if (incomingMsg.toLowerCase().includes('quote')) {
    reply = '“Success is not final; failure is not fatal.”';
  

  twiml.message(reply);
