+++
date = "2016-08-01"
title = "Spycraft Espionage Handbook for PCGen"
original_url = "/source/spycraft/spycraft.html"

[menu.main]
    identifier = "spycraft_spycraft"
    name = "Spycraft Espionage Handbook for PCGen"
    parent = "spycraft"
    
+++
**Game Mode: Spycraft**

ALDERAC ENTERTAINMENT GROUP &gt; SPYCRAFT &gt; CORE RULES

**Spycraft Espionage Handbook**

PCGen Dataset user guide
------------------------

**Updated 10/12/04**

This read me file contains information on how to make the most of this
dataset. Specifically it will alert you to work-around's for Spycraft
rules that PCGen does not currently support.

### Nationalities

When you select your department the first pop up chooser will let you
select your characters nationality. This will apply a template which
specifies your nationality and will grant you an additional bonus
language if your native countries language is something other than
English. The Nationality template can be removed and replaced with
another as people in the modern age will occasionally immigrate though
the bonus language granted with your original choice will not be
removed. You can only apply one Nationality at a time. The list is by no
means complete, if you wish to add additional nationalities edit the
spycraft\_templates.lst file to add the nationality template. Edit the
spycraft\_feats\_hidden.lst file to add additional choices to the list
that appears when you choose a department. The Language list is also
incomplete, you can add them by editing the spycraft\_languages.lst
file.

### Skills

The skills 'Hobby (Untrained)' and 'Sport (Untrained)' are listed to
keep the skill list uncluttered and cannot be selected. Although all
sport and hobby skills are usable untrained only these two will show up
when skills are exported with 'show untrained skills' selected.

### Backgrounds

Backgrounds appear in the skill list though they are not skills and are
never used as such. They are in the skill list because they are
purchased with skill points. The rules say you can have no more than 5
points in no more than 2 backgrounds at any one time. PCGen does not
enforce this rule. Once the background is resolved or 'cashed in' it is
suggested that you transfer the skill points into the skill named
'Resolved Backgrounds'.

### Languages

Languages are treated a little differently in Spycraft and some work
around's are used to comply with the Spycraft rules. It is suggested
that you create a new note in the description tab to keep a list of
which languages your character speaks natively and another for those
picked up by making a language check. Languages your character starts
with are considered native. Any languages learned through the language
skill can become native by spending an additional skill rank on it. To
do this purchase one rank of the Native Language Skill corresponding to
that language. The Native Language Skill will add one rank to the
Languages Skill but no additional languages. The Native Language Skills
is a work-around, you should always use your Languages score for skill
checks. Adding more then one rank of any Native Language Skill will not
add any additional ranks to Languages, so don't do it.

### Feats

**Training** grants you 4 additional skill points, however PCGen cannot
add these. You may add these points manually by changing the number in
the "Skill Points left for Class" field on the Skills Tab.

**Unlocked Potential** raises your max ranks for a specific skill. PCGen
does not have a way to raise the max ranks for a specific skill, the
feat will allow you to choose the skill to apply it to but it will not
raise the maximum ranks you can spend on it. To work around this
limitation you can check the Bypass Max Skill Ranks option in
[Preferences/House Rules](/menu/settings/character/house-rules.html) .

### Purchasing Equipment

PCGen cannot yet deal with multiple currency systems like that used in
Spycraft. Items in Spycraft have a budget point value or a gadget point
value as well as a monetary value if purchased on the street. This
dataset lists items in either budget points or gadgets points. The first
Type listed for every item is either Gear, Gadget or Vehicle. Gear type
items are bought with Budget Points and Mission Budget points while
Gadget and Vehicle type items are bought with Gadget Points. PCGen
cannot tell the difference between the two and does not restrict your
purchasing, it is up to the user to determine his or her budgets and
stay within them. This is especially important if you customize a gear
item with a gadget modification, the customizer will add the
modification cost (in gadget points) to the cost of the gear item (in
budget points) and the resulting cost will be incorrect. You can see
your characters budgets in the lower right pane in the Class Tab. Street
values are not listed.

### Modifying Equipment

Some gadgets and vehicles can be modified with additional capabilities.
To do this right click on the item to bring up the customizer. The
modifications will be listed and can be added to the item for an
additional cost. Please note that Spycraft places some limits on the
number of modifications that can be added to certain items. PCGen does
not restrict the number of modifications you can add though the Spycraft
rules do. Please read the rules to determine the limits.

### Equipment

To get the full benefits of **Tiger claws** you must equip your PC with
a pair, one on each hand. Using one will only give you half of the
bonuses.

### Vehicles

PCGen will output the correct stats for your chosen vehicle but you must
set things up in a certain way for it to output correctly. Most
importantly you must Equip the vehicle to the character in the equipping
sub-tab, setting the vehicle to not carried or another setting will not
activate the vehicle stats. Secondly you may only equip one vehicle at
any one time, the reason for this is that PCGen cannot, at this time,
assign variables to objects and so all variables are associated with
your character. What this means is that if you equip you character with
2 or more vehicles that output sheet will still only have one vehicle
block but the stats will equal the combined totals of all the vehicles
you have. Equipping the vehicle to your character does not add any
weight or take up any slots from your character not does any items you
may put in the vehicle. Vehicles are containers that do not have any
restrictions on what they may contain, I leave that to you, your Game
master and common sense.

Customizing vehicles. You may add gadgets and other refinements to your
vehicle by customizing it. Find the vehicle in the equipment list and
right click it to choose create custom object. You will be presented
with a list of refinements you can add to the vehicle. PCGen will not
limit the number of these items you can add to the vehicle, again its up
to you and your GM to follow the rules. When output the OS will display
the number of gadgets as well as the maximum number of gadgets that can
be added to that type of vehicle.

### Using the Output Sheet

At this time there is an html sheet and a pdf template. The text set in
the tab name field of the summery tab will output as the characters code
name. You can find the Spycraft html Output Sheet in the Modern/HTML
folder, it is named csheet\_spycraft\_std.htm. The Spycraft pdf Output
Sheet can be found in the Modern/PDF folder, it is named
csheet\_spycraft\_std.fo.



