# Global Bans API

<h4>Discord.js Implementation</h4>
<code>const Discord = require('discord.js');
const client = new Discord.Client();
const request = require('request');

const token = 'TOKEN';
const site = 'http://172.93.101.204:3000' // Temporary address for the API.

client.on('ready', () => {
    console.log(`Logged in as ${client.user.tag}!`);
});

client.on('message', message => {
    let prefix = '!'
    let args = message.content.slice(prefix.length).trim().split(' ');

    if (message.content.toLocaleLowerCase().startsWith(prefix + "isbanned")) {
        let id = args[1];
        if (id) {
            request(`${site}/users/${id}`, function (error, response, body) {
                let parsed = JSON.parse(body);
                if (parsed[0] === 'Invalid Request') return message.channel.send("User is **not** banned!");
                message.channel.send(`User **is** banned. Reason: \`\`${parsed[0].Reason}\`\``);
                // More ban info is also available: Id, timestamp, UserId, Reason
            });
        } else {
            message.reply(":x: Please specify a user!");
        }
    }
});

client.login(token);</code>
