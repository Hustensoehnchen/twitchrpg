# twitchrpg
Open Sauce Twitch Idle RPG thru Streambot C# script collection

# GENERALK
Base idea is simple: Text-Based idle RPG via Twitch chat that can be customized to use with redeems, effects and whatever thru streamerbot.

# Limitations
- Streamerbot C# Library limitations exist
- Streamerbot doesn't have integrations for everything, it might be required to write middlewares for advanced ideas
- Twitch Message Length limit: For data parsed as text, keep in mind Twitch only has limited amount of characters available. Going above it will not send any message at all
- Twitch actual Message limit: not tested but prolly if ur bot spams too many messages, it might get suspended
- Currently .json is loaded for more complex data structures, never tested with huge amount of users so it might later make sense to migrate to DB

# Structure/General Format
The base format of this thing is simple: 
- We use the inbuilt twitch user vars from Streamerbot to save data for each user.
- An "encounter" procedure is running in the background with a set timer after which each registered user has a chance for an encounter
- The encounter is being stored as user var, making it so the user never "loses" the encounter, but can also not encounter anything new before interacting with the encounter
- User has two options, fight or flee
- Fight leads to a customizable combat simulation, current state relatively simple
- If the user wins they get goods such as currency and items where currency is stored in user vars and items are stored in an external .json
- If the user loses, they lose a percentage of their currency
- Since the user vars have limited capability in terms of data type, we use external .json to store more complex structures such as items, enemies, user inventory and so on

