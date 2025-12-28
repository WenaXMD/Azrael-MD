[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1000&background=FFD85600&width=435&lines=Welcome+%F0%9F%98%8A+to+wena+tech+)](https://git.io/typing-svg)  # Azrael-MD
*Wena-Tech Auto Reply Bot* – A Node.js-based smart auto-responder designed to handle chat interactions, provide system info, quick replies, and personalized features. Integrates with platforms like WhatsApp using Heroku and webhook APIs.

---

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
