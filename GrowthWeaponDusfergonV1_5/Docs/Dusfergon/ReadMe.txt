INSTALLATION

Install the files into your Oblivion\Data\ directory either manually or with your favorite mod manager.
Enable the .esp

UNINSTALLATION

Disable the .esp
Delete the Data\Docs, Data\Meshes\Weapons\Dusfergon, Data\Textures\Weapons\Dusfergon, Data\Textures\Menus\Icons\Dusfergon folders, Dusfergon.ini under Data\ini and GrowthWeapon_Dusfergon.esp.
Or use the mod manager you installed this mod with!

CREDITS

Suhoi72 - Bastard, Merciless, Wolf
noirq - Fixing the collision meshes for Suhoi72's swords
Lazarus89 - Somewhat Realistic Swords, Ivellon Dungeon
billryo - Serenity
Adonnay - Classical Weaponry, Classic Sword Replacer
Gardelin - Classic Sword Replacer Extended
Waalx - RealSwords Argonian, Bosmer, Khajiit, Orc, Dunmer, Breton, Redguard, Goblin, Nord
Alastor117 - Daedric katana
Andragorn - Mirondil, Sotonhorian, Thorgeir, Ziragon warhammers, battleaxes, maces, waraxes
Lexx666 - Sathix
tda Armoury - Akatosh
The MC - MC's Staff Pack
Havelock and Dorje - Staff of Magnus
talion - Staff of Chaos
Trollf - Armamentarium Staffs
Isilmeriel - Nazgul Sword Set

PERMISSIONS

Classical Weaponry and Serenity require permission from their respective authors to be used in your own works.

Tell me if you use my mod in something.  Not because you need permission, but because I want to see what cool thing it's being used for!
However, if the work is a paid product, you WILL need permission.



INSTRUCTIONS FOR TRANSFERING AGREMON'S PROGRESS

	Set aaDusfergonXP to aaAgremonXP

Dat's it.



INSTRUCTIONS FOR CHANGING LEVEL

METHOD 1

Make a Save.
Type into the console:

	Set aaDusfergonLevel to [int A]
	Set aaDusfergonXP to aaDusfergonXPReq
	Show aaDusfergonXPReq

With [int B] as the number you got from the last command,
load the Save you made at the start and type into the console:

	Set aaDusfergonXP to [int B]

This will take you through every enchant option select you
would have missed and had to compensate for with Method 2.

METHOD 2

Type ﻿into the console:

	Set aaDusfergonLevel to [int A]
	Set aaDusfergonEnch to [1-10]

And divide [int A - 11] (11 is the default level the enchants kick in) between:

	Set aaDusfergonEnch1 to [int B]
	Set aaDusfergonEnch2 to [int C]
	Set aaDusfergonEnch3 to [int D]
	Set aaDusfergonEnch4 to [int E]
	Set aaDusfergonEnch5 to [int F]
	Set aaDusfergonEnch6 to [int G]
	Set aaDusfergonEnch7 to [int H]
	Set aaDusfergonEnch8 to [int I]
	Set aaDusfergonEnch9 to [int J]
	Set aaDusfergonEnch10 to [int K]

then save and reload to force the stats to recalculate.

You'll also want to type:

	Set aaDusfergonXP to aaDusfergonXPReq

after reloading the save so the first level up doesn't take 8 years.


If you want to level down Dusfergon, make use of sBreakLevel in the ini.






















DESCRIPTION - SHORT, SPOILER FREE DESCRIPTION IS ON THE MOD PAGE
		THIS IS THE LONG ONE - YE HATH BEEN WARNED, SOUR SUMMER CHILD

-All values and keybindings listed are under default ini settings

Like Agremon and Shurifen before it, Dusfergon grows stronger with use in combat.

Initializing upon first starting Oblivion may take a couple seconds.  Until
initialized, Dusfergon will be in its default model and stats.  When Dusfergon
initializes "Dusfergon initialized!" will be output to the console and you will
hear it being equipped if you had it already equipped as the model swapper script
re-equips to force a refresh.

Once initialized, the script lag will be reduced to 0.5 seconds during gameplay
and 0.001 seconds during inventory menus.  Loading other saves after this point 
should result in instant initialization.



When equipped, an event handler will be set, looking for anytime a valid target
is hit with Dusfergon.  It will then see if the player is power attacking and
award appropriate XP.  The event handler is unset when Dusfergon is unequipped.


Bows are handled a bit differently, as you don't actually hit anything with a bow.
When equipped, an event handler is set, looking for anytime you release the bow
(fire an arrow).  That handler then checks your currently equipped ammo type and
sets an event handler looking for anytime anything is hit by the type of arrow
you just fired.  The second handler checks if the thing your arrow hit is a living 
NPC before awarding XP, it then removes itself regardless of whether the hit 
awarded XP or not.

There are a couple edge cases where this won't work as expected: 

1) If an arrow of the same type as the one you fired impacts something before yours 
does.  In this case it treats that arrow as yours instead of your own.

2) If you have multiple arrows airborne at the same time and they are of different
types.  The handler can only listen for one arrow type but its counter is 
incremented everytime you fire, so the counter will never reach 0 and the handler
never removed.

In the rare case (2) happens, you can drop Dusfergon, as that kills all handlers as
a workaround for this exact issue.


Staves are handled very differently, as again, you don't hit anything with a staff.
The handler is built into the staff's enchantment as a scripted effect and as such
fires everytime you hit something with the staff's magic.  It will do the same check
as an arrow for if the target is a living NPC before awarding XP.  This "handler" is
never unset because it's directly built into the enchantment.


The XP logger has been overhauled to give a final combat report instead of logging
every instance of XP gained and flooding your console log.  As soon as you hit a
target with Dusfergon, the event handler will mark the current XP value and flag
the combat logger.  When combat ends, the combat logger will print to console
A/B +CXP, where A is Dusfergon's current total XP, B is the total XP needed to
level up and C is the XP gained since the combat logger was flagged.  The level up
console message was also improved to show you what level Dusfergon is currently at
in the new format "Dusfergon leveled up to X!"



Dusfergon has a defualt level cap of 201, for 200 increases from Lv1.  The XP 
formula is the same as Agremon's, with the same default values as well.  The amount
of XP awarded per hit is 1 for a normal attack, 3 for a power attack, 3 for an
arrow hit and 2 for a staff hit.

XP Requirement formula:

( XPReqBase * aaDusfergonLevel ) + ( XPReqMult * ( aaDusfergonLevel * aaDusfergonLevel ) )
Where XPReqBase = 95 and XPReqMult = 5.

This will cause the XP required to level up go 100, 110, 120, 130, 140, etc.



At the halfway point to each level up, 1 of 6 random messages will appear.
(18%)	"Dusfergon itches..."
(18%)	"Dusfergon stirs..."
(18%)	"Dusfergon quivers..."
(18%)	"Dusfergon sips magicka..."
(18%)	"Dusfergon sheens..."
(10%)	"Dusfergon seethes..."

At level up, 1 of 6 random messages will appear.
(18%)	"Dusfergon seems a littler cleaner."
(18%)	"Dusfergon gleams satisfactorily."
(18%)	"Dusfergon rests comfortably in the hand."
(18%)	"Dusfergon feels a little heftier."
(18%)	"Dusfergon radiates ambient magicka."
(10%)	"Dusfergon grasps latent power."

At level cap a message box will appear, stating "Dusfergon has reached its apex."



Dusfergon will gain an enchantment at internal Lv11.  As soon as you're out of combat, 
a menu will appear prompting you to choose 1 of 10 options:  Fire, Ice, Volt, 
Knight-Slayer, Mage-Slayer, Weaken, Subjugate, Corruption, Unbalance and Siphon.  Each 
has their own effects, growth rates and costs.  See the ini file for full statistics on 
each effect, including base value, growth rate, base cost and cost growth rate.

The effects of each option are as follows:

Fire
Fire Damage		Weakness to Fire	Weakness to Magic

Ice
Frost Damage		Weakness to Frost	Weakness to Magic

Volt
Shock Damage		Weakness to Shock	Weakness to Magic

Knight-Slayer
Disintegrate Weapon	Disintegrate Armor	Damage Fatigue

Mage-Slayer
Damage Magicka		Dispel			Silence

Weaken
Burden			Drain Strength		Weakness to Magic

Subjugate
Command Creature	Command Humanoid	Rally

Corruption
Frenzy			Light			Soul Trap

Unbalance
Drain Agility		Damage Fatigue		Weakness to Magic

Siphon
Absorb Fatigue		Absorb Health		Absorb Magicka

Dusfergon has a Charge of 500 from the start, which is only used by the staff,
as it is the only form with an enchantment.  Once Lv11 is reached and all forms
gain an enchantment, Charge will increase by 75 every level.

Every 5 additional internal levels you will be prompted again in the same way to 
choose an enchantment.  Whichever enchantment you choose is the one that will grow 
as Dusfergon levels.  All other enchantments will cease to grow.  You can choose 
to pick a new option, your current option, or an old option.  Each effect has its 
own cost and cost growth associated with it, so selecting new options will also 
increase the cost of the enchantment, thereby reducing the uses.

Oblivion's engine displays a maximum of 8 effects in the UI, but allows for many more.
With as little as 3 options chosen, Dusfergon can have more than 8 effects on it.  As
such, you can Ctrl + RMB Dusfergon in your inventory or hold 9 ingame to bring up a 
message box displaying all effects.  It will have a scroll bar if necessary.

If the player decides to enchant Dusfergon, a message box will appear when Dusfergon
is selected in the enchanting menu: "Dusfergon rattles as if to resist enchantment."
If the player ignores the warning and goes through with enchanting, all handlers are
unset and the enchantment is undone, the soulgem or sigil stone refunded -- unless 
it's Azura's Star.



When Dusfergon breaks, it's level will be reset to 1, undoing all enchantments and 
reseting XP to 0.  This is configurable in the ini, allowing this feature to either
be disabled or changed to a fixed level reduction.  In the case of fixed level reduction,
the enchantment options will be cycled through and reduced by 5 levels where applicable,
and setting the active enchantment to the last option reduced.  As breaking your weapon
in Oblivion is exceptionally rare, the default punishment is harsh.

Of note with the delevel function:  Oblivion unequips weapons when their durability is
less than 0, so the scripts check Dusfergon's health on unequip and subsequently flag for
delevel.  There are a couple instances, namely with Disintegrate Weapon on Self effects,
where the weapon's durability can be reduced to 0 but not automatically unequipped.



Dusfergon can change form to suit the wielder.  Specifically, RMB Dusfergon in your
inventory to bring up a menu of weapon types; Choosing one will take you to a menu
for sub-types, and finally a menu for various forms.  As of V1.1, you can Cancel or
go back a page in your selection.  This has also greatly expanded the number of 
forms allowed, so you will find multiple sub-types have multiple pages of forms.
Dusfergon's stats will adjust according to the sub-type chosen.

As of V1.5, for ease of use you can hold V ingame to quickswap back to the last
form Dusfergon held.  With this, you can more easily change between melee and
ranged forms in combat.

Due to the sheer number of forms, a Random option is available in the first menu.
It will pick a sub-type first, then specific form, so you have an equal chance of
each sub-type appearing.  You can also activate the Random option from ingame by
holding down G.

Incase you like the form Random chose and want to change to it later, Shift+RMB 
Dusfergon in your inventory or hold 0 ingame to receive a message stating 
"Dusfergon's current form is [name] ([sub-type menu])."


The sub-types ordered by main-type are:

2H - Blade
Claymore	- 1.3 reach, 0.8 speed, highest damage of all Blade, longest reach of all sub-types;
		  The base sub-type, all stat changes are relevant to this one
Bastard2H	- 0.2 shorter, 0.2 faster, slightly less damage, like a 2H Longsword

2H - Blunt
Warhammer	- 0.4 shorter, negligibly slower, highest damage of all sub-types
Battleaxe	- 0.4 shorter, 0.1 faster, second highest damage of all sub-types

1H - Blade
Bastard1H	- 0.2 shorter, 0.1 faster, slightly less damage, little slower b/c shield
Longsword	- 0.3 shorter, 0.2 faster, moderatly less damage, all-rounder
Shortsword	- 0.5 shorter, 0.4 faster, significantly less damage, balance of speed and power
Dagger		- 0.7 shorter, 0.6 faster, half damage, fastest of all sub-types

1H - Blunt
Mace		- 0.5 shorter, 0.1 faster, very slightly less damage, highest damage of all 1H
Waraxe		- 0.5 shorter, 0.3 faster, somewhat less damage, shortsword of Blunt

Bow		- 0.2 faster, significantly less damage, but very slightly more than Shortsword

Staff		- 0.2 faster, somewhat less damage, makes the enchantment area of effect

The specific stat adjustments can be found in the ini file.

The base stat increments per level up are:

Damage	Reach	Speed	Weight	Health	Value
0.5	0	0.003	0.5	30	115



In addition, you will find transcripts of all code written for this mod in Data\Docs\Dusfergon\Scripts.