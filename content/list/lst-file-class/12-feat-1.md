+++
date = "2016-08-01"
title = "Lesson #12: .lst - Feats (Part 1 - basic setup)"
original_url = "/list/lst-file-class/12-feat-1.html"

[menu.main]
    identifier = "lst-file-class_12-feat-1"
    name = "Lesson #12: .lst - Feats (Part 1 - basic setup)"
    parent = "lst-file-class"
    
+++
By Professor Chris Chandler (Barak)

**File(s) Covered:** \*feat.lst

**Tags used:**

`      OUTPUTNAME          ,           TYPE          ,           VISIBLE          ,           STACK          ,           MULT          ,           CHOOSE          ,           DESC          ,           DESCISPI          ,           BENEFIT          ,           COST          ,           SOURCELONG          ,           SOURCESHORT          ,           SOURCEWEB          ,           SOURCEPAGE     `

------------------------------------------------------------------------

The feat object in PCGen is one of the main workhorses used in getting
the RSRD rules implemented, so it's very important to learn to create
them and what can and cannot be accomplished with them. While it covers
the usual business that is covered by a feat in the 3.5e game, it also
does a lot of behind the scenes work in PCGen to make all the mechanics
happen.

As an example of what I'm speaking of, a Ranger's Favored Enemy ability
and a Cleric's Turning ability are both coded as "feats" in PCGen, even
though they don't appear as such in the program or on output.

I'll run through the most common tags, explain how to put them together
and then I will go into some specific uses for feats and how to
configure PCGen feats to achieve the desired outcome. In order to cover
all of this, I'm going to split it into different lessons. This first
part of the feat lesson will deal with setting the feat up for use in
general, the second lesson will deal with implementing the prerequisites
(if there are any) to take the feat and how to implement the effects of
the feat as far as the game mechanics go and a final one to discuss
anything that didn't fit in the first two lessons.

------------------------------------------------------------------------

**Feat Name**

The feat file is currently a lst file that has one feat entry per line.
The first thing on each line is the feat name. There is no tag for it,
the program assumes that whatever is there is the name of a feat. Note
that you should not use parens in the name of a feat as those are used
by PCGen when referencing a feat with a sub choice/target.

For demonstration purposes we'll code up the "Improved Critical" feat
from the RSRD. So our feat line will start with those words.

------------------------------------------------------------------------

**OUTPUTNAME**

The OUTPUTNAME tag can be used in a couple of different manners. You can
completely change the name of an object (as far as output is concerned)
and not reference the real name at all, or you can use part of the real
name. A special string was developed to grant access to only the text
contained in parens. That string is "\[NAME\]" (no quotes).

In feats this is mostly done when there are some sort of math operator
characters in the feat name (hyphens being the most often occurring
issue). In newer versions of PCGen this appears to have been fixed
somewhat but in older versions those characters in feat names caused
issues, so we started dropping those characters from the feat name and
then using an OUTPUTNAME tag with those characters in it to get around
the issues.

So, as an example of OUTPUTNAME use, if we wanted the name on output to
be "Critical (Improved)", we could cause it to happen by entering
`OUTPUTNAME:Critical (Improved)` . Note that there is a preference
setting that turns off output names so the user may not see it if they
have elected to turn them off.

The name "Improved Critical" is just fine as it is, so we'll skip an
OUTPUTNAME tag on this one.

------------------------------------------------------------------------

**TYPE**

The TYPE tag is used for a couple of different purposes. The first and
most obvious is to set the feat type as indicated by the source. Another
use of it is for internal program use to group a set of feats together
for later selection by an `ADD:FEAT(TYPE=type)` tag elsewhere. This is
especially useful when you have several benefits that a PC can choose
from. These TYPEs can also be used in separating feats for display in
different areas on an output sheet.

By convention we do not put spaces in the TYPEs (historically it caused
issues in the program). If there is more than one word in the TYPE, we
run them together and capitalize each one. A feat \*can\* have more than
one TYPE. In that case we put each TYPE in and separate them with
periods.

From the RSRD you will see TYPEs of: General, Fighter, Metamagic,
Psionic and ItemCreation. Codemonkey Publishing went so far as to start
creating all class and racial abilities as hidden feats and they have
added SpecialAttack, SpecialQuality, ClassFeature, Extraordinary,
SpellLike and Supernatural as standards in their datasets. Please note
that you are not limited to just those TYPEs mentioned, you can make a
TYPE of anything, those listed above are just ones you might commonly
see.

Looking at the RSRD, Improved Critical is a General feat and a Fighter
feat, so we enter `TYPE:General.Fighter`

------------------------------------------------------------------------

**VISIBLE**

This is a tag that takes one of four values; YES, NO, DISPLAY and
EXPORT. It controls whether or not the user can see the feat in the
program UI feat list and on the output sheet feat list.

If the VISIBLE tag is set to YES (or is not present) then the user will
see the feat in their feat list in the UI and on their output sheet and
they will be able to access it in the UI.

If the VISIBLE tag is set to DISPLAY, that means that the user will be
able to access it in the UI, but it will not be listed in their feat
list when they generate an output sheet.

If the VISIBLE tag is set to EXPORT then the user will not see or be
able to access the feat in the UI, but it \*will\* appear in the feat
list when they generate an output sheet.

Setting VISIBLE to NO creates what we call a "hidden feat". It's how we
make a lot of things work behind the scenes. The Ranger Favored Enemy
and Cleric Turn Undead are examples of hidden feats used to implement
game mechanics. The only way for this type of feat to be accessed is by
being specifically granted by a .lst file or being called via an
ADD:FEAT chooser tag in a lst file. It will never appear/be available
for selection as a bonus feat from the UI.

A good rule of thumb is that if the feat is listed in the feat section
of a data source, it should be VISIBLE:YES (or leave out the VISIBLE tag
so it defaults to YES). If it's not listed as a feat in the source, it
should be `VISIBLE:NO` . The EXPORT and DISPLAY options are used for
special cases where we need to something very strange... :)

Since the Improved Critical feat is a normal feat listed in the RSRD
feat section, we'll skip the VISIBLE tag and it will default to being
visible to the user in the UI and on output.

------------------------------------------------------------------------

**MULT**

The MULT tag is a simple YES or NO tag. It determines whether you can
take a feat more than once. This information is usually found under the
"Special" section in the feat description. It will tell you whether or
not the feat may be taken multiple times.

Note that if set to YES, then you \*must\* use a CHOOSE tag in the feat
also.

According to the RSRD, Improved Critical can be taken more than once, so
we'll use `MULT:YES` .

------------------------------------------------------------------------

**STACK**

The STACK tag is another tag that is a simple YES or NO. Default if the
tag is not present however is NO in this case. If you have the MULT tag
set to NO, then the STACK tag will have no effect. If you have the MULT
tag set to yes however, this determines whether or not the feat will
stack with itself if you take it more than once. Like with the MULT tag,
this information is usually given to you in the "Special" section of the
feat description.

According to the RSRD, Improved Critical does not stack with itself (you
can take it again but must choose a different weapon) so we need to put
`STACK:NO` in the feat line.

------------------------------------------------------------------------

**CHOOSE**

There are many versions of the CHOOSE tag. For full information please
read the section of the PCGen documentation dedicated to CHOOSE in all
it's different forms. In this tutorial I'm just going to touch on a
couple of common ones that you might see/use over and over again.

First is the free text version. That would simply appear as
"CHOOSE:Choice 1|Choice 2|Choice 3" in the .lst file and pop a chooser
with a list containing Choice 1, Choice 2 and Choice 3. You would use
this when the choice is something that is not a game effect coded for
PCGen (a good example of this is the CHOOSE statement in the 3.0 Ranger
Favored Enemy hidden feat).

Next comes CHOOSE:NOCHOICE. This causes the CHOOSER to not be displayed.
This is useful when you have a feat that may be taken multiple times
that doesn't really have any choice to it. Since you used MULT:YES you
must have a CHOOSE, but there really is no choice. A good example of
this is the Toughness feat.

Another popular one is CHOOSE:FEAT=featname. This is used mostly in
cascading feats where the new feat will apply to the object of a
previous feat. A good example of the use of this is the Weapon
Specialization feat. It uses "CHOOSE:FEAT=Weapon Focus|1" which presents
a list of all the weapons that the character has taken the Weapon Focus
feat for and lets the user pick one.

Moving on to our current feat under construction, we see that Improved
Critical requires that you be proficient with the weapon you choose this
feat for. While this is listed as a prerequisite, it actually affects
what you can choose from so we implement it via a CHOOSE restriction.

Looking through the PCGen documentation for a CHOOSE tag that will suit
our purposes, we find the following: CHOOSE:WEAPONPROFS|LIST which is
supposed to present a chooser containing a list of all the weapon
proficiencies that your character has. We'll add
"CHOOSE:WEAPONPROFS|LIST|1" to the feat line.

------------------------------------------------------------------------

**DESC**

This tag is used to hold the one to two line "flavor text" that
describes the feat. This is usually the first couple of sentences found
under the feat name.

This is what will be output to the feat description field if the
"Display Feat Description" checkbox is checked in the preferences.
Otherwise the more verbose contents of the BENEFIT tag will be
displayed.

For the Improved Critical feat we can paraphrase the short description
and enter "DESC:With your selected weapon you know how to hit where it
hurts."

------------------------------------------------------------------------

**DESCISPI**

Another simple YES or NO tag. If the tag is not present it defaults to
NO.

This tag is used to indicate to the program that the description is
considered to be Product Identity of the publisher and should be marked
as such when displayed in the program. Permission must be obtained from
the publisher to use Product Identity.

There is no Product Identity in the Improved Critical description, so we
will leave this tag out of our feat.

------------------------------------------------------------------------

**BENEFIT**

This tag is meant to contain the text from the "Benefit" section of the
feat from the source material. This text will be displayed in the feat
description field in both the UI and on output if the "Display Feat
Description" checkbox in the Appearance/Display Options Preference
window is unchecked. Otherwise the (much shorter) text from the DESC tag
will be displayed.

For the Improved Critical feat we would enter
`BENEFIT:When using the weapon you selected, your threat range is doubled.`

Note that it is quite common to leave this tag out so as to encourage
people to purchase the books that the dataset represents.

------------------------------------------------------------------------

**COST**

This tag is used to set the cost (in feat slots) of the feat. If it is
not present it defaults to a value of 1. This tag can be used to set up
a system where you can take a penalty type feat to get another positive
effect feat (think Flaws & Traits).

Since Improved Critical is a normal feat, we will leave the COST tag out
and let it default to a cost of one feat slot.

------------------------------------------------------------------------

**SOURCELONG**

This is a free-form text tag. We put the full name of the source here.
This tag may be entered once at the top of the .lst file and will apply
to everything below it until another SOURCELONG tag is encountered, or
it may be placed on each feat line (which is the practice CMP has
adopted for this tag).

Since we are using the RSRD for our example, the tag would be
`SOURCELONG:Revised (v.3.5) System Reference Document`

------------------------------------------------------------------------

**SOURCESHORT**

This tag is also a free-form text tag. We put an abbreviated version of
the source name here for use in the program to help keep everything on
the screen. This tag may be entered once at the top of the .lst file and
will apply to everything below it until another SOURCESHORT tag is
encountered, or it may be placed on each feat line (which is the
practice CMP has adopted for this tag).

Again, since we are using the RSRD for our example reference, the tag
would be **SOURCESHORT:RSRD**

------------------------------------------------------------------------

**SOURCEWEB**

This tag is for the entry of the URL pointing to the product/book. This
tag may be entered once at the top of the .lst file and will apply to
everything below it until another SOURCEWEB tag is encountered, or it
may be placed on each feat line.

In the case of the RSRD, the tag would be
`SOURCEWEB:http://www.wizards.com/default.asp?x=d20/article/srd35`

------------------------------------------------------------------------

**SOURCEPAGE**

This is just what it seems, where we indicate the page from the source
material where you can find the text for the feat. It takes freeform
text, so anything you put in there will be displayed when using the
SOURCEPAGE output token.

When you are going from an OGL book the format is usually
`SOURCEPAGE:p.#` . If you are working from an online document such as
the SRD, it would be the filename, so `SOURCEPAGE:<filename>`

Since we are working from the RSRD, our tag will look like
`SOURCEPAGE:Feats.rtf`

------------------------------------------------------------------------

I'm going to end this lesson here even though our example feat isn't
complete yet. We've covered the most commonly occurring tags in feats
here (other than PRE and BONUS tags). In the next lesson I will cover
setting up prerequisites to take the feats and implementing the effects
of feats (which will allow us to complete the entry of the Improved
Critical feat).

For quick reference, we currently have the following for our feat so far
(new lines should tab characters):

> `Improved Critical            TYPE:General.Fighter            MULT:YES            STACK:NO            CHOOSE:WEAPONPROFS|LIST|1            DESC:With your selected weapon you know how to hit where it hurts.            BENEFIT:When using the weapon you selected, your threat range is doubled.            SOURCELONG:Revised (v.3.5) System Reference Document            SOURCESHORT:RSRD            SOURCEWEB:             http://www.wizards.com/default.asp?x=d20/article/srd35            SOURCEPAGE:Feats.rtf`

Barak\
 LST Chimp



