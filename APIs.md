# APIs:
## [GroupInitiative](https://wiki.roll20.net/Script:Group_Initiative)
The GroupInitiative API script for bulk-rolling Initiative is available in the approved dropdown list. Once it is activated it can be prepared for D&D 5e rules using the below commands in the chat log:

```
!group-init --del-group 1
!group-init --add-group --Bare initiative_bonus|current
!group-init --add-group --Bare npcd_dex_mod|current
```

## [Initiative Tracker](https://wiki.roll20.net/Script:Initiative_Tracker)
This one works well with _GroupInitiative_ to add rounds to the turn order automatically. It can do a whole bunch more as well (including tracking effects like poisoning etc.) but I haven't really used those features.  
  
It's not available in the approved scripts dropdown but you can check out the [wiki article](https://wiki.roll20.net/Script:Initiative_Tracker) that has a link to the code.

To use _Initiative Tracker_ and _GroupInitiative_ together make a new Macro (displayed in the _Macro Bar_) with the below text then highlight all tokens you want to include in the Turn Order and click the button:
```
!group-init
!tracker Round 1
!tracker Start
```

## Long Rest
This one comes with _5th Edition OGL by Roll20 Companion_ which is available in the approved dropdown. It'll reset the Player characters' health and spell slots using the below command/Macro:

`!longrest <character name>`

I've prettied one up a little to make a Token Action:
```
!longrest @{selected|character_name}
&{template:default} {{name=Long Rest}} {{@{selected|character_name} has completed a long rest}}
```
Or you can make a list of Players to affect:
```
!longrest Adran
!longrest Gargax Norixius
!longrest Lanor Tilde
!longrest Lukian Nastacia
!longrest Volen
!longrest Hootie

&{template:default} {{name=Long Rest}} {{[[1t[Longrest-Description]]]}}
```
In the above a random entry from the custom _Longrest-Description_ table is displayed as well for a bit of flavour.

## [Wild Magic Surge Tables](https://github.com/jfflbnntt/roll20-api-scripts/tree/master/WildMagicSurgeTables)
Rolls a d20 and, on a 20, rolls on the Wild Magic Surge table, displaying the result in the chat. For Wild Magic origin Sorcerers.

I've added this as an Ability to the character sheet as well as tacking it onto the end of spell descriptions via a button as below:

`[Wild Magic](!wildmagic)`

## [Bloodied and Dead Status Markers](https://github.com/Roll20/roll20-api-scripts/tree/master/Bloodied%20and%20Dead%20Status%20Markers)
Adds a red token marker when a token reaches the 'bloodied' status (<= 50% hp) and a black cross when the token reaches 0hp.

## API Check
```
on("ready", function() {
  sendChat('API', "/desc STARTED");
});
```

Adds a comment to the chat that the API has started - we completely ignore it until it doesn't appear in the chat when we start a game, at which point we know something has probably broken in the API service and to check the API Output Console for errors.

## [TimeTracker](https://github.com/capekfilip/roll20-scripts/blob/master/time-tracker)
Adds a clock comment into the chat (e.g. 17:30) to help all players and GM keep track of the in-game time. Can be used in Macros to create buttons for one-click increments eg:

```
# Set the time
!time -set ?{hours|00}:?{minutes|00}

# Add 30 minutes
!time -plus 0:30

# Add queried hours and minutes
!time -plus ?{hours|0}:?{minutes|0}

# Show the current in-game time
!time -show
```