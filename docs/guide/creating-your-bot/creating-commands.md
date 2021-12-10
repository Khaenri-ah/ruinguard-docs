# Creating Commands

```js
import { Module } from '@ruinguard/core';
import essentials from '@ruinguard/essentials';
import moderation from '@ruinguard/moderation';
import { config as ENV } from 'dotenv';
ENV();

await Module.registerGuildCommands([essentials, moderation], {
  app: process.env.CLIENTID,
  guild: process.env.GUILDID
  token: process.env.TOKEN,
}).then(console.log);
```
