const Discord = require("discord.js")
const Bot = new Discord.Client()
var prefix = "!"
 
const Webhook = require("webhook-discord")
const Hook = new Webhook("YOUR WEBHOOK URL")
 
Bot.on("ready", () => {
    Hook.success(Bot.user.username,"Bot is online and ready in "+Bot.guilds.size+" servers")
})
 
Bot.on("message", (msg) => {
 
    if(msg.content.startsWith(prefix + "ping")){
    Hook.info(Bot.user.username, msg.author.username + " executed "+msg.cleanContent+" in "+msg.guild.name)
}
 
})
 
Bot.on("error",(e) => {
Hook.error(Bot.user.username, e)
})
 
Bot.on("warn",(w) => {
    Hook.warn(Bot.user.username,"Warning: `"+w+"`")
})
 
Bot.login("token").then(() => {
    Hook.info("Bot Daemon","Logged in")
})
