Growth Armor Zefiros V1.1


DEFAULT CONTROLS

highlight Zefiros item in your inventory
RMB - Options menu
RMB+SHFT - Get current form name
RMB+CTRL - Popup with all enchantment stats

highlight not Zefiros item in your inventory
RMB - Offer to Zefiros
RMB+SHFT - Mimic


INSTALLATION
Recommended to use a mod manager like Vortex or Wrye Bash.
Extract the archive's contents into your Oblivion/Data/ folder.
Enable the .esp.

UNINSTALLATION
Disable the .esp.
Delete Data/Docs/Zefiros/, Data/ini/Zefiros.ini, Data/Meshes/Zefiros/, Data/Textures/Zefiros/, Data/Textures/menus/icons/Zefiros/, Data/Textures/underworld/, Data/Textures/Dragonknight/, Data/Textures/armor/MilanPlateArmor/,
Data/Textures/armor/Daedric/F/cuirass_g.dds, Data/Textures/armor/Daedric/M/cuirass_g.dds, Data/Textures/armor/Daedric/M/helmet_g.dds, Data/Textures/armor/Daedric/M/Skyrimhelmet.dds, Data/Textures/armor/Daedric/M/Skyrimhelmet_g.dds, and Data/Textures/armor/Daedric/M/Skyrimhelmet_n.dds.
Or use the mod manager you installed this with!


KNOWN ISSUES
-Without the recommended mods, some modded armors may look odd.
-Leveling up leaves you naked for 1 frame.
-Environmental damage and self harm are the same thing.
-When offering armor, the highest durability instance will be consumed.


REQUIREMENTS
OBSE - scripts scripts scripts scripts scripts scripts scripts scripts scripts scripts scripts
Universal Skeleton - Movomo's Daedric armor and Local Guards Features require it


RECOMMENDED
HG EyeCandy Body
Robert Male Body


CONFLICTS
Some of the meshes crash NifSkope, so I cannot relocate this mod's texture files into their own folder like Dusfergon.
When installing other mods that include armor, they may overwrite some of Zefiros's textures.
No textures were edited from their original mods so overwriting should have no impact.


PERMISSIONS
If it's free, use it with appropriate credit given.
If it's paid, cut me a share of profits.
Regardless, notify me so I can check out the final product!


CREDITS
Pike9 - Witcher 2 Plate Armor
IKirostI - Daedricious Armor Replacer﻿
Movomo - Movomo's Armor Replacer - The Very Daedric Armor﻿
McMuffin - Daedric Lord Armor﻿
Phitt & Ghogiel - Knightly Armory﻿
ElderScrollsFan001 - Witcher 2 Shields and Helmets Packs for Oblivion﻿, Elderscrollsfan001s Resources﻿
zertual - Underworld Armor﻿
ken1945 - Draonknight Armor﻿
alphaprime_01 - Medieval Shields﻿
navinavi - Knight Plate Armor﻿
Krassus222 - Shield 2Womens and Cat﻿
VanillaBeans - Plate of the Shadow﻿
Renzeekin - Concealing Hoods﻿
Stavroguin - Imperial Dragon Armor Reforged﻿
tbsk - Local Guards Features﻿﻿
Mixxa77 - LGF Kvatch Addon﻿, LGF Thorn Addon











































EXTENDED DESCRIPTION
THIS IS BASICALLY A SUMMARY OF THE CODE
values and names are with default ini settings

Zefiros is the armor implementation of Dusfergon.  It is an armor set that grows with use
in combat.

Zefiros is just leather armor with iron stats until Oblivion runs the mod's scripts.  This
may take a few seconds or it may happen instantaneously.  However, once running the script
lag can be set, and set it is to 0.5 seconds in GameMode and 0.01 seconds in MenuMode.
This latency will stick throughout the session, so further loading of saves will result in
initialization within 0.5 seconds.

During initialization Zefiros rebuilds all data arrays and recalculates stats before
finally setting the appearance.  Once the appearance is set, the items are re-equipped to
apply all changes, inventory UI refreshed and "Zefiros initialized!" output to console.
The collective name used in messages is either str_Prefix or "Armor " + str_Postfix if
str_Prefix is empty.

There are insufficient tools for equipping items silently so you will hear the armor equip
SFX each time a re-equip happens.  Additionally, re-equips during GameMode leave the 
player naked for 1 frame.  Unequipping then equipping armor on the same frame during
GameMode causes EquipItem to fail.  To bypass this engine bug, a 1 frame delay was 
inserted.

Upon first initialization, Zefiros will be added to the player's inventory alongside a
flavor message in the upper left.

The INI is read when a save is loaded, so exiting the game is not required for changes to
take effect.  The INI is also not required, as the default values are loaded by the mod
prior to attempting to read the INI.





Zefiros gains XP from the player taking damage.  The listeners which track damage taken
are only active while a piece of Zefiros is equipped.  XP gained is also multiplied by
the number of pieces worn.  All pieces share the same level and XP pool so wearing them
all is not required to grow, but will expedite it.

The listeners track how much damage you take, what magic effects you were hit by, what
diseases are caught, and whether the weapons hitting you ignore Normal Weapon Resistance
or not.  Because the tools either aren't available or aren't reliable, the mod does not
determine exactly how much damage of each type you were hit by (i.e. 32 pts Fire, 68 pts
Physical).  Instead it evaluates total damage taken every 0.1 seconds and evenly 
attributes it to each type (i.e. 50 pts Fire, 50 pts Physical).

This damage type tracking is used for dynamic resistances, where as you take elemental
damage the armor grows resistance to that element.  Fire, frost, shock, magic, paralysis,
disease, and normal weapon resistances can be grown.  In lieu of the player not equipping
the full set, each piece will gain 1% resistance simultaneously instead of staggered or
exclusive.  This means resistances will increment by 5% if the full set is worn (shield
is excluded from dynamic resistances) and XP required is adjusted accordingly.

Non-damaging but hostile magic effects will award a small fixed amount towards magic 
resistance, as non-elemental magic damage is rather uncommon.
Diseases and paralysis are non-damaging, but can be detected with tools available, 
therefore making dynamic disease and paralysis resistance possible.  Do note weaponry
Master perks ignore paralysis resistance.

To prevent exploiting this system by self harming with spells, a check is made to 
determine the damage was not self harm.  Unfortunately, Oblivion treats damage from the
environment (falling, traps) the same as self harm, and won't count towards XP either.
There is a toggle in the INI to disable this check, allowing both sources to count.

While great pains have been taken to ensure listeners are properly set and unset, a 
failsafe has also been implemented whereby dropping a Zefiros item forces the mod to
re-evaluate the listeners' states.





When the XP requirement is met or exceded, Zefiros will level up, increasing AR, weight,
value and durability.  The stat scaling and XP curve is designed to approximate the 
player's own growth, with Zefiros matching Daedric when it's Lv26 (starting at Lv1) and
the player is also finding Daedric gear.  "Zefiros is level X!" will be output to console
on level up and a randomized flavor message will appear in the upper left.  A flavor
message will also appear when the halfway point to the next level is passed.

XP is cumulative rather than per level, so overflow carries over.
The XP requirement formula is:
XPReq = ( XPBase * Lvl ) + ( XPMult * Lvl * ( Lvl - 1 ) / 2 )
Each level will require XPBase + ( XPMult * Lvl ) to advance.

At the end of combat, XP gained will be output to console in the format
"XP / XPReq	+ XPGain	Damage taken."

At Lv11 Zefiros will seek an enchantment, prompting the player to choose from a list of
effects.  One effect can be chosen per piece and the player gets to choose again every
5 levels thereafter.

Dynamic resistances will also not appear until this point, so the player can repair
Zefiros.  This can be toggled in the INI.

The effects available are:
Fortify Strength	Fortify Intelligence	Fortify Willpower	Fortify Agility
Fortify Speed		Fortify Endurance	Fortify Personality	Fortify Luck
Fortify Blade		Fortify Blunt		Fortify Hand to Hand	Fortify Armorer
Fortify Block		Fortify Heavy Armor	Fortify Athletics	Fortify Acrobatics
Fortify Light Armor	Fortify Security	Fortify Sneak		Fortify Marksman
Fortify Mercantile	Fortify Speechcraft	Fortify Illusion	Fortify Alchemy
Fortify Conjuration	Fortify Mysticism	Fortify Destruction	Fortify Alteration
Fortify Restoration	Fortify Fatigue		Fortify Health		Fortify Magicka
Restore Fatigue		Restore Health		Restore Magicka
Shield			Feather

Where the shield is excluded from dynamic resistances, it gains exclusive access to
Reflect Damage, Reflect Spell and Spell Absorption effects.

Zefiros can level down as well, in the event 3 or more parts are broken.  In the event
of a level down, 10 levels are lost, XP is reduced and all effects grown in that time are 
undone.  Zefiros keeps track of every effect choice the player makes and undose them 
exactly like a Ctrl+Z.  "Zefiros is level X!" will be output to console and a message box
containing randomized flavor text will appear too.  There is a different pool of messages
for when Zefiros goes down to Lv1.

A message box will appear when the level is capped, again with randomized flavor text.
The level cap is 201, for 200 level ups.  But the cap can be set to dynamic in the INI,
instead locking step with the player's level, fame or armor skills.





Zefiros has numerous functions accessible from the Inventory menu.  Right-clicking any
Zefiros item will bring up an options menu with the choices "Save Set", "Load Set",
"Form", "Form ALL", "Random", "Random ALL", "Weight" and "Weight ALL".


Form allows you to change the appearance of the armor piece.  Given the sheer number of
meshes included, a table of contents was implemented to shorten navigation time.  This
will appear first when you click on Form.  Each button will list a page range which it
will take you to.  Once within a page range, you can select a name to equip that form or
page through the range with [<Prev] and [Next>].  If at any point you page outside the
range, whether backwards or forwards, you will be returned to the table of contents.

At any point clicking on [Cancel] will exit out of the options menu entirely, regardless
of where in the process you are.

The size of the page ranges in the ToC can be changed in the INI.  However, the ToC will
increase the range size if necessary to fit all ranges within the 8 buttons it has.  If 
the range size is 0 or less or is so large as to include all pages, the ToC will be 
skipped and you'll go straight into the pages.

It is possible to select multi-slot forms from the list (such as robes), which will merge
the relevant items together into one, combining stats and enchantments.  Level changes
take into account these merged items.  If the required items for the merge are not present
in the player's inventory, a message will display in the upper left stating that it failed
and which item is missing.  If multiple items are missing, only the first discovered
missing will be stated in the message.


Form ALL is much the same as Form however instead of individual meshes it contains sets
of meshes.  Picking an option from here will equip multiple appearances at once across
multiple parts.  E.G. Choosing "Iron" will equip the full iron set.  Not all options here
touch all pieces.  E.G. "Imperial Dragon" does not have a shield and so will not change
it.


Save Set gives you 8 slots to save custom appearances to.  When choosing a slot it will
save the current appearance of every item to it.  A scroll SFX will play alongside a
message in the upper left.


Load Set allows you to equip the custom sets you created with Save Set.  Until populated
they are all iron armor.  A scroll SFX will play alongside a message in the upper left.


Random randomly selects an entry found in Form and equips it.


Random ALL is Random but applied to all Zefiros items simultaneously.  The results
sometimes turn out surprisingly good.


Weight allows you to change the item's type between Light and Heavy.  The stats will be
changed based on the selection, with Heavy having 50% more AR and 100% more weight than
Light.  For reference, vanilla Heavy armor has 50% more AR and 300% more weight than 
Light.


Weight ALL allows you to change the type of all Zefiros items with one selection.


Shift + Right-click will display the equipped form's name as it is found under the Form
pages.  This is useful for answering "what armor is that?" or finding out what Random
equipped.


Control + Right-click will display a message box containing all enchantment information
for that Zefiros item.  Oblivion's UI only shows up to 8 magic effects, which Zefiros can
handily excede.


Right-clicking a non Zefiros item will display a message box prompting the player to offer
that item to Zefiros.  Offering items will convert the armor into XP and repair Zefiros
slightly.  The higher the armor's durability, the more value it has to Zefiros.  Enchanted
armors grant substantially more XP.  "XP / XPReq	+ XPGain	Item offered."
will be output to the console alongside an item break SFX and randomized flavor message
in the upper left.  Aside from selling, this is another reason to continue looting.
Items cannot be offered once Zefiros is at its level cap.

Due to the coding of Oblivion's inventories, the exact item you are highlighting cannot be
gotten.  However the base item can be gotten and from there all inventory references to
said item.  At this point, all that can be done is pull out the first inventory reference,
which also happens to usually be the highest durability reference.


Shift + Right-clicking a non Zefiros item will copy its appearance onto the corresponding
Zefiros item.  Boots to boots, shields to shields.  Mimicked appearances are stored in a
specially designated slot with names ending in " (Mimic)".  This slot can be found under
Form p.1 and have their cumulative set selectable under Form ALL p.1.  Mimicked 
appearances can be swapped to and from without the need of the original item(s) due to 
this storage.  However, there is only 1 mimic slot per Zefiros item, so mimicking other 
items will overwrite this slot.

As there are no amulet, ring or tail items in Zefiros, those such items cannot be 
mimicked.  However, because Zefiros can mimic multi-slot items, if the one in question
occupies the head, amulet and tail slots, it can be mimicked by Zefiros's helmet.  The
helmet will then take up those same 3 slots.

Mimicry creates a soft dependency upon the mod the mimicked item comes from.  Zefiros
saves the file paths to those meshes, and so does not need the mod's .esp to be active,
but does need the files to be installed.  Uninstalling the files will not break Zefiros,
however.  This is because mimicry data is validated during initialization and reset if
found to be invalid.


Zefiros's currently equipped form and all custom outfits are also validated upon
initialization.  This is done using the fact that all names in each Form registry are
unique, thereby making custom and equipped outfits index agnostic.  What that means is if
the ordering of the lists ever changed, your custom and currently equipped outfits will
remain the same.  The one exception lies in deletions and renaming, in which event the 
validation will default your outfit to iron if it fails.





If the player attempts to enchant Zefiros items with either a soul gem or a sigil stone,
the act will be reversed upon completion.  Player enchanted items use dynamic IDs which
are difficult to track and introduce so much variation in what Zefiros can be that I will
not code that.





While testing Zefiros, many DebugPrint messages were made to accurately report what's
going on in areas of potential issue.  These DebugPrint messages were left in and can be
toggled to appear in the console by setting aaZefirosDebug to 1 in the INI or calling
"Set aaZefirosDebug to 1" in the console in-game.  The messages can be disabled by 
changing the flag to 0.





Finally, report any feedback you have in the Posts section of the mod page.  Most people
won't even read the entire mod page, yet here you are at the end of the ReadMe.txt.  Those
same people most certainly won't even open the INI and adjust any settings, so it's 
important that the defaults are well balanced.  Unfortunately, I am only one person and 
have been unable to extensively test the finished mod (having just completed it).  I've 
done my best, analyzing vanilla item stats, focus testing certain features and going with 
my gut on novel mechanics, but none of that means my defaults make for the a well balanced
experience.

Thank you for reading this far and thank you for downloading my mod.
I am proud of the work I've done and grateful to you for caring about it.