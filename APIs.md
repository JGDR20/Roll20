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