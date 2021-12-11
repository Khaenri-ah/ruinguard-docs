# Bot

**extends [Client]**

The main bot class.

## Constructor

```javascript
new Bot(options);
```

PARAMETER |     TYPE     |     DESCRIPTION
:-------: | :----------: | :-----------------:
 options  | [BotOptions] | Options for the bot

## Properties

### `.commands` { data-toc-label='commands' }

All commands currently loaded

**Type: [CommandManager]**

### `.embeds` { data-toc-label='embeds' }

The EmbedFactory of this bot

**Type: [EmbedFactory]**

### `.modules` { data-toc-label='modules' }

The modules this bot loaded with

**Type: [Array]<[Module]>**

### `.owners` { data-toc-label='owners' }

The owners of the bot

**Type: [Array]<[String]>**

## Methods

### `._onInteractionCreate(interaction)` { data-toc-label='_onInteractionCreate' }

The default interaction handler, you may need to explicitely call this if you add your own listeners on the `interactionCreate` event, but want the default command handling to work regardless.

 PARAMETER  |     TYPE      |          DESCRIPTION
:---------: | :-----------: | :---------------------------:
interaction | [Interaction] | The interaction to be handled

**Returns: [Promise]<([Message]|[APIMessage]|_undefined_)>**

**Examples:**

```javascript
// custom interactionCreate hook
bot.on('interactionCreate', interaction => {
  console.log('Interaction received!');
  // call default handler
  interaction.client._onInteractionCreate(interaction);
});
```

[apimessage]: https://discord.com/developers/docs/resources/channel#message-object
[array]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array
[botoptions]: ../types/BotOptions.md
[client]: https://discord.js.org/#/docs/main/stable/class/Client
[commandmanager]: CommandManager.md
[embedfactory]: EmbedFactory.md
[interaction]: https://discord.js.org/#/docs/main/stable/class/Interaction
[message]: https://discord.js.org/#/docs/main/stable/class/Message
[module]: Module.md
[promise]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
[string]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String
