# 🤖 Kingshot Discord Bot
A powerful, multi-server Discord bot designed to coordinate alliance activities. It features automated daily reports, event reminders, and a dynamic role management system via dropdown menus.

It is designed for the **best alliance**:

### SYN FROM #1004

<img src="https://media.discordapp.net/attachments/1432834473803649155/1439786015094083785/1763341085023.jpg?ex=69888c77&is=69873af7&hm=0de32b0fb727f6fd145ea896181402635910626fdb1a1cdba04518d964652bdc&=&format=webp&width=1138&height=960" width="200" alt="[SYNERGY FROM 1004]">

So if you see this, greetings from us. If you want to join us, message Vexxy from SYN.

_(DON'T JOIN US IF YOU DISLIKE CLAY!)_

## 🚀 Key Features
- **Multi-Guild Support**: Complete data isolation between different Discord servers using unique Guild IDs.
- **Automated Role Management**: Automatically creates alliance roles and manages permissions for dedicated channels.
- **Persistent Dropdowns**: Self-service role selection menus that remain functional even after bot restarts.
- **Smart Event Reminders**: Automatically pings the relevant alliance role 15 minutes before an event starts.
- **Daily Agenda**: Posts a comprehensive overview of all scheduled events for the day (with an daily bot restart).
- **Flexible Scheduling**: Supports one-time events or recurring intervals (e.g., repeating every 7 days).

# 📋 Command Reference
This is a brief overview of the commands which exists. For further information, use the given information in Discord while using the bot.
For event management, look at section [Eventmanagement](#eventmanagement).
## Admin Commands (Permission Level 2)
|Command | Description |
|--------|-------------|
|/set_rank | Set rank of a person |
## Moderator Commands (Permission Level 1)
|Command | Description |
|-------------|---------|
|/allow_channel| Use this command in the channel where bot commands should work.
|/setup_roles | Deploys the persistent dropdown menu for users to join/leave alliance roles. Use this command in the role channel.|
|/set_alliance_channel |Links an alliance name to a text channel and creates the corresponding role.|
|EVENT COMMANDS|
|/add_event | Adds a new event. Format: Date YYYY-MM-DD, Time HH:MM.
|/update_event | Modifies an existing event using its ID or Name.|
|/remove_event | Permanently deletes an event from the database.|
|/list_alliance_channels | Displays all current alliance-to-channel mappings for the server. |
| CODE COMMANDS|
|/add_player|Remove User per User ID|
|/remove_player|Add new User per User-ID or multiple User (comma separeted)|
|/redeem|Start code redeemer for all players with a given code|


## Member Commands
|Command | Description |
|--------|-------------|
|/event_list | Displays an interactive panel showing all upcoming events for a specific alliance.|

## Eventmanagement

There are different kind of commands and usages, depending on the case.
All in all, I recommend to use the /-commands as they help you with the parameters. All following examples still will be message commands.

<b> THE ORDER OF THE COMMANDS ARE IMPORTANT IF YOU USE MESSAGE COMMANDS!</b>
### Initialization:
To start, you need to link a specific channel to a new alliance, you want to manage.
e.g.
```!set_alliance_channel SYN #syn```<br>
If there was no role for SYN (called SYN (case-sensitiv)), the bot will automatically create on and checks the permission for the linked channel (read only).
Now people can assign themselves the role of SYN in the channel where ```!setup_roles``` was used. The options for the drop down menu "updates" itself (resends new role message).
<br>

### For the events:

#### Add new event
If you want to add a new event, you have following options:
- Command: **/add_event**
- Parameter:
    - name: Name of the event
    - alliance: For which linked alliance is this event
    - time: Which time will it happen (HH:mm) in UTC
    - date: Which date will it happen (YYYY-MM-dd)
    - OPTIONAL: interval_days: What is the interval it will happen again. All followed events will reoccur at the same time as the event was created (e.g. 19:00), 0 or no interval_days means onetime events.

E.g.
```!add_event BT1 SYN 19:00 2026-02-07 2``` 
<br> 
#### Update / change event
If you want to update an old event, you have following options:
- Command: **/update_event**
- Parameter:
    - id_or_name: Name or id of the event
    - alliance: For which linked alliance is this event
    - time: Which time will it happen (HH:mm). If you change the time and don't add a date, only the time will change.
    - OPTIONAL: date: Which date will it happen (YYYY-MM-dd)
    - OPTIONAL: interval_days: What is the interval it will happen again
    - OPTIONAL: default_time: Change the default time when events will reoccur

E.g.
```!update_event BT1 SYN 18:30 2026-02-08 3 18:00``` 
#### Remove event
If you want to remove an old event, you have following options:
- Command: **/remove_event**
- Parameter:
    - id_or_name: Name or id of the event
    - alliance: For which linked alliance is this event

E.g.
```!remove_event BT1 SYN``` 

### Automatation
Events which has a interval_days as a parameter, will automatically be adjusted to the next date. The check for changes will happen after each restart of the bot, so currently at 2 UTC.

Events won't be deleted at all. So if you want to clean up the list from one time events, you need to delete them manually (maybe I change this to be automatically).
## 🛠 Setup & Installation
### 1. Prerequisites
- Python 3.9 or higher
- SQLite3 
- A Discord Bot Token (obtainable via the Discord Developer Portal)
### 2. Permissions
For the bot to function correctly, ensure it has the following **Guild Permissions**:
- ```Manage Roles``` (The bot's role must be higher in the hierarchy than the roles it creates).
- ```Manage Channels```
- ```Use External Emojis``` (Required for App-Emojis/Custom Emojis).
- ```Send Messages```
- ```Embed Links```