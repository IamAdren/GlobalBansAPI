# Global Bans API

<h4>Discord.js Implementation</h4>

```javascript
const Discord = require('discord.js');
const client = new Discord.Client();
const request = require('request');

const token = 'TOKEN';
const site = 'http://172.93.101.204:3000' // Temporary address for the API.

client.on('ready', () => {
    console.log(`Logged in as ${client.user.tag}!`);
});
```
