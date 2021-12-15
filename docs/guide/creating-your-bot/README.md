# Initial files

Once you [add your bot to a server](../preparations#next-steps), the next step is to start coding and get it online! Let's start by creating a config file for your client token and a main file for your bot application.

## Creating configuration files

Once again, DJS have written a [nice guide](https://discordjs.guide/creating-your-bot/#creating-configuration-files) on this topic. We recommend you to [use environment variables](https://discordjs.guide/creating-your-bot/#using-environment-variables) to store your config as it has less trouble with ESM nature of RuinGuard.

In this guide we will be using environment variables to store the config. But you may use any method which is compatible with ESM.

Suppose your config is this:

```sh
A=123
B=456
DISCORD_TOKEN=your-token-goes-here
```

This is how you should use:

```javascript
import { config as ENV } from "dotenv";
ENV();

console.log(process.env.A);
console.log(process.env.B);
console.log(process.env.DISCORD_TOKEN);
```

## Creating the main file

Open your code editor and create a new file. We suggest that you save the file as `index.js`, but you may name it whatever you wish.

In this guide we will also import RuinGuard essentials module. Which provides you with a ping slash command. Here's the base code to get you started:

```javascript
// Import necessary classes
import { Bot } from "@ruinguard/core";
import essentials from "@ruinguard/essentials";
import { config as ENV } from "dotenv";
ENV();

// Create a new Bot instance
const bot = new Bot({

  // Import modules
  modules: [essentials]
});

// Login to Discord with your client's token
await bot.login(process.env.TOKEN);
```

This is how you create a bot using RuinGuard.

Open your terminal and run `node index.js` to start the process. If you see "Ready!" after a few seconds, you're good to go!

Check out the ping command in your discord server by typing `/ping`.
