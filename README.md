
[![Typing SVG](https://readme-typing-svg.demolab.com?font=Rubik+Storm&pause=1000&color=F70000&background=000000&multiline=true&width=435&lines=%60%60%60+%F0%9F%93%8A+SYSTEM+STATUS+++-+%F0%9F%9F%A2+Server+Uptime%3A+100%25+++-+%F0%9F%94%84+CPU+Load%3A+41%25+++-+%F0%9F%92%BE+Memory+Usage%3A+2.3+GB+%2F+4+GB+++-+%F0%9F%94%90+Firewall%3A+Active+++-+%F0%9F%93%A1+Connection%3A+Stable++++%F0%9F%91%A4+YOUR+PROFILE+++-+Name%3A+%7Bname!%7D+++-+ID%3A+WENA-00123+++-+Member+Since%3A+Jan+2024+++-+Current+Plan%3A+Premium+++-+Last+Login%3A+Today++%F0%9F%92%B0+ACCOUNT+BALANCE+++-+Wallet+Balance%3A+KES+420.00+++-+Points%3A+135+++-+Last+Transaction%3A+%2BKES+200+(Top-up)+++-+Billing+Method%3A+M-Pesa+++-+Renewal%3A+Auto-renew+enabled+%60%60%60+1.+Previous+Menu+0.+Main+Menu)](https://git.io/typing-svg)

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
