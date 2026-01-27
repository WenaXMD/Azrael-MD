[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&pause=200&color=00FF41&multiline=true&width=600&height=140&lines=101001011010010110100101;010110100101101001011010;110100101101001011010010;ACCESSING+WenaXMD...;ACCESS+GRANTED)](https://git.io/typing-svg)
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
