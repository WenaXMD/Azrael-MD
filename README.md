
---[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&pause=150&color=FF0000&multiline=true&width=650&height=160&lines=101011001010110010101100;010100110101001101010011;RGB+SIGNAL+DETECTED...;ACCESSING+WenaXMD+SYSTEM...)](https://git.io/typing-svg)

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&pause=150&color=00FF00&multiline=true&width=650&height=160&lines=110010101100101011001010;001101010011010100110101;SYNCING+RGB+CHANNELS...;ACCESS+GRANTED)](https://git.io/typing-svg)

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&pause=150&color=00BFFF&multiline=true&width=650&height=160&lines=101010101010101010101010;010101010101010101010101;SYSTEM+OVERRIDE...;WELCOME+OPERATOR)](https://git.io/typing-svg)

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
