# Bot
**extends [Client][]**

The main bot class.

## Constructor
```js
new Bot(options);
```

| PARAMETER | TYPE                        | DESCRIPTION         |
| :-------: | :-------------------------: | :-----------------: |
| options   | [BotOptions](BotOptions.md) | Options for the bot |

## Properties

### `.commands` { data-toc-label='commandss' }
All commands currently loaded

**Type: [CommandManager]**

### `.embeds` { data-toc-label='embeds' }
The EmbedFactory of this bot

**Type: [EmbedFactory]**


### `.modules` { data-toc-label='modules' }
The modules this bot loaded with

**Type: [Array]&lt;[Module]&gt;**

### `.owners` { data-toc-label='owners' }
The owners of the bot

**Type: [Array]&lt;String&gt;**

## Methods

### `._onInteractionCreate(interaction)` { data-toc-label='_onInteractionCreate' }
The default interaction handler, you may need to explicitely call this if you add your own listeners on the `interactionCreate` event

**Returns: [Promise]&lt;([Message][]|[APIMessage])&gt;**

**Examples:**
```js
// custom interactionCreate hook
bot.on('interactionCreate', interaction => {
  console.log('Interaction received!');
  // call default handler
  interaction.client._onInteractionCreate(interaction);
});
```



[Module]: Module.md
[CommandManager]: CommandManager.md
[EmbedFactory]: EmbedFactory.md

[Client]: https://discord.js.org/#/docs/main/stable/class/Client
[Message]: https://discord.js.org/#/docs/main/stable/class/Message

[APIMessage]: https://discord.com/developers/docs/resources/channel#message-object

[Promise]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
[Array]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array
[String]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String