# BotOptions

Options for a bot.

## Types

- [ClientOptions]

Parameter |         Type          |         Optional          | Default |                Description
:-------: | :-------------------: | :-----------------------: | :-----: | :----------------------------------------:
 modules  |   [Array]<[Module]>   | :fontawesome-solid-check: |  `[]`   |    The modules you want the bot to use
 embeds   | [EmbedFactoryOptions] | :fontawesome-solid-check: | _none_  | Options for the [EmbedFactory] of this bot
  owner   |       [String]        | :fontawesome-solid-check: | _none_  |    The owner of the bot, if there's one
 owners   |   [Array]<[String]>   | :fontawesome-solid-check: |  `[]`   | The owners of the bot, if there's multiple

[array]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array
[clientoptions]: https://discord.js.org/#/docs/main/stable/typedef/ClientOptions
[embedfactory]: ../classes/EmbedFactory.md
[embedfactoryoptions]: EmbedFactoryOptions.md
[module]: ../classes/Module.md
[string]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String
