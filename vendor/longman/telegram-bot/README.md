<h1 align="center">
    PHP Telegram Bot<br>
	<br>
    <img src="https://raw.githubusercontent.com/php-telegram-bot/assets/master/logo/512px/logo_plain.png" title="PHP Telegram Bot" alt="PHP Telegram Bot logo">
	<br>
</h1>

A Telegram Bot based on the official [Telegram Bot API]

[![API Version](https://img.shields.io/badge/Bot%20API-4.4%20%28July%202019%29-32a2da.svg)](https://core.telegram.org/bots/api#july-29-2019)
[![Join the bot support group on Telegram](https://img.shields.io/badge/telegram-@PHP__Telegram__Bot__Support-64659d.svg)](https://telegram.me/PHP_Telegram_Bot_Support)
[![Donate](https://img.shields.io/badge/%F0%9F%92%99-Donate%20%2F%20Support%20Us-blue.svg)](#donate)

[![Build Status](https://travis-ci.org/php-telegram-bot/core.svg?branch=master)](https://travis-ci.org/php-telegram-bot/core)
[![Code Coverage](https://img.shields.io/scrutinizer/coverage/g/php-telegram-bot/core/master.svg?style=flat)](https://scrutinizer-ci.com/g/php-telegram-bot/core/?b=master)
[![Code Quality](https://img.shields.io/scrutinizer/g/php-telegram-bot/core/master.svg?style=flat)](https://scrutinizer-ci.com/g/php-telegram-bot/core/?b=master)
[![Latest Stable Version](https://img.shields.io/packagist/v/longman/telegram-bot.svg)](https://packagist.org/packages/longman/telegram-bot)
[![Dependencies](https://tidelift.com/badges/github/php-telegram-bot/core?style=flat)][Tidelift]
[![Total Downloads](https://img.shields.io/packagist/dt/longman/telegram-bot.svg)](https://packagist.org/packages/longman/telegram-bot)
[![Downloads Month](https://img.shields.io/packagist/dm/longman/telegram-bot.svg)](https://packagist.org/packages/longman/telegram-bot)
[![Minimum PHP Version](http://img.shields.io/badge/php-%3E%3D5.6-8892BF.svg)](https://php.net/)
[![License](https://img.shields.io/packagist/l/longman/telegram-bot.svg)](https://github.com/php-telegram-bot/core/LICENSE)

## Table of Contents
- [Introduction](#introduction)
- [Instructions](#instructions)
    - [Create your first bot](#create-your-first-bot)
    - [Require this package with Composer](#require-this-package-with-composer)
    - [Choose how to retrieve Telegram updates](#choose-how-to-retrieve-telegram-updates)
- [Webhook installation](#webhook-installation)
    - [Self Signed Certificate](#self-signed-certificate)
    - [Unset Webhook](#unset-webhook)
- [getUpdates installation](#getupdates-installation)
    - [getUpdates without database](#getupdates-without-database)
- [Support](#support)
    - [Types](#types)
    - [Inline Query](#inline-query)
    - [Methods](#methods)
    - [Send Message](#send-message)
    - [Send Photo](#send-photo)
    - [Send Chat Action](#send-chat-action)
    - [getUserProfilePhoto](#getuserprofilephoto)
    - [getFile and downloadFile](#getfile-and-downloadfile)
    - [Send message to all active chats](#send-message-to-all-active-chats)
- [Utils](#utils)
    - [MySQL storage (Recommended)](#mysql-storage-recommended)
        - [External Database connection](#external-database-connection)
    - [Channels Support](#channels-support)
- [Commands](#commands)
    - [Predefined Commands](#predefined-commands)
    - [Custom Commands](#custom-commands)
    - [Commands Configuration](#commands-configuration)
    - [Admin Commands](#admin-commands)
        - [Set Admins](#set-admins)
        - [Channel Administration](#channel-administration)
- [Upload and Download directory path](#upload-and-download-directory-path)
- [Logging](doc/01-utils.md)
- [Documentation](#documentation)
- [Assets](#assets)
- [Example bot](#example-bot)
- [Projects with this library](#projects-with-this-library)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [Security](#security)
- [Donate](#donate)
- [License](#license)
- [Credits](#credits)

## Introduction

This is a pure PHP Telegram Bot, fully extensible via plugins.

Telegram announced official support for a [Bot API](https://telegram.org/blog/bot-revolution), allowing integrators of all sorts to bring automated interactions to the mobile platform.
This Bot aims to provide a platform where one can simply write a bot and have interactions in a matter of minutes.

The Bot can:
- Retrieve updates with [webhook](#webhook-installation) and [getUpdates](#getupdates-installation) methods.
- Supports all types and methods according to Telegram API 4.4 (July 2019).
- Supports supergroups.
- Handle commands in chat with other bots.
- Manage Channel from the bot admin interface.
- Full support for **inline bots**.
- Inline keyboard.
- Messages, InlineQuery and ChosenInlineQuery are stored in the Database.
- Conversation feature.

---

This code is available on [GitHub](https://github.com/php-telegram-bot/core). Pull requests are welcome.

## Instructions

### Create your first bot

1. Message [`@BotFather`](https://telegram.me/BotFather) with the following text: `/newbot`
   
   If you don't know how to message by username, click the search field on your Telegram app and type `@BotFather`, where you should be able to initiate a conversation. Be careful not to send it to the wrong contact, because some users have similar usernames to `BotFather`.

   ![BotFather initial conversation](https://user-images.githubusercontent.com/9423417/60736229-bc2aeb80-9f45-11e9-8d35-5b53145347bc.png)

2. `@BotFather` replies with:

    ```
    Alright, a new bot. How are we going to call it? Please choose a name for your bot.
    ```

3. Type whatever name you want for your bot.

4. `@BotFather` replies with:
    
    ```
    Good. Now let's choose a username for your bot. It must end in `bot`. Like this, for example: TetrisBot or tetris_bot.
    ```

5. Type whatever username you want for your bot, minimum 5 characters, and must end with `bot`. For example: `telesample_bot`

6. `@BotFather` replies with:

    ```
    Done! Congratulations on your new bot. You will find it at
    telegram.me/telesample_bot. You can now add a description, about
    section and profile picture for your bot, see /help for a list of
    commands.

    Use this token to access the HTTP API:
    123456789:AAG90e14-0f8-40183D-18491dDE

    For a description of the Bot API, see this page:
    https://core.telegram.org/bots/api
    ```

7. Note down the 'token' mentioned above.

*Optionally set the bot privacy:*

1. Send `/setprivacy` to `@BotFather`.

   ![BotFather later conversation](https://user-images.githubusercontent.com/9423417/60736340-26439080-9f46-11e9-970f-8f33bbe39c5f.png)

2. `@BotFather` replies with:

    ```
    Choose a bot to change group messages settings.
    ```

3. Type (or select) `@telesample_bot` (change to the username you set at step 5
above, but start it with `@`)

4. `@BotFather` replies with:

    ```
    'Enable' - your bot will only receive messages that either start with the '/' symbol or mention the bot by username.
    'Disable' - your bot will receive all messages that people send to groups.
    Current status is: ENABLED
    ```

5. Type (or select) `Disable` to let your bot receive all messages sent to a group.

6. `@BotFather` replies with:

    ```
    Success! The new status is: DISABLED. /help
    ```

### Require this package with Composer

Install this package through [Composer].
Edit your project's `composer.json` file to require `longman/telegram-bot`.

Create *composer.json* file
```json
{
    "name": "yourproject/yourproject",
    "type": "project",
    "require": {
        "php": ">=5.5",
        "longman/telegram-bot": "*"
    }
}
```
and run `composer update`

**or**

run this command in your command line:

```bash
composer require longman/telegram-bot
```

### Choose how to retrieve Telegram updates

The bot can handle updates with [**Webhook**](#webhook-installation) or [**getUpdates**](#getupdates-installation) method:

|      | Webhook | getUpdates |
| ---- | :----: | :----: |
| Description | Telegram sends the updates directly to your host | You have to fetch Telegram updates manually |
| Host with https | Required | Not required |
| MySQL | Not required | ([Not](#getupdates-without-database)) Required  |

## Webhook installation

Note: For a more detailed explanation, head over to the [example-bot repository] and follow the instructions there.

In order to set a [Webhook][api-setwebhook] you need a server with HTTPS and composer support.
(For a [self signed certificate](#self-signed-certificate) you need to add some extra code)

Create [*set.php*][set.php] with the following contents:
```php
<?php
// Load composer
require __DIR__ . '/vendor/autoload.php';

$bot_api_key  = 'your:bot_api_key';
$bot_username = 'username_bot';
$hook_url     = 'https://your-domain/path/to/hook.php';

try {
    // Create Telegram API object
    $telegram = new Longman\TelegramBot\Telegram($bot_api_key, $bot_username);

    // Set webhook
    $result = $telegram->setWebhook($hook_url);
    if ($result->isOk()) {
        echo $result->getDescription();
    }
} catch (Longman\TelegramBot\Exception\TelegramException $e) {
    // log telegram errors
    // echo $e->getMessage();
}
```

Open your *set.php* via the browser to register the webhook with Telegram.
You should see `Webhook was set`.

Now, create [*hook.php*][hook.php] with the following contents:
```php
<?php
// Load composer
require __DIR__ . '/vendor/autoload.php';

$bot_api_key  = 'your:bot_api_key';
$bot_username = 'username_bot';

try {
    // Create Telegram API object
    $telegram = new Longman\TelegramBot\Telegram($bot_api_key, $bot_username);

    // Handle telegram webhook request
    $telegram->handle();
} catch (Longman\TelegramBot\Exception\TelegramException $e) {
    // Silence is golden!
    // log telegram errors
    // echo $e->getMessage();
}
```

### Self Signed Certificate

To upload the certificate, add the certificate path as a parameter in *set.php*:
```php
$result = $telegram->setWebhook($hook_url, ['certificate' => '/path/to/certificate']);
```

### Unset Webhook

Edit [*unset.php*][unset.php] with your bot credentials and execute it.

## getUpdates installation

For best performance, the MySQL database should be enabled for the `getUpdates` method!

Create [*getUpdatesCLI.php*][getUpdatesCLI.php] with the following contents:
```php
#!/usr/bin/env php
<?php
require __DIR__ . '/vendor/autoload.php';

$bot_api_key  = 'your:bot_api_key';
$bot_username = 'username_bot';

$mysql_credentials = [
   'host'     => 'localhost',
   'port'     => 3306, // optional
   'user'     => 'dbuser',
   'password' => 'dbpass',
   'database' => 'dbname',
];

try {
    // Create Telegram API object
    $telegram = new Longman\TelegramBot\Telegram($bot_api_key, $bot_username);

    // Enable MySQL
    $telegram->enableMySql($mysql_credentials);

    // Handle telegram getUpdates request
    $telegram->handleGetUpdates();
} catch (Longman\TelegramBot\Exception\TelegramException $e) {
    // log telegram errors
    // echo $e->getMessage();
}
```

Next, give the file permission to execute:
```bash
$ chmod +x getUpdatesCLI.php
```

Lastly, run it!
```bash
$ ./getUpdatesCLI.php
```

### getUpdates without database

If you choose to / or are obliged to use the `getUpdates` method without a database, you can replace the `$telegram->useMySQL(...);` line above with:
```php
$telegram->useGetUpdatesWithoutDatabase();
```

## Support

### Types

All types are implemented according to Telegram API (20 January 2016).

### Inline Query

Full support for inline query according to Telegram API (20 January 2016).

### Methods

All methods are implemented according to Telegram API (20 January 2016).

#### Send Message

Messages longer than 4096 characters are split up into multiple messages.

```php
$result = Request::sendMessage([
    'chat_id' => $chat_id,
    'text'    => 'Your utf8 text 😜 ...',
]);
```

#### Send Photo

To send a local photo, add it properly to the `$data` parameter using the file path:

```php
$result = Request::sendPhoto([
    'chat_id' => $chat_id,
    'photo'   => Request::encodeFile('/path/to/pic.jpg'),
]);
```

If you know the `file_id` of a previously uploaded file, just use it directly in the data array:

```php
$result = Request::sendPhoto([
    'chat_id' => $chat_id,
    'photo'   => 'AAQCCBNtIhAoAAss4tLEZ3x6HzqVAAqC',
]);
```

To send a remote photo, use the direct URL instead:

```php
$result = Request::sendPhoto([
    'chat_id' => $chat_id,
    'photo'   => 'https://example.com/path/to/pic.jpg',
]);
```

*sendAudio*, *sendDocument*, *sendAnimation*, *sendSticker*, *sendVideo*, *sendVoice* and *sendVideoNote* all work in the same way, just check the [API documentation](https://core.telegram.org/bots/api#sendphoto) for the exact usage.
See the [*ImageCommand.php*][ImageCommand.php] for a full example.

#### Send Chat Action

```php
Request::sendChatAction([
    'chat_id' => $chat_id,
    'action'  => Longman\TelegramBot\ChatAction::TYPING,
]);
```

#### getUserProfilePhoto

Retrieve the user photo, see [*WhoamiCommand.php*][WhoamiCommand.php] for a full example.

#### getFile and downloadFile

Get the file path and download it, see [*WhoamiCommand.php*][WhoamiCommand.php] for a full example.

#### Send message to all active chats

To do this you have to enable the MySQL connection.
Here's an example of use (check [`DB::selectChats()`][DB::selectChats] for parameter usage):

```php
$results = Request::sendToActiveChats(
    'sendMessage', // Callback function to execute (see Request.php methods)
    ['text' => 'Hey! Check out the new features!!'], // Param to evaluate the request
    [
        'groups'      => true,
        'supergroups' => true,
        'channels'    => false,
        'users'       => true,
    ]
);
```

You can also broadcast a message to users, from the private chat with your bot. Take a look at the [admin commands](#admin-commands) below.

## Utils

### MySQL storage (Recommended)

If you want to save messages/users/chats for further usage in commands, create a new database (`utf8mb4_unicode_520_ci`), import *structure.sql* and enable MySQL support after object creation and BEFORE `handle()` method:

```php
$mysql_credentials = [
   'host'     => 'localhost',
   'port'     => 3306, // optional
   'user'     => 'dbuser',
   'password' => 'dbpass',
   'database' => 'dbname',
];

$telegram->enableMySql($mysql_credentials);
```

You can set a custom prefix to all the tables while you are enabling MySQL:

```php
$telegram->enableMySql($mysql_credentials, $bot_username . '_');
```

You can also store inline query and chosen inline query data in the database.

#### External Database connection

It is possible to provide the library with an external MySQL PDO connection.
Here's how to configure it:

```php
$telegram->enableExternalMySql($external_pdo_connection)
//$telegram->enableExternalMySql($external_pdo_connection, $table_prefix)
```
### Channels Support

All methods implemented can be used to manage channels.
With [admin commands](#admin-commands) you can manage your channels directly with your bot private chat.

## Commands

### Predefined Commands

The bot is able to recognise commands in a chat with multiple bots (/command@mybot).

It can execute commands that get triggered by chat events.

Here's the list:

- *StartCommand.php* (A new user starts to use the bot.)
- *NewChatMembersCommand.php* (A new member(s) was added to the group, information about them.)
- *LeftChatMemberCommand.php* (A member was removed from the group, information about them.)
- *NewChatTitleCommand.php* (A chat title was changed to this value.)
- *NewChatPhotoCommand.php* (A chat photo was changed to this value.)
- *DeleteChatPhotoCommand.php* (Service message: the chat photo was deleted.)
- *GroupChatCreatedCommand.php* (Service message: the group has been created.)
- *SupergroupChatCreatedCommand.php* (Service message: the supergroup has been created.)
- *ChannelChatCreatedCommand.php* (Service message: the channel has been created.)
- *MigrateToChatIdCommand.php* (The group has been migrated to a supergroup with the specified identifier.)
- *MigrateFromChatIdCommand.php* (The supergroup has been migrated from a group with the specified identifier.)
- *PinnedMessageCommand.php* (Specified message was pinned.)

- *GenericmessageCommand.php* (Handle any type of message.)
- *GenericCommand.php* (Handle commands that don't exist or to use commands as a variable.)
    - Favourite colour? */black, /red*
    - Favourite number? */1, /134*

### Custom Commands

Maybe you would like to develop your own commands.
There is a guide to help you [create your own commands][wiki-create-your-own-commands].

Also, be sure to have a look at the [example commands][ExampleCommands-folder] to learn more about custom commands and how they work.

### Commands Configuration

With this method you can set some command specific parameters, for example:

```php
// Google geocode/timezone API key for /date command
$telegram->setCommandConfig('date', [
    'google_api_key' => 'your_google_api_key_here',
]);

// OpenWeatherMap API key for /weather command
$telegram->setCommandConfig('weather', [
    'owm_api_key' => 'your_owm_api_key_here',
]);
```

### Admin Commands

Enabling this feature, the bot admin can perform some super user commands like:
- List all the chats started with the bot */chats*
- Clean up old database entries */cleanup*
- Show debug information about the bot */debug*
- Send message to all chats */sendtoall*
- Post any content to your channels */sendtochannel*
- Inspect a user or a chat with */whois*

Take a look at all default admin commands stored in the [*src/Commands/AdminCommands/*][AdminCommands-folder] folder.

#### Set Admins

You can specify one or more admins with this option:

```php
// Single admin
$telegram->enableAdmin(your_telegram_user_id);

// Multiple admins
$telegram->enableAdmins([
    your_telegram_user_id,
    other_telegram_user_id,
]);
```
Telegram user id can be retrieved with the [*/whoami*][WhoamiCommand.php] command.

#### Channel Administration

To enable this feature follow these steps:
- Add your bot as channel administrator, this can be done with any Telegram client.
- Enable admin interface for your user as explained in the admin section above.
- Enter your channel name as a parameter for the [*/sendtochannel*][SendtochannelCommand.php] command:
```php
$telegram->setCommandConfig('sendtochannel', [
    'your_channel' => [
        '@type_here_your_channel',
    ]
]);
```
- If you want to manage more channels:
```php
$telegram->setCommandConfig('sendtochannel', [
    'your_channel' => [
        '@type_here_your_channel',
        '@type_here_another_channel',
        '@and_so_on',
    ]
]);
```
- Enjoy!

## Upload and Download directory path

To use the Upload and Download functionality, you need to set the paths with:
```php
$telegram->setDownloadPath('/your/path/Download');
$telegram->setUploadPath('/your/path/Upload');
```

## Documentation

Take a look at the repo [Wiki] for further information and tutorials!
Feel free to improve!

## Assets

All project assets can be found in the [assets](https://github.com/php-telegram-bot/assets) repository.

## Example bot

We're busy working on a full A-Z example bot, to help get you started with this library and to show you how to use all its features.
You can check the progress of the [example-bot repository]).

## Projects with this library

Here's a list of projects that feats this library, feel free to add yours!
- [Inline Games](https://github.com/jacklul/inlinegamesbot) ([@inlinegamesbot](https://telegram.me/inlinegamesbot))
- [Super-Dice-Roll](https://github.com/RafaelDelboni/Super-Dice-Roll) ([@superdiceroll_bot](https://telegram.me/superdiceroll_bot))
- [tg-mentioned-bot](https://github.com/gruessung/tg-mentioned-bot)

## Troubleshooting

If you like living on the edge, please report any bugs you find on the [PHP Telegram Bot issues][issues] page.

## Contributing

See [CONTRIBUTING](CONTRIBUTING.md) for more information.

## Security

See [SECURITY](SECURITY.md) for more information.

## Donate

All work on this bot consists of many hours of coding during our free time, to provide you with a Telegram Bot library that is easy to use and extend.
If you enjoy using this library and would like to say thank you, donations are a great way to show your support.

Donations are invested back into the project :+1:

Thank you for keeping this project alive :pray:

- [![Patreon](https://user-images.githubusercontent.com/9423417/59235980-a5fa6b80-8be3-11e9-8ae7-020bc4ae9baa.png) Patreon.com/phptelegrambot][Patreon]
- [![OpenCollective](https://user-images.githubusercontent.com/9423417/59235978-a561d500-8be3-11e9-89be-82ec54be1546.png) OpenCollective.com/php-telegram-bot][OpenCollective]
- [![Ko-fi](https://user-images.githubusercontent.com/9423417/59235976-a561d500-8be3-11e9-911d-b1908c3e6a33.png) Ko-fi.com/phptelegrambot][Ko-fi]
- [![Tidelift](https://user-images.githubusercontent.com/9423417/59235982-a6930200-8be3-11e9-8ac2-bfb6991d80c5.png) Tidelift.com/longman/telegram-bot][Tidelift]
- [![Liberapay](https://user-images.githubusercontent.com/9423417/59235977-a561d500-8be3-11e9-9d16-bc3b13d3ceba.png) Liberapay.com/PHP-Telegram-Bot][Liberapay]
- [![PayPal](https://user-images.githubusercontent.com/9423417/59235981-a5fa6b80-8be3-11e9-9761-15eb7a524cb0.png) PayPal.me/noplanman][PayPal-noplanman] (account of @noplanman)
- [![Bitcoin](https://user-images.githubusercontent.com/9423417/59235974-a4c93e80-8be3-11e9-9fde-260c821b6eae.png) 166NcyE7nDxkRPWidWtG1rqrNJoD5oYNiV][Bitcoin]
- [![Ethereum](https://user-images.githubusercontent.com/9423417/59235975-a4c93e80-8be3-11e9-8762-7a47c62c968d.png) 0x485855634fa212b0745375e593fAaf8321A81055][Ethereum]

## License

Please see the [LICENSE](LICENSE) included in this repository for a full copy of the MIT license, which this project is licensed under.

## Credits

Credit list in [CREDITS](CREDITS)

---

<div align="center">
    <b>
        <a href="https://tidelift.com/subscription/pkg/packagist-longman-telegram-bot?utm_source=packagist-longman-telegram-bot&utm_medium=referral&utm_campaign=readme-footer">Get professional support for this package with a Tidelift subscription</a>
    </b>
    <br>
    <sub>
        Tidelift helps make open source sustainable for maintainers while giving companies<br>assurances about security, maintenance, and licensing for their dependencies.
    </sub>
</div>

[Telegram Bot API]: https://core.telegram.org/bots/api "Telegram Bot API"
[Composer]: https://getcomposer.org/ "Composer"
[example-bot repository]: https://github.com/php-telegram-bot/example-bot "Example Bot repository"
[api-setwebhook]: https://core.telegram.org/bots/api#setwebhook "Webhook on Telegram Bot API"
[set.php]: https://github.com/php-telegram-bot/example-bot/blob/master/set.php "example set.php"
[unset.php]: https://github.com/php-telegram-bot/example-bot/blob/master/unset.php "example unset.php"
[hook.php]: https://github.com/php-telegram-bot/example-bot/blob/master/hook.php "example hook.php"
[getUpdatesCLI.php]: https://github.com/php-telegram-bot/example-bot/blob/master/getUpdatesCLI.php "example getUpdatesCLI.php"
[AdminCommands-folder]: https://github.com/php-telegram-bot/core/tree/master/src/Commands/AdminCommands "Admin commands folder"
[ExampleCommands-folder]: https://github.com/php-telegram-bot/example-bot/blob/master/Commands "Example commands folder"
[ImageCommand.php]: https://github.com/php-telegram-bot/example-bot/blob/master/Commands/ImageCommand.php "example /image command"
[WhoamiCommand.php]: https://github.com/php-telegram-bot/example-bot/blob/master/Commands/WhoamiCommand.php "example /whoami command"
[HelpCommand.php]: https://github.com/php-telegram-bot/example-bot/blob/master/Commands/HelpCommand.php "example /help command"
[SendtochannelCommand.php]: https://github.com/php-telegram-bot/core/blob/master/src/Commands/AdminCommands/SendtochannelCommand.php "/sendtochannel admin command"
[DB::selectChats]: https://github.com/php-telegram-bot/core/blob/0.46.0/src/DB.php#L1000 "DB::selectChats() parameters"
[Wiki]: https://github.com/php-telegram-bot/core/wiki "PHP Telegram Bot Wiki"
[wiki-create-your-own-commands]: https://github.com/php-telegram-bot/core/wiki/Create-your-own-commands "Create your own commands"
[issues]: https://github.com/php-telegram-bot/core/issues "PHP Telegram Bot Issues"

[Patreon]: https://www.patreon.com/phptelegrambot "Support us on Patreon"
[OpenCollective]: https://opencollective.com/php-telegram-bot "Support us on Open Collective"
[Ko-fi]: https://ko-fi.com/phptelegrambot "Support us on Ko-fi"
[Tidelift]: https://tidelift.com/subscription/pkg/packagist-longman-telegram-bot?utm_source=packagist-longman-telegram-bot&utm_medium=referral&utm_campaign=readme "Support us on Tidelift"
[Liberapay]: https://liberapay.com/PHP-Telegram-Bot "Donate with Liberapay"
[PayPal-noplanman]: https://paypal.me/noplanman "Donate with PayPal"
[Bitcoin]: https://www.blockchain.com/btc/address/166NcyE7nDxkRPWidWtG1rqrNJoD5oYNiV "Donate with Bitcoin"
[Ethereum]: https://etherscan.io/address/0x485855634fa212b0745375e593fAaf8321A81055 "Donate with Ethereum"
