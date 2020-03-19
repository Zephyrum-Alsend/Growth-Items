REQUIREMENTS

OBSE

INSTALLATION

Extract the files to your Oblivion/Data/ directory manually or with your favorite mod manager.
Enable the .esp.

UNINSTALLATION

Disable the .esp.
Delete the /Meshes/Weapons/Wolf/ folder, /Textures/Weapons/Wolf/ folder, Data/Docs folder and the .esp.

CREDITS

Suhoi72 for creating the beautiful model and textures used in this mod, 2h sword - Wolf
noirq for fixing the collision mesh
OBSE Team for documenting everything in OBSE
shadeMe for making life easy(er) with the Construction Set Extender
Bethesda for giving us hackerman tools

MID PLAYTHROUGH CATCHUP COMMANDS

Where X is the player's level...
Set aaAgremonLevel to ( X - 1 )
Save and load the new save.
Set aaAgremonXP to aaAgremonXPReq
That's it!























DESCRIPTION - TURN BACK NOW, LEST YE BE BURDENED WITH KNOWLEDGE

Agremon grows with usage.  It gains XP every time you hit a valid target with the sword.
Agremon gains 1 XP from attacks and 3 XP from power attacks.  Acquired XP is logged in the
console as "XP +X Y/Z" Where X is the XP earned from the last strike, Y is the total XP
Agremon has earned over its lifetime, and Z is the total XP needed to level up.  Agremon
will level up as soon as the XP threshold is passed, even while in combat.  CurrentHealth
is not updated to the new BaseHealth, so Agremon's durability percentage will lower a
little every level up.

The game checks script conditions every half second, so level ups and other features may
not happen immediately as their conditions are fulfilled.

The sword's stats will be that of an iron claymore until the manager script initializes.
"Agremon initialized!" will be logged in the console when this happens.  It shouldn't take
more than 2 seconds, often happening in half a second, unless your game is heavy on scripts.

Upon first receiving Agremon, you will receive a message stating "A depleted artifact selects
a new owner..." and "Agremon added to player!" will be logged in the console.

At the halfway point to each level up, you will receive one of four messages:
"Agremon groans..."
"Agremon warms a little..."
"Agremon itches..."
"Agremon stirs..."
Each with an equal chance of appearing.

At level up, you will receive one of four messages, all with equal chance of appearing:
"Agremon reclaims a fragment of lost power."
"Agremon restructures."
"Agremon adjusts to your hand slightly."
"Agremon grasps latent strenght."

Upon reaching the level cap, you will receive a message box stating:
"Agremon has achieved full glory!"

If you try to enchant Agremon, you will receive a warning message box:
"Agremon quivers as if to resist enchantment."

If you go through with enchanting Agremon:
"[new name] silently screams as it is rendered inert."
The scripts will cease to function at this point.

Due to the game checking the conditions every half second, if you move through the enchanting
menu fast enough, these may fail to appear or appear erroneously.

XP acquisition is handled by an OBSE "OnHitWith" event handler, looking for Agremon.  Level
ups are performed when two conditions are met: 1) Agremon is not max level 2) Agremon's total
XP meets or excedes the total required XP.  Due to this check being a While loop, Agremon can
level up multiple times simultaneously if enough XP is gained.  Agremon will continue to log
XP past the level cap and due to the current implementation, if the cap is ever raised,
Agremon will instantly level to its new level without any wasted XP.

The simple formula for XP required is:
XPReqBase + ( XPReqMult * ( aaAgremonLevel - 1 ) )
Where XPReqBase = 100 and XPReqMult = 10.  aaAgremonLevel is incremented every level up.
The starting XP requirement is 100 ( 100 + ( 10 * ( 1 - 1 ) ) ).
The actual formula used to calculate total XP required is:
( XPReqBase * aaAgremonLevel ) + ( XPReqMult * ( aaAgremonLevel * aaAgremonLevel ) )
Where XPReqBase = 95 and XPReqMult = 5.
Agremon has a starting level of 1 and level cap of 201, for 200 level ups.

Agremon's base stats are:
Weight 10	Health 150	Value 50	Attack 12	Speed 0.8	Reach 1.3

Each level, these stats are incremented by:
Weight 0.5	Health 30	Value 115	Attack 0.5	Speed 0.005	Reach 0

As of level 11, Agremon will gain an enchantment. The related base stats are:
Fire Damage	4pts
Fire Weakness	40%	4sec
Magic Weakness	20%	4sec
Cost		31
Charge		500

Each level, these stats are incremented by:
Fire Damage	0.2pts
Fire Weakness	2%	0sec
Magic Weakness	1%	0sec
Cost		0.1
Charge		50

As of the current level cap of 201, Agremon's final stats will be:
Weight 110	Health 6150	Value 27070	Attack 112	Speed 1.8	Reach 1.3
Fire Damage	42pts
Fire Weakness	420%	4sec
Magic Weakness	210%	4sec
Cost		50
Charge		10000