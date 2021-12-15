# Initial files

Once you have added your bot to a server, the next step is to start coding and get it online! Let's start by creating a config file for your client token and a main file for your bot application.

## Creating configuration files

Once again, DJS have written a [nice guide][djs-config] on this topic. We recommend you to [use environment variables][djs-env] to store your config as it has less trouble with ESM nature of RuinGuard.

In this guide we will be using environment variables to store the config. But you may use any method you like.

Suppose your config is this:

```sh
A=123
B=456
DISCORD_TOKEN=your-token-goes-here
```

This is how you could use dotenv in an ESM module:

```javascript
import { config as ENV } from 'dotenv';
ENV();

console.log(process.env.A);             // outputs `123`
console.log(process.env.B);             // outputs `456`
console.log(process.env.DISCORD_TOKEN); // outputs `your-token-goes-here`
```

## Creating the main file

Open your code editor and create a new file. We suggest that you save the file as `index.js`, but you may name it whatever you wish.

The following code creates the most simple bot you can make:

```javascript
import { Bot } from '@ruinguard/core';
import { config as ENV } from 'dotenv';
ENV();

// Create a new Bot instance
const bot = new Bot();

// Login to Discord with your bot token
await bot.login(process.env.TOKEN);
```

This bot does not have any functionality however, let's fix that.

## Modules

RuinGuard works with modules, which all have their own commands, events, and configuration options.

For this first bot, let's keep it simple

TODO: show @ruinguard/essentials



[djs-config]: https://discordjs.guide/creating-your-bot/#creating-configuration-files
[djs-env]: https://discordjs.guide/creating-your-bot/#using-environment-variables