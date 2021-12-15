# Creating Commands

Discord allows developers to register [slash commands](https://discord.com/developers/docs/interactions/application-commands), which provide users a first-class way of interacting directly with your application. Before being able to reply to a command, you must first register it.

## Registering Commands

### Command deployment script

Create a `deploy-commands.js` file in your project directory. This file will be used to register & update the slash commands for your Discord Bot.

```javascript
import { Module } from '@ruinguard/core';
import essentials from '@ruinguard/essentials';
import { config as ENV } from 'dotenv';
ENV();

await Module.registerGuildCommands([essentials], {
  app: process.env.CLIENTID,
  guild: process.env.GUILDID
  token: process.env.TOKEN,
}).then(console.log);
```

### Command Handling

Since the speciality of RuinGuard is modularity, we will need another script which will act as command importer.<br>
This command importer will then be imported as a module. This will make things a bit easy in long run.<br>

Else it would be a hassle to import all individual commands one by one.

Create a file named `CommandIndex.js` with the following code:

```javascript
import { Module } from "@ruinguard/core";
import { getDir } from "file-ez";

export default await new Module({
  commands: getDir("./commands").path,
  intents: [1 << 0]
});
```

This script will now automatically import all commands into itself acting as a module.

Import this module into `deploy-commands.js` file.

After changes it should look like this: <!-- ```js hl_lines=" 3 7" -->

```javascript hl_lines="3 7"
import { Module } from '@ruinguard/core';
import essentials from '@ruinguard/essentials';
import commands from "./CommandIndex.js";
import { config as ENV } from 'dotenv';
ENV();

await Module.registerGuildCommands([essentials, commands], {
  app: process.env.CLIENTID,
  guild: process.env.GUILDID
  token: process.env.TOKEN,
}).then(console.log);
```

## Making commands

Now to add your commands, create a folder named `commands`.

Making a command follows exactly same structure as given [here](https://discord.com/developers/docs/interactions/application-commands).

In the examples, a json object is created.

But in Ruinguard you make JS objects & pass it to the command function.

!!! tip
    Its a good practice to keep command names as the file names. Avoids confusion.

Let's start by making 2 simple commands.

### Server info Command

Note that servers are referred to as "guilds" in the Discord API and discord.js library. `interaction.guild` refers to the guild the interaction was sent in (a [`Guild`](https://discord.js.org/#/docs/main/stable/class/Guild) instance), which exposes properties such as `.name` or `.memberCount`.

So create a file named `server-info.js` with the following code:

```js
import {command} from '@ruinguard/core';

export default new Command({
  data: {
    name: "server-info",
    description: "Tells info about server",
  },

  async run(interaction){
    return interaction.reply(`Server name: ${interaction.guild.name}\nTotal members: ${interaction.guild.memberCount}`);
  }
})
```

You could also display the date the server was created, or the server's verification level. You would do those in the same manner–use `interaction.guild.createdAt` or `interaction.guild.verificationLevel`, respectively.

!!! tip
    Refer to the [Guild](https://discord.js.org/#/docs/main/stable/class/Guild) documentation for a list of all the available properties and methods!

#### User info Command

A "user" refers to a Discord user. `interaction.user` refers to the user the interaction was sent by (a [`User`](https://discord.js.org/#/docs/main/stable/class/User) instance), which exposes properties such as `.tag` or `.id`.

Create a new file called `user-info.js` with the following code:

```js
import {command} from '@ruinguard/core';

export default new Command({
  data: {
    name: "user-info",
    description: "Tells info about user",
  },

  async run(interaction){
    return interaction.reply(`Your tag: ${interaction.user.tag}\nYour id: ${interaction.user.id}`);
  }
})
```
