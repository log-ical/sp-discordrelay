# sp-discordrelay

Discord ⇄ Server interaction for the Source Engine

# Installation

Place discordrelay.smx inside of `./cstrike/addons/sourcemod/plugins` and update convars in `./cstrike/cfg/sourcemod/discordrelay.cfg` after running the plugin.

# Dependencies

SteamWorks - https://forums.alliedmods.net/showthread.php?t=229556

discord-api - https://github.com/Cruze03/sourcemod-discord

*Note - If you plan to send messages/requests to the server from discord ensure you have Message Intents enabled in the app dashboard. [^1]
![unknown](https://user-images.githubusercontent.com/42725021/191847732-36a08338-ca11-4ae3-8584-ddc9a308400a.png)
[^1]:  Thank you ampere. Image provieded by dysphie.

ripext (sourcemod REST api) - https://forums.alliedmods.net/showthread.php?t=298024

# Configuration

### discrelay_steamapikey
This will be your steam API key which you can find at https://steamcommunity.com/dev/apikey. The key is used to grab the client's steam avatar.

### discrelay_discordbottoken
Your discord bot token found/created by going to https://discord.com/developers/applications, creating an application, creating a bot, and copying the bot token. *You do not need the bot to be running, just having it in your server will work.*

### discrelay_discordwebhook 
Set this to your Discord channel's webhook url. You can create one by going to your Discord server, entering a text channel's settings, then in integrations create a webhook and copy the url. 

### discrelay_discordserverid
Enable Developer Mode in Discord, right click on the server name in the top left and click Copy ID. Required for communication between Discord and Source. 

### discrelay_channelid
Enable Developer Mode in Discord, right click on the channel name and click Copy ID. This is the channel messages will appear in.

### discrelay_servertodiscord
Enable to allow messages sent in the server to be sent through discord via webhook.

### discrelay_discordtoserver 
Enable to allow messages sent in discord to be sent to the server.

### discrelay_servertodiscordavatars
Change avatar in messages sent to Discord to the client's Steam avatar. Requires a valid Steam API key.

### discrelay_connectmessage
Send client connection messages to Discord.

### discrelay_disconnectmessage 
Send client disconnection messages to Discord.

### discrelay_mapchangemessage
Send map change messages to Discord.

### discrelay_message
Enable to allow client messages in the server to be sent to Discord. This is any message thats not a command, only exception is any ! command which can be hidden by enabling discrelay_hideexclammessage.

### discrelay_hideexclammessage
Hides any message that begins with ! or /, discrelay_message needs to be enabled for this to work.

### discrelay_msg_textcol & discrelay_msg_varcol
	("%s[%sDiscord%s] %s%s%s#%s%s%s: %s", 	g_msg_textcol, g_msg_varcol, g_msg_textcol,
								g_msg_varcol, discorduser, g_msg_textcol,
								g_msg_varcol, discriminator, g_msg_textcol,
								message)
discorduser, discriminator, and message are discord things, but g_msg_textcol and g_msg_varcol refer to the colors used for the message that will be sent to the server when doing discord -> server. The plugin uses morecolors.inc to supply the colors, so when setting the cvar make sure to set it like {red} for example. Depending on the game you are using different options to set the color can be chosen such as using hex (more information here https://forums.alliedmods.net/showthread.php?t=247770). 

### discrelay_printsbppbans
Print bans, if SBPP is installed on the server.

### discrelay_printsbppcomms
Print gags, mutes, and silences, if SBPP is installed on the server.

### discrelay_sbppavatar
URL to an image. Used to change the avatar of the SBPP messages.

### discrelay_rcon_enabled
Enable RCon functionality.

# Warning to server owners: only let people you trust have access to the RCon channel; all messages sent in this channel is considered to be a command.
### discrelay_rcon_channelid
Discord channel ID for where rcon commands should be sent.
### discrelay_rcon_printreponse
Prints server response to the command.
### discrelay_rcon_webhook
Webhook for RCon reponse.
