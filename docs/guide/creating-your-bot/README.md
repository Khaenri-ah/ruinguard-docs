# Initial files

## Creating the main file

Open your code editor and create a new file. We suggest that you save the file as `index.js`, but you may name it whatever you wish.

Here's the base code to get you started:

```javascript
// Import necessary classes
import { Bot } from "@ruinguard/core";
import essentials from "@ruinguard/essentials";
import { config as ENV } from "dotenv";
ENV();

// Create a new Bot instance
const bot = new Bot({

  // Import modules
  modules: [essentials]
});

// Login to Discord with your client's token
await bot.login(process.env.TOKEN);
```

This is how you create a bot using RuinGuard.

Open your terminal and run `node index.js` to start the process. If you see "Ready!" after a few seconds, you're good to go!
