# Custom commands

You might want to create your own commands, instead of only using those from existing modules. This page will show you how you can make your own commands.

## Creating a custom module

To add custom commands, we'll need to create a module for them. Create a file named `module.js` (or whatever you want) and paste the following code into it:

```javascript title="module.js"
import { Module } from '@ruinguard/core';

export default await new Module();
```

Now add the module to your bot:

=== "index.js"

    ```javascript hl_lines="3 9"
    import { Bot } from '@ruinguard/core';
    import essentials from '@ruinguard/essentials';
    import custom from './module.js';
    import { config as ENV } from 'dotenv';
    ENV();

    // Create a new Bot instance
    const bot = new Bot({
      modules: [essentials, custom]
    });

    // Login to Discord with your bot token
    await bot.login(process.env.TOKEN);
    ```

=== "register.js"

    ```javascript hl_lines="3 7"
    import { Module } from '@ruinguard/core';
    import essentials from '@ruinguard/essentials';
    import custom from './module.js';
    import { config as ENV } from 'dotenv';
    ENV();

    await Module.registerGuildCommands([essentials, custom], {
      app: process.env.CLIENTID,
      guild: process.env.GUILDID,
      token: process.env.TOKEN,
    }).then(console.log);
    ```

## Adding commands

Now to add your commands, first create a folder named `commands`. In this folder, we're gonna create a sample command file `server-info.js` with the one of the following snippets of code:

=== "using a builder"
    !!! info "@discord.js/builders"
        Discord.js recommends using their builders, which can be installed with:

        ```sh
        npm install @discord.js/builders
        ```
    ```javascript title="commands/server-info.js"
    import { SlashCommandBuilder } from '@discordjs/builders';
    import {command} from '@ruinguard/core';

    export default new Command({
      data: new SlashCommandBuilder()
        .setName('server-info')
        .setDescription('Shows info about this server'),

      async run(interaction){
        return interaction.reply(`Server name: ${interaction.guild.name}\nTotal members: ${interaction.guild.memberCount}`);
      }
    });
    ```

=== "using an object"

    ```javascript title="commands/server-info.js"
    import {command} from '@ruinguard/core';

    export default new Command({
      data: {
        name: 'server-info',
        description: 'Shows info about this server',
      },

      async run(interaction){
        return interaction.reply(`Server name: ${interaction.guild.name}\nTotal members: ${interaction.guild.memberCount}`);
      }
    });
    ```

Now add this command to your module:

=== "using file-ez"
    !!! info "file-ez"
        RuinGuard uses `file-ez` for most file operations. You can explicitly install it with:

        ```sh
        npm install file-ez
        ```
    ```javascript title="module.js" hl_lines="1 2 4-7"
    import { Module, Intents } from '@ruinguard/core';
    import { getDir } from 'file-ez';

    export default await new Module({
      commands: getDir('./commands').path,
      intents: [Intents.FLAGS.GUILDS],
    });
    ```

=== "using imports"

    ```javascript title="module.js" hl_lines="1 2 4-7"
    import { Module, Intents } from '@ruinguard/core';
    import serverInfo from './commands/server-info.js';

    export default await new Module({
      commands: [serverInfo],
      intents: [Intents.FLAGS.GUILDS],
    });
    ```

Let's add another command which will tell user info. Create another file `user-info.js` with the following snippet of code:

=== "using a builder"
    !!! info "@discord.js/builders"
        Discord.js recommends using their builders, which can be installed with:

        ```sh
        npm install @discord.js/builders
        ```
    ```javascript title="commands/user-info.js"
    import { SlashCommandBuilder } from '@discordjs/builders';
    import { command } from '@ruinguard/core';

    export default new Command({
      data: new SlashCommandBuilder()
        .setName('user-info')
        .setDescription('Shows info about you!'),

      async run(interaction){
        return interaction.reply(`Your name: ${interaction.user.tag}\nYour ID: ${interaction.user.id}`);
      }
    });
    ```

=== "using an object"

    ```javascript title="commands/user-info.js"
    import { command } from '@ruinguard/core';

    export default new Command({
      data: {
        name: 'user-info',
        description: 'Shows info about you!',
      },

      async run(interaction){
        return interaction.reply(`Your name: ${interaction.user.tag}\nYour ID: ${interaction.user.id}`);
      }
    });
    ```

Now add this command to your module:

=== "using file-ez"
    !!! info
        There is no change in code because `getDir()` automatically scans the `commands` folder & adds them into the module.

    ```javascript title="module.js"
    import { Module, Intents } from '@ruinguard/core';
    import { getDir } from 'file-ez';

    export default await new Module({
      commands: getDir('./commands').path,
      intents: [Intents.FLAGS.GUILDS],
    });
    ```

=== "using imports"

    ```javascript title="module.js" hl_lines="3 6"
    import { Module, Intents } from '@ruinguard/core';
    import serverInfo from './commands/server-info.js';
    import userInfo from './commands/user-info.js';

    export default await new Module({
      commands: [serverInfo, userInfo],
      intents: [Intents.FLAGS.GUILDS],
    });
    ```

### Dynamically adding commands

If you have used `file-ez` method to add commands into your module, you must have noticed that there was no change to be done in `module.js`. Where as for `imports` method, you had to import all individual commands.

Both methods have their own pros & cons. `file-ez` takes care of importing all commands where as `imports` method gives you control over which commands to add into module.

For convenience use `file-ez` method of importing commands.

## Project Directory

If you are following correctly till now, the project directory should look like this:

```text
discord-bot/
├── node_modules
├── commands/
│  ├── server-info.js
│  └── user-info.js
├── index.js
├── module.js
├── register.js
├── package-lock.json
└── package.json
```

!!! info
    For RuinGuard module developers there won't be `index.js` or `register.js`

## More about slash commands

More info about slash commands can be found on the [discord.js guide][djs-cmds] or discord's [official documentation][dsc-cmds]

[djs-cmds]: https://discordjs.guide/interactions/registering-slash-commands.html#options

[dsc-cmds]: https://discord.com/developers/docs/interactions/application-commands
