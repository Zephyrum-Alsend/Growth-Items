REQUIREMENTS

OBSE

INSTALLATION

Extract the files to your Oblivion/Data/ directory manually or with your favorite mod manager.
Enable the .esp.

UNINSTALLATION

Disable the .esp.
Delete the /Meshes/Weapons/Merciless/ folder, Textures/Weapons/Merciless/ folder and the .esp.

CREDITS

Suhoi72 for creating the fabulous model and textures used in this mod, Merciless - 2h sword
noirq for fixing the collision mesh
OBSE Team for making this possible with OBSE
shadeMe for making the wonderful Construction Set Extender
Bethesda for giving us hackerman tools





















DESCRIPTION

THIS IS THE FULL STAT DESCRIPTION. ONLY READ IF YOU WANT TO KNOW THE INTERNAL WORKINGS OF THE MOD.

Shurifen is a weapon that grows with usage.  It gains XP every time you hit a valid target with the sword.
Shurifen gains 1 XP from attacks and 3 XP from power attacks.  XP acquired is logged in the console, in the
form of "XP +X!  Y/Z" Where X is the XP earned from the most recent strike, Y is the current total XP
accrued, and Z is the total XP required to reach the next level.  "Level up flag set!" will be logged when
the XP threshold is passed.  After which, as soon as you exit combat and have Shurifen in your inventory
(equipped or not), it will upgrade to the next version.

The mod also outputs messages at milestones to each level and when each level up is ready.
1/4th XP required: "Shurifen cuts a bit finer."
2/4th XP required: "Shurifen sharpens itself on your foe."
3/4th XP required: "Shurifen quenches itself in your foe."
XP required met:   "Shurifen prepares to reforge itself..."
Upon leveling:     "Shurifen reforges itself."

Upon first receiving the sword, you will get the message "A shard of power finds it's way into your 
belongins..."

After reaching Shurifen's level cap, you will receive a message box stating "Shurifen has reforged a final 
time."

XP acquisition is handled by an OBSE OnHitWith handler, set to look for the current version of Shurifen you
have equipped.  Upon leveling, the script will check 4 things: that you don't have the max level variant; 
the level up flag is set; you aren't in combat or riding; you have an instance of Shurifen.  Taking more 
instances out of the cheat chest will still log XP fine, but level ups will upgrade the lowest tier
version of Shurifen, regardless of the level you were working on.  The new XP requirement will be set to 
that of the lower tier, though.

XP required per level is determined by the formula:
BaseRequirement + ( aaShurifenLevel * LevelMult )
Where BaseRequirement = 200 and LevelMult = 200.  aaShurifenLevel is set during level up according to the
version upgraded.  Upgrading the Level 1 version will set aaShurifenLevel to 2 and upgrading the Level 95
version will set aaShurifenLevel to 21 (There are 21 versions).  The starting XP requirement is 400 
(200 + ( 1 * 200 )).

Shurifen will continue to log XP beyond Level 99, despite being at the cap.  As such, if the cap is ever
raised, Shurifen will immediately upgrade to the next tier.  XP is not carried over between levels, so
multiple level ups is not possible.

Shurifen has a fixed Speed of 0.9 and Reach of 1.3 (same reach as Claymore, inbetween Longsword and 
Claymore on speed).  The enchantment always has 50 uses.

The stats for each tier of Shurifen:
Level	Weight	Health	Base Value	Attack	Charge	Enchant
01	10	150	100		12
05	13	220	250		15
10	16	290	500		18	500	Shock Damage 4	Weakness to Shock 70	Weakness to Magic 35
15	19	500	1000		21	1000	Shock Damage 6	Weakness to Shock 80	Weakness to Magic 40
20	22	600	2000		24	1500	Shock Damage 8	Weakness to Shock 90	Weakness to Magic 45
25	25	750	4000		27	2000	Shock Damage 10	Weakness to Shock 100	Weakness to Magic 50
30	28	900	8000		30	2500	Shock Damage 12	Weakness to Shock 110	Weakness to Magic 55
35	31	1050	16000		33	3000	Shock Damage 14	Weakness to Shock 120	Weakness to Magic 60
40	34	1200	32000		36	3500	Shock Damage 16	Weakness to Shock 130	Weakness to Magic 65
45	37	1350	64000		39	4000	Shock Damage 18	Weakness to Shock 140	Weakness to Magic 70
50	40	1500	72000		42	4500	Shock Damage 20	Weakness to Shock 150	Weakness to Magic 75
55	43	1650	84000		45	5000	Shock Damage 22	Weakness to Shock 160	Weakness to Magic 80
60	46	1800	96000		48	5500	Shock Damage 24	Weakness to Shock 170	Weakness to Magic 85
65	49	1950	108000		51	6000	Shock Damage 26	Weakness to Shock 180	Weakness to Magic 90
70	52	2100	120000		54	6500	Shock Damage 28	Weakness to Shock 190	Weakness to Magic 95
75	55	2250	132000		57	7000	Shock Damage 30	Weakness to Shock 200	Weakness to Magic 100
80	58	2400	144000		60	7500	Shock Damage 32	Weakness to Shock 210	Weakness to Magic 105
85	61	2550	156000		63	8000	Shock Damage 34	Weakness to Shock 220	Weakness to Magic 110
90	64	2700	168000		66	8500	Shock Damage 36	Weakness to Shock 230	Weakness to Magic 115
95	67	2850	180000		69	9000	Shock Damage 38	Weakness to Shock 240	Weakness to Magic 120
99	70	3000	192000		72	9500	Shock Damage 40	Weakness to Shock 250	Weakness to Magic 125