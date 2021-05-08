# sp-discordrelay

Discord ⇄ Server interaction made for CS:S

# Installation

Place discordrelay.smx inside of `./cstrike/addons/sourcemod/plugins` and update convars to your liking in `./cstrike/cfg/sourcemod/discordrelay.cfg` after running the plugin (May take a map change for some changed to take effect).

# Dependencies

SteamWorks - https://forums.alliedmods.net/showthread.php?t=229556

discord-api - https://forums.alliedmods.net/showthread.php?t=292448

ripext (sourcemod REST api) - https://forums.alliedmods.net/showthread.php?t=298024

# Configuration

### discrelay_steamapikey
This will be your steam API key which you can find at https://steamcommunity.com/dev/apikey. The key is used to grab the client `ISteamUser/GetPlayerSummaries`from the steam api so it can change the discord webhook's avatar to the clients steam avatar. If you aren't going to be using webhook avatars (discrelay_servertodiscordavatars) then you can leave this blank, just make sure that discrelay_servertodiscordavatars is 0.
### discrelay_discordbottoken
This will be your discord bots token which is found/created by going to https://discord.com/developers/applications, creating an application, then in the bots setting by creating a bot and copying the bot token. You do not need the bot to be running, just having it in your server will work.
The discord bot is responsible for handling discord to server interaction, in order to use this feature discrelay_discordserverid, discrelay_channelid, and discrelay_discordtoserver need to be set correctly.
### discrelay_discordwebhook 
Set this to your webhook url, you can create one by going to your discord server, entering a text channels settings, integrations, create a webhook, then copy url. The webhook is needed to handle all server to discord integration, if you don't want to have anything going to your discord server from the server leave this blank and be sure to set discrelay_servertodiscord, and all message cvars (ex: discrelay_connectmessage) to 0.
### discrelay_discordserverid
This is for discord to server integration, to get it make sure developer mode is enabled in your discord and right clicking on the server and clicking Copy Id. discrelay_discordbottoken, discrelay_channelid, and discrelay_discordtoserver need to be set for messages to go through.
### discrelay_channelid
This is for discord to server integration, to get it make sure developer mode is enabled in your discord and right clicking on the channel and clicking Copy Id. **This will be the channel that messages sent in will go to the server.** discrelay_discordbottoken, discrelay_discordserverid, and discrelay_discordtoserver need to be set for messages to go through.
### discrelay_servertodiscord
Enable to allow messages sent in the server to be sent through discord through the webhook. Requires that discrelay_discordwebhook is set to a valid url.
### discrelay_discordtoserver 
Enable to allow messages sent in discord to be sent to the server. Requires discrelay_discordbottoken, discrelay_discordserverid, and discrelay_channelid to be set.
### discrelay_servertodiscordavatars
Enable to make webhooks change its avatar to the client's steam avatar. Requires that discrelay_steamapikey and discrelay_discordwebhook are valid.
### discrelay_connectmessage
Enable to allow client connection messages to be sent to discord through the webhook.
### discrelay_disconnectmessage 
Enable to allow client disconnection messages to be sent to discord through the webhook.
### discrelay_mapchangemessage
Enable to allow map changes to be sent to discord through the webhook.
### discrelay_message
Enable to allow client messages in the server to be sent to discord though the webhook. This is any message thats not a command, only exception is any ! command which can be hidden by enabling discrelay_hideexclammessage.
### discrelay_hideexclammessage
Hides any message that begins with ! or /, discrelay_message needs to be enabled for this to work.
### discrelay_msg_textcol & discrelay_msg_varcol
	CPrintToChatAll("%s[%sDiscord%s] %s%s%s#%s%s%s: %s", 	g_msg_textcol, g_msg_varcol, g_msg_textcol,
								g_msg_varcol, discorduser, g_msg_textcol,
								g_msg_varcol, discriminator, g_msg_textcol,
								message);
discorduser, discriminator, and message are discord things, but g_msg_textcol and g_msg_varcol refer to the colors used for the message that will be sent to the server when doing discord -> server. The plugin uses morecolors.inc to supply the colors, so when setting the cvar make sure to set it like {red} for example. Depending on the game you are using different options to set the color can be chosen such as using hex (more information here https://forums.alliedmods.net/showthread.php?t=247770). 
### discrelay_printsbppbans
If set to 1, it will print bans, if you have sbpp installed on the server, to the location of where the discrelay_discordwebhook is set.
### discrelay_printsbppcomms
If set to 1, it will print gags, mutes, and silences, if you have sbpp installed on the server, to the location of where the discrelay_discordwebhook is set.
### discrelay_sbppavatar
This must be a URL to an image, this will be the image used for the webhooks profile picutre and footer icon for SBPP related functions.
