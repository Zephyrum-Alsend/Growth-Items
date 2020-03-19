INSTALLATION

Install the files into your Oblivion\Data\ directory either manually or with your favorite mod manager.
Enable the .esp

UNINSTALLATION

Disable the .esp
Delete the Data\Docs, Data\Meshes\Weapons\Dusfergon, Data\Textures\Weapons\Dusfergon, Data\Textures\Menus\Icons\Dusfergon folders, Dusfergon.ini under Data\ini and GrowthWeapon_Dusfergon.esp.
Or use the mod manager you installed this mod with!

CREDITS

Suhoi72 - Bastard, Merciless, Wolf, Wolf Ricasso
noirq - Fixing the collision meshes for Suhoi72's swords
Lazarus89 - Type-A/B/C/D/E, Warhammer, Arming Sword, Zweihander
billryo - Serenity
Adonnay - Kinslayer, Sorrow, Despair, Maul, Iron/Fine Iron/Steel/Fine Steel/Silver/Ebony longswords
Gardelin - Iron/Fine Iron/Steel/Fine Steel/Silver/Ebony shortswords and daggers
Waalx - Gotland, Clint XVI, Angular Leaf, Flanged Bronze/Steel, Goblinstar, Macil, Mormacil, Morningstar Bronze/Steel warhammers and maces, Bearded/Fine Bearded/War battleaxes and waraxes, Rhino, Stiletto, Spike, Claw, Elvin, Baskethilt, Moonbrand, Thame, Eagle, Elhazan, Falshion, Seaward
Alastor117 - Daedric katana
Andragorn - Mirondil, Sotonhorian, Thorgeir, Ziragon warhammers, battleaxes, maces, waraxes
Lexx666 - Ice, Fire
tda Armoury - Akatosh

PERMISSIONS

Serenity, Kinslayer, Sorrow, Despair and Maul require permission from their respective authors to be used in your own works.

Tell me if you use my mod in something.  Not because you need permission, but because I want to see what cool thing it's being used for!
However, if the work is a paid product, you WILL need permission.



INSTRUCTIONS FOR CHANGING LEVEL

Type ﻿into the console:

Set aaDusfergonLevel to [intA]
Set aaDusfergonEnch to [1-5]

And divide [intA - 11] from the Level number before between

Set aaDusfergonEnch1 to [intB]
Set aaDusfergonEnch2 to [intC]
Set aaDusfergonEnch3 to [intD]
Set aaDusfergonEnch4 to [intE]
Set aaDusfergonEnch5 to [intF]

then save and reload to force the stats to recalculate.

You'll also want to type:

Set aaDusfergonXP to aaDusfergonXPReq

after reloading the save so the first level up doesn't take 8 years.























DESCRIPTION - SHORT, MECHANIC SPOILER FREE DESCRIPTION IS ON THE MOD PAGE
		THIS IS THE LONG ONE - YE HATH BEEN WARNED, SUMMER CHILD

Like Agremon and Shurifen before it, Dusfergon grows stronger with use in combat.

Initializing upon first starting Oblivion may take a couple seconds.  Until
initialized, Dusfergon will be in its default model and stats.  When Dusfergon
initializes "Dusfergon initialized!" will be output to the console and you will
hear it being equipped as the model swapper script re-equips to force a refresh.

Once initialized, the script lag will be reduced to 0.01 seconds.  Loading other
saves after this point should result in instant initialization.



When equipped, an event handler will be set, looking for anytime a valid target
is hit with Dusfergon.  It will then see if the player is power attacking and
award either 1XP or 3XP.  The event handler is unset when Dusfergon is unequipped.

The XP logger has been overhauled to give a final combat report instead of logging
every instance of XP gained and flooding your console log.  As soon as you hit a
target with Dusfergon, the event handler will mark the current XP value and flag
the combat logger.  When combat ends, the combat logger will print to console
A/B +CXP, where A is Dusfergon's current total XP, B is the total XP needed to
level up and C is the XP gained since the combat logger was flagged.  The level up
console message was also improved to show you what level Dusfergon is currently at
in the new format "Dusfergon leveled up to X!"



Dusfergon has a defualt level cap of 201, for 200 increases from Lv1.  This is configurable
in the .ini file.  The only limit is how larger a number a short int can store (which is
32767).  The XP formula is the same as Agremon's, with the same default values as well.
These values are also configurable in the .ini.

( XPReqBase * aaDusfergonLevel ) + ( XPReqMult * ( aaDusfergonLevel * aaDusfergonLevel ) )
Where XPReqBase = 95 and XPReqMult = 5.

This will cause the XP required to level up go 100, 110, 120, 130, 140, etc.



At the halfway point to each level up, 1 of 5 random messages will appear.
(15%)	"Dusfergon sharpens on your foe..."
(20%)	"Dusfergon stirs..."
(25%)	"Dusfergon rattles faintly..."
(15%)	"Dusfergon quenches in your foe..."
(25%)	"Dusfergon gathers magicka..."

At level up, 1 of 5 random messages will appear.
(23%)	"Dusfergon looks a littler cleaner."
(23%)	"Dusfergon feels more comfortable."
(23%)	"Dusfergon adjusts in the hand."
(23%)	"Dusfergon seems a little heftier."
(8%)	"Dusfergon grasps latent power."

At level cap a message box will appear, stating "Dusfergon has reached its apex."



Dusfergon will, under default .ini configuration, gain an enchantment at internal
Lv11.  As soon as you're out of combat, a menu will appear prompting you to choose
1 of 5 options:  Fire, Ice, Volt, Knight-Slayer and Mage-Slayer.  Each has their
own effects, growth rates and costs.  See the .ini file for full statistics on
each effect, including base value, growth rate, base cost and cost growth rate.

The effects of each option are as follows:
Fire
Fire Damage	Weakness to Fire	Weakness to Magic
Ice
Frost Damage	Weakness to Frost	Weakness to Magic
Volt
Shock Damage	Weakness to Shock	Weakness to Magic
Knight-Slayer
Damage Fatigue	Disintegrat Weapon	Disintegrate Armor
Mage-Slayer
Damage Magicka	Dispel			Silence

At Lv11, Dusfergon will have a Charge of 500, which will increase by 75 every level.

By default, every 10 additional internal levels you will be prompted again in the
same way to choose an enchantment.  Whichever enchantment you choose is the one
that will grow as Dusfergon levels.  All other enchantments will cease to grow.
You can choose to pick a new option, your current option, or an old option.  Each
effect has its own cost and cost growth associated with it, so selecting new options
will also increase the cost of the enchantment.

Oblivion's engine displays a maximum of 8 effects in the UI, but allows for many more.
With as little as 3 options chosen, Dusfergon can have more than 8 effects on it.  As
such, you can Ctrl+RMB Dusfergon in your inventory to bring up a message box displaying
all effects.  It will have a scroll bar if there are enough effects.

If the player decides to enchant Dusfergon, a message box will appear when Dusfergon
is selected in the enchanting menu: "Dusfergon rattles as if to resist enchantment."
If the player ignores the warning and goes through with enchanting, all handlers are
unset and the scripts can no longer track the new ID Dusfergon was given.  The message
box "[new name]'s latent power is overwritten." will also appear.



Dusfergon can change form to suit the wielder.  Specifically, RMB Dusfergon in your
inventory to bring up a menu of weapon types; Choosing one will take you to a menu
for sub-types, and finally a menu for various forms.  You cannot cancel or go back
once the menus have started.  Adding that at this point will require a significant
recoding of the backend for form selection.  Due to the engine limitation of 10
buttons max per message box, there can only be up to 10 options per sub-type.
Dusfergon's stats will adjust according to the sub-type chosen.

The sub-types ordered by main-type are:
Claymore	- The base sub-type, all stat changes are relevant to this one
Bastard2H	- Slightly shorter, slightly less damage, longsword swing speed
Warhammer	- Shortsword reach, highest damage of all sub-types, very slightly slower than base
Battleaxe	- Slightly longer than Warhammer, second highest damage, half-way between base and longsword in speed
Bastard1H	- Same as Bastard2H except speed is now same as Battleaxe to compensate for presence of shield
Longsword	- Very slightly less damage than Bastard, longsword reach and speed
Shortsword	- Shortsword reach, balance of damage and speed, less than longsword but faster
Dagger		- Shortest reach, half damage of base, fastest of all sub-types
Mace		- Shortsword reach, very slightly less damage than base, same speed as Battleaxe/Bastard1H
Waraxe		- Shortsword reach, slightly less damage than mace/very slightly less than Bastard, speed half-way between longsword and shortsword

The base and growth stats as per default .ini configuration are:

		Damage	Speed	Reach	Weight	Value
Base		12	0.8	1.3	10	50
Growth		0.5	0.005	0	0.5	115
The sub-type adjustments are:
Claymore	0	0	0
		0	0	0
Bastard2H	-1	0.2	-0.15
		-0.05	0.001	0
Bastard1H	-1	0.1	-0.15
		-0.05	0.0005	0
Longsword	-2	0.2	-0.3
		-0.075	0.001	0
Shortsword	-4	0.4	-0.5
		-0.14	0.002	0
Dagger		-6	0.6	-0.7
		-0.25	0.003	0
Warhammer	3	0	-0.5
		0.18	-0.0005	0
Battleaxe	1	0.1	-0.4
		0.1	0	0
Mace		-1	0.1	-0.5
		-0.02	0.0005	0
Waraxe		-3	0.3	-0.5
		-0.07	0.0015	0

The stat adjustments per sub-type are also configurable in the .ini, alongside the base stats.