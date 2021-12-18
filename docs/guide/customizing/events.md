# Events

## Creating a custom module

If you haven't created a custom module yet, read how to do so [here][custom-cmd]. This page will assume you have already added a module with custom commands.

## Adding events

Create a folder called `events`, and add a file called `guildAdd.js` with the following code:

```javascript title="events/guildAdd.js"
import { Event } from '@ruinguard/core';

export default new Event({
  event: 'guildAdd',

  run(guild) {
    console.log(`+ ${guild.name} (${guild.id})`);
  }
});
```

Now add this event to your module:

=== "using file-ez"

    ```javascript title="module.js" hl_lines="6"
    import { Module, Intents } from '@ruinguard/core';
    import { getDir } from 'file-ez';

    export default await new Module({
      commands: getDir('./commands').path,
      events: getDir('./events').path,
      intents: [Intents.FLAGS.GUILDS],
    });
    ```

=== "using imports"

    ```javascript title="module.js" hl_lines="3 7"
    import { Module, Intents } from '@ruinguard/core';
    import serverInfo from './commands/server-info.js';
    import onGuildAdd from './events/guildAdd.js';

    export default await new Module({
      commands: [serverInfo],
      events: [onGuildAdd],
      intents: [Intents.FLAGS.GUILDS],
    });
    ```

Check the [discord.js documentation][djs-events] for all the available events.

For events also you can use [dynamic imports][dynamic-import]

## Project Directory

If you are following correctly till now, the project directory should look like this:

```bash
discord-bot/
├── node_modules
├── commands/
│   ├── server-info.js
│   └── user-info.js
├── events/
│   └── guildAdd.js    
├── index.js
├── module.js
├── register.js
├── package-lock.json
└── package.json
```

[custom-cmd]: commands.md#creating-a-custom-module

[djs-events]: https://discord.js.org/#/docs/main/stable/class/Client

[dynamic-import]: commands.md#dynamically-adding-commands
