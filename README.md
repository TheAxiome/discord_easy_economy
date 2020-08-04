# Package Info

This package has just released, more updates soon!

# Useful Links

- [Github issues](https://github.com/TheAxiome/discord_easy_economy/issues)

- My [Discord server](https://discord.gg/agnpBXA)

# Usage
`npm i discord_easy_economy`

```javaScript
const Discord = require('discord.js')
const client = new Discord.Client()

const { EconomyBot } = require('discord_easy_economy')
const eco = new EconomyBot()

client.on('ready', () => {
    console.log(`${client.user.tag} is now online!`)
})

client.on('message', async message => {
    eco.defaultValue(message, "Money", 10)

    if (message.content ==='!beg') {
        message.channel.send(`You begged for $20`)
        eco.addValue(message.author, "Money", 20)
    }
    if (message.content === `!subtract`) {
        message.channel.send(`I took away $20`)
        eco.subtractValue(message.author, "Money", 20)
    }
    if (message.content === `!bal`) {
        const user = message.mentions.users.first() || message.author
        const bal = await eco.fetchValue(user, "Money")
        message.channel.send(`Your bal is ${bal}!`)

    }
    if (message.content === `!daily`) {
        eco.timeValue(message, "Money", 86400000, 200)//message value, economy value, ms time to wait, amount to add
    }
})

client.login('TOKEN')
```

# Values/Syntax
**If you do not understand, or do not want to change values, copy from the example above!**

Note: You can have multiple economy values, it dosent have to be `Money` and it dosent have to be just 1 value.

```
defaultValue(message, input, value)
```
```css
Give a default amount of money to anyone, with any money value you have!

Replace "message" with your message value
Replace "input" with the name of the economy value you are using
Replace "value" with the default amount of money you want to give
```

```
addValue(message, input, value)
```
```css
Add an amount to your economy value

Replace "message" with your message value
Replace "input" with the name of the economy value you are using
Replace "value" with the amount of money you want to give
```

```
subtractValue(message, input, value)
```
```css
Add an amount to your economy value

Replace "message" with your message value
Replace "input" with the name of the economy value you are using
Replace "value" with the amount of money you want to subtract
```

```
fetchValue(user, input)
```
```css
Fetch the amount someone has for an economy value

Replace "user" with the preson you are fetching values for
Replace "input" with the economy value
```

```
timeValue(message, input, timeout, value)
```
```css
Create hourly, daily, weekly, monthly or any other timed based economy commands!

Replace "message" with your message value
Replace "input" with your economy value
Replace "timeout" with the ms time someone needs to wait, before using the command again
Replace "value" with the amount you want to give!
```

More values coming soon!
