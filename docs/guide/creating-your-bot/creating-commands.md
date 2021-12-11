# Creating Commands

Creating command follows exactly same structure as given [here](https://discord.com/developers/docs/interactions/application-commands).

In the examples, a json object is created.

But in Ruinguard you make JS objects & pass it to the command function.

For example, referring to this sample [code](https://discord.com/developers/docs/interactions/application-commands#making-a-global-command) (See the `json = {` part)

```javascript
import { Command } from "@ruinguard/core";

export default new Command({
  data: {
    name: "blep",
    type: 1,
    description: "Send a random adorable animal photo",
    options: [
        {
            name: "animal",
            description: "The type of animal",
            type: 3,
            required: True,
            choices: [
                {
                    name: "Dog",
                    value: "animal_dog"
                },
                {
                    name: "Cat",
                    value: "animal_cat"
                },
                {
                    name: "Penguin",
                    value: "animal_penguin"
                }
            ]
        },
        {
            name: "only_smol",
            description: "Whether to show only baby animals",
            type: 5,
            required: False
        }
    ]
}

async run(interaction){
  // The code to be executed when a particular command is selected by `interaction.user`
}
})
```

## Registering Commands

### Command deployment script

Create a `deploy-commands.js` file in your project directory. This file will be used to register & update the slash commands for your Discord Bot.

```javascript
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
