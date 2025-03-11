![Bot avatar](https://cdn.discordapp.com/embed/avatars/0.png&fit=cover&mask=circle)

# bot-ts

> Made with [bot.ts](https://ghom.gitbook.io/bot-ts/) by **team1349069864027033650**  
> CLI version: `9.0.7`  
> Bot.ts version: `v9.0.0-Nirbose`  
> Licence: `ISC`

## Description

Discord bot for Avalonya  
This bot is private and cannot be invited in other servers.

## Specifications

You can find the documentation of bot.ts [here](https://ghom.gitbook.io/bot-ts/).  
Below you will find the specifications for **bot-ts**.

## Configuration file

```ts
import { Config } from "#core/config"
import { Options, Partials } from "discord.js"
import { z } from "zod"

export const config = new Config({
  ignoreBots: true,
  openSource: true,
  envSchema: z.object({}),
  permissions: ["Administrator"],
  client: {
    intents: [
      "Guilds",
      "GuildMessages",
      "GuildMessageReactions",
      "GuildMessageTyping",
      "DirectMessages",
      "DirectMessageReactions",
      "DirectMessageTyping",
      "MessageContent",
    ],
    partials: [Partials.Channel],
    makeCache: Options.cacheWithLimits({
      ...Options.DefaultMakeCacheSettings,

      // don't cache reactions
      ReactionManager: 0,
    }),
    sweepers: {
      ...Options.DefaultSweeperSettings,
      messages: {
        // every hour (in second)
        interval: 60 * 60,

        // 6 hours
        lifetime: 60 * 60 * 6,
      },
    },
  },
})

export default config.options

```

## Cron jobs

> No cron jobs have been created yet.

## Commands

### Slash commands

- [/help](src/slash/help.native.ts) - Show slash command details or list all slash commands  
- [/ping](src/slash/ping.native.ts) - Get the bot ping

### Textual commands

- [database](src/commands/database.native.ts) - Run SQL query on database  
- [eval](src/commands/eval.native.ts) - JS code evaluator  
- [help](src/commands/help.native.ts) - Help menu  
- [info](src/commands/info.native.ts) - Get information about bot  
- [terminal](src/commands/terminal.native.ts) - Run shell command from Discord  
- [turn](src/commands/turn.native.ts) - Turn on/off command handling

## Buttons

- [pagination](src/buttons/pagination.native.ts) - The pagination button

## Listeners

### Button  

- [interactionCreate](src/listeners/button.interactionCreate.native.ts) - Handle the interactions for buttons  

### Command  

- [messageCreate](src/listeners/command.messageCreate.native.ts) - Handle the messages for commands  

### Cron  

- [ready](src/listeners/cron.ready.native.ts) - Launch all cron jobs  

### Log  

- [afterReady](src/listeners/log.afterReady.native.ts) - Just log that bot is ready  

### Pagination  

- [messageDelete](src/listeners/pagination.messageDelete.native.ts) - Remove existing deleted paginator  
- [messageReactionAdd](src/listeners/pagination.messageReactionAdd.native.ts) - Handle the reactions for pagination  

### Slash  

- [guildCreate](src/listeners/slash.guildCreate.native.ts) - Deploy the slash commands to the new guild  
- [interactionCreate](src/listeners/slash.interactionCreate.native.ts) - Handle the interactions for slash commands  
- [ready](src/listeners/slash.ready.native.ts) - Deploy the slash commands

## Database

Using **sqlite3@latest** as database.  
Below you will find a list of all the tables used by **bot-ts**.

> No tables have been created yet.

## Information

This readme.md is dynamic, it will update itself with the latest information.  
If you see a mistake, please report it and an update will be made as soon as possible.

- Used by: **0** Discord guild
- Last update date: **3/11/2025**
