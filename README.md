# discorator.js
The Discord API Wrapper that works for both bots and user accounts.

> [!WARNING]  
> not being updated anymore but feel free to fork it or whatever

## Installing
#### npm
```
npm i discorator.js
```

## Example
You can check the example files in the `testing` directory for more details, however the following shows how one would sign into Discord:
```js
import { Client, IntentBits, TextChannel, generateNonce } from 'discorator.js'

(async function() {
    const client = await new Client({ 
        verbose: true, 
        userType: 'user',
        intents: [IntentBits.Guilds, IntentBits.Direct_Messages, IntentBits.Message_Content, IntentBits.Guild_Messages]
    });
    await client.loginByToken('token') // token login
    // await client.loginByCredentials({email: 'h@h.com', password: 'h', captchaToken: '2captcha-token'}) // credential login (todo: totp support)

    // send command to a channel
    let channel = await new TextChannel(client).fetch('channel_id') // create a new channel and initialize it
    let res = await channel.emitCommand('ping', 'id') // issue a command (name and application id), subcommand and args are under the 'options' argument, although they need to be manually constructed at the moment.
    
})();
``

