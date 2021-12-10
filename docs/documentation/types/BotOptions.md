# BotOptions

Options for a bot.

## Types
- [ClientOptions :fontawesome-solid-external-link-alt:](https://discord.js.org/#/docs/main/stable/typedef/ClientOptions)

| Parameter | Type                    | Optional                  | Default | Description |
| :-------: | :---------------------: | :-----------------------: | :-----: | :---------: |
| modules   | [Array]&lt;[Module]&gt; | :fontawesome-solid-check: | `[]`    | The modules you want the bot to use |
| embeds    | [EmbedFactoryOptions]   | :fontawesome-solid-check: | *none*  | Options for the [EmbedFactory] of this bot |
| owner     | [String]                | :fontawesome-solid-check: | *none*  | The owner of the bot, if there's one |
| owners    | [Array]&lt;[String]&gt; | :fontawesome-solid-check: | `[]`    | The owners of the bot, if there's multiple |



[Module]: ../classes/Module.md
[EmbedFactory]: ../classes/EmbedFactory.md
[EmbedFactoryOptions]: EmbedFactoryOptions.md

[Array]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array
[String]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String