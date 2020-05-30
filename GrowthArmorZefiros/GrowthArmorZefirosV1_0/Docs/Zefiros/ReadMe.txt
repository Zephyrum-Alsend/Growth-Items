Growth Armor Zefiros V1.0

KNOWN ISSUES
-Leveling up leaves you naked for 1 frame
-When offering armor, the highest durability instance will be consumed

FAQ
Q: Why are the Known Issues?
A: OK, so...

Fun fact: Oblivion doesn't register changes to stats or enchantments until their associated
item is re-equipped!  Even funner fact: re-equipping items quickly during gameplay fails!
Basically, if I call UnequipItem EquipItem on the same frame, EquipItem fails and you are
left naked, alone, with ought to do but manually equip it yourself.  So I put a one frame
delay in there, to avoid the bug.  Funnest fact: it just works for weapons!

For variables, inventories don't exist.  They are a myth perpetrated by the Bethesdian 
government to sow false complacency with the system, distracting you from the real issues: 
Khajiits being turned into furries.  As such, I do not and cannot actually know what item
precisely you are looking at in your inventory.  I know the base item, I can get that.
I know it's an iron longsword.  But you've got like 7, right?  So I hire OBSE, private eye,
to snoop around the real code for some hard proof those 7 exist.  Then it returns a dossier
of untraceable references to those 7 iron longswords.  But I still don't know which one exactly
you were looking at, so I pull off the top one.  That's usually the highest durability one.
Until OBSE infiltrates Bethesda and exposes v22, this issue will persist.