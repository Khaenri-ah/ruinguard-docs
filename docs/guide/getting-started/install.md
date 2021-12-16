# Preparations

## Installing Node.js

To use RuinGuard, you'll need to install [Node.js][node]. RuinGuard is built on [Discord.js][djs], which requires Node v16.6.0 or higher.

To check if you already have Node installed on your machine, run `node -v` in your terminal. If it outputs `v16.6.0` or higher, then you're good to go! Otherwise, install a version that's new enough from [the Node.js website][node-dwn] or your package manager.

## Creating a project folder

Navigate to a suitable place on your machine and create a new folder named `discord-bot` (or whatever you want). Then, open a terminal window and navigate to that folder.

!!! tip
    We recommend you to name the folder same as the Bot/Module. Even better if a Git repository is created for the same purpose.

To turn your folder into a Node.js project, run the following command:

```sh
npm init esm
```

This command creates a `package.json` file for you, which will keep track of the dependencies your project uses, as well as other info.

This command will ask you a sequence of questions–you should fill them out as you see fit. If you're not sure of something or want to skip it as a whole, leave it blank and press enter.

!!! tip
    To get started quickly, you can run the following command to have it fill out everything for you. Works best if the command is run inside a Git repository or similar.

    ```sh
    npm init esm -y
    ```

## Installing RuinGuard

Run the following command in your terminal:

```sh
npm install @ruinguard/core
```

This will install the core of RuinGuard, as well as its dependencies.

And that's it! With all the necessities installed, you're almost ready to start coding your bot/module.

If you are following correctly till now, the project directory should look like this:

```text
discord-bot/
├── node_modules
├── package-lock.json
└── package.json
```

!!! note
    Git or any VCS initialised projects will have more files. These files will not be taken into consideration in this guide.

## Installing a linter

While you are coding, it's possible to run into numerous syntax errors or code in an inconsistent style. You should install a linter to ease these troubles. While code editors generally can point out syntax errors, linters coerce your code into a specific style as defined by the configuration. While this is not required, it is advised.

We recommend [ESLint]. You may want to follow the DJS guide on [setting up a linter][djs-linter].

## Next steps

The discord.js guide perfectly explains how to [setup a bot application][djs-app] and [adding your bot to servers][djs-add].

Follow those guides before proceeding!

[node]: https://nodejs.org/

[node-dwn]: https://nodejs.org/en/download/

[npm]: https://docs.npmjs.com/about-npm

[eslint]: https://eslint.org/

[djs]: https://discord.js.org/#/

[djs-guide]: https://discordjs.guide

[djs-linter]: https://discordjs.guide/preparations/setting-up-a-linter.html

[djs-app]: https://discordjs.guide/preparations/setting-up-a-bot-application.html

[djs-add]: https://discordjs.guide/preparations/adding-your-bot-to-servers.html
