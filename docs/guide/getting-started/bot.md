# Creating your bot

Once you have added your bot to a server, the next step is to start coding and get it online! Let's start by creating a config file for your client token and a main file for your bot application.

## Creating configuration files

Once again, DJS have written a [nice guide][djs-config] on this topic. We recommend you to [use environment variables][djs-env] to store your config.

In this guide we will be using environment variables to store the config, but you may use any method you like.

Our config will look like this:

```sh title=".env"
TOKEN=your-token-goes-here  # put your own bot token here
CLIENTID=0123456789         # put the ID of your bot here
GUILDID=0123456789          # put the ID of your test server here
```

This is how you could use dotenv in an ESM module:

```javascript
import { config as ENV } from 'dotenv';
ENV();

console.log(process.env.GUILDID);        // outputs your guild ID
console.log(process.env.CLIENTID);       // outputs bot's client ID
console.log(process.env.TOKEN);          // outputs bot's token ID
```

## Creating the main file

Open your code editor and create a new file. We suggest that you save the file as `index.js`, but you may name it whatever you wish.

The following code creates the most simple bot you can make:

```javascript title="index.js"
import { Bot } from '@ruinguard/core';
import { config as ENV } from 'dotenv';
ENV();

// Create a new Bot instance
const bot = new Bot();

// Login to Discord with your bot token
await bot.login(process.env.TOKEN);
```

If you run `node index.js` in your console, the bot should show as online, but it doesn't do anything yet. Let's fix that.

## Modules

RuinGuard works with modules, which all have their own commands, events, and configuration options.

Let's add a module to your bot.

### Adding a module

Modules need to be installed with npm, just like the core module, here we're going to install the `essentials` module, which contains basic things like a ping command and a message that gets printed to the console once the bot has started up.

```sh
npm install @ruinguard/essentials
```

!!! tip
    All modules starting with `@ruinguard/` are official modules, but you can also use 3rd party modules.

Now we need to add the module to the bot:

```javascript title="index.js" hl_lines="2 7-9"
import { Bot } from '@ruinguard/core';
import essentials from '@ruinguard/essentials';
import { config as ENV } from 'dotenv';
ENV();

// Create a new Bot instance
const bot = new Bot({
  modules: [essentials]
});

// Login to Discord with your bot token
await bot.login(process.env.TOKEN);
```

If you run `node index.js` now, you should see it print `ready!` to the console.

But where are the commands?

### Registering commands

Slash commands don't just show up once you start your bot, you need to register them.

Luckily, this is just as easy as getting a bot running, let's make a file called `register.js` and add the following code to it:

```javascript title="register.js"
import { Module } from '@ruinguard/core';
import essentials from '@ruinguard/essentials';
import { config as ENV } from 'dotenv';
ENV();

await Module.registerGuildCommands([essentials], {
  app: process.env.CLIENTID,
  guild: process.env.GUILDID,
  token: process.env.TOKEN,
}).then(console.log);
```

After running this script, you should see some commands appear in your server. Start the bot again and run one of the commands. Congratulation, You have made a working bot with RuinGuard!

!!! note "Global & Guild commands"
    In this code snippet, we are registering commands to server. During development, its advised to register it as guild commands as commands get refreshed instantly.
    Once the bot is ready to go public, then you can register the commands globally.  

    ```diff
    - await Module.registerGuildCommands([essentials], {
    + await Module.registerCommands([essentials], {
    ```

!!! note "Deleting commands"
    You might find your self in a situation to delete all commands. For that just pass an empty array to register commands. It will delete them all.

    ```js
    await Module.registerGuildCommands([], {
      // rest of the code
    })
    ```

If you are following correctly till now, the project directory should look like this:

```text
discord-bot/
├── node_modules
├── .env
├── index.js
├── register.js
├── package-lock.json
└── package.json
```

[djs-config]: https://discordjs.guide/creating-your-bot/#creating-configuration-files

[djs-env]: https://discordjs.guide/creating-your-bot/#using-environment-variables
