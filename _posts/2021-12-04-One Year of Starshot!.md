---
layout: post
---
And how many to go, I do not know.

I'm roughly a week late on it, but as the title says, I have been working on Starshot for roughly a year now! I <f>definitely</f> could have done more in that time, but I am quite happy with what I've been able to do nonetheless. I am going to continue with this project for the forseeable future of course, starting with the latest relatively major feature addition:

<h1>Fleet Management!</h1>

A long-missing feature of the story layer, fleet management <f>encompasses the player's inventory, loadouts, and unit customization</f> systems- though primarily the <f>inventory.</f>

As it stands, the fleet management screen consists of a series of row blocks, each of which being tied to and representing one ship in the player's fleet- in an arbitrary but player-modifiable order.
Each row block by default displays the ship's unique name, its current inventory, and some of its attributes- with a dropdown button allowing the full attribute list, and additional secondary details, to be seen.


<h2>The Inventory</h2>
The inventory itself is a series of clickable boxes, displaying an icon for whatever item is contained in the respective inventory slot, as well as iconography to indicate if it is a "specialty slot"- more on them later. Hovering over a filled slot will provide specific details about the item it contains, including its requirements to be considered "functional".

For an item to be considered "functional", it must be placed in an inventory slot of the appropriate type, and on a ship of the correct class- if the requirements listed on the item are not met, it will not be able to function as intended, but still can be used for trade and <b>some</b> story events.

"Specialty slots" are more restricted inventory spaces intended for more universally powerful (and less restrictive) pieces of equipment, and currently there are two types of specialty slot a ship can have: Weapon hardpoints, and defensive system mounts. Respectively, these are for primary weapon batteries and shields and armour, the most basic things a ship uses to engage in combat in the strategy layer. Most ships will have at least one of each, but while some will specialise in having more, others may be more lacking.

The bulk of a ships inventory will be unspecialised slots, however- and while guns and platings won't work in them, <f>ability and support modules</f> will, if equipped on an applicable ship. In theory, a ship can have as many modules equipped at once as it has inventory slots, albeit at the sacrifice of being unable to haul any cargo at the same time. This itself may not be a problem, but if that cargo is particularly valuable, it can easily make other ships more precious targets.

<h2>Loadouts</h2>
The mechanics for equipping equipment are explained just above, but to reiterate: <f>Place an item in the appropriate slot on a ship of the appropriate class, and that ship can make use of that item in battle.</f>

For abilities and weapons, this means providing the ship with the ability(ies) displayed in the item's 
tooltip, while for defensive systems and support modules providing the ship with a stat boost, calculated 
within the story layer. Items can provide other effects still, such as stat adjusting "auras" or other passive effects to the ship they are equipped on.

Alongside the pre-calculated stats, it will also be possible to see a ship's ability list within the fleet management screen, but one must bear in mind that it can currently only pre-calculate a ships <i>individual</i> stats- auras from allies and enemies are not taken into account.

Additionally, the ability to reorganize the order of ships in the your fleet is planned, however this currently would not have any effect beyond spawn order inside the strategy layer. This is very likely going to change, though.

<h2>Customization/Personalization?</h2>
<f>Unfortunately, there isn't much planned for this.</f>
Between my own technical skill, trying to keep the systems as "open" as possible, and the feasability of what could be customized, it just isn't an avenue I believe I could explore.

One bit of customization I <i>have</i> been able to implement however, is allowing the unique display name for a ship to be changed. It's not much, but it's something.



<h1>Other Stuff and Closing Words</h1>
I haven't just done this inventory system in the meantime, of course! Though admittedly there have been a few trickier parts, but nonetheless; There are two major things I've done alongside it.

First, I have been trawling through material logic to create my own responsive visual aids for the strategy layer- highlighting entities behind walls, for starters- as well as beginning to open up my UI colourizer system for proper user-end customization. Neither are completely finished yet, but I always enjoy toying with materials. Usually.

Secondly, I have partially started work on a Unity variant of the interactive story "generator" Starshot uses! The intention for that is to make it a publicly-accessible toolkit for others to use (potentially including myself in the future), as well as another piece to add to my portfolio. I'll have news on that soon enough, hopefully!

<f>But other than these two things, I have nothing else for this blogpost- so here's to a hopefully better year just around the corner!</f>