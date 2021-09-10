---
layout: post
---
AKA, I need to be better with naming these.

If you've seen [the last post](https://xavierhtech.github.io/Starshot/2021/08/14/UI-Revamp.html), and assumed I was done with my UI revamps, you would now be correct. Shortly after making that post, I reached a point where I was content with the stylishly cleaner aesthetic I had created, even if only a small number of things have been ultimately "finished" with it. As always, more to come on that in the future.

For now, though, I've moved on to more significant changes and reworks for the actual gameplay parts of <ss>Starshot</ss>, particularly in the story half of it. And first on my list of things to rework is a very significant one, both for development- mine and potential modders- and for gameplay: <f>A complete rework of the events system</f>, and hopefully a similar rework of the "requirements logic" system shortly after.

<h2>So what's the deal with that?<h2>

It may not answer that question on its own, but this is a big part of it:

![Response Data Struct - datehere](https://xavierhtech.github.io/Starshot/media/blog/responsestruct.png){: width="100%"}

In short, <f>this struct is already too big for my tastes.</f> And yes, that was something I saw coming when mashing this together for my initial prototyping- Most of the variables are there for good reason, including some that are intentionally only meant to be prefilled in certain conditions, continuity settings and strategy generation data (Listed as "settingstoload") included.
As this is a struct used for an essential datatable, especially if I want people to add their own content after the game is available to them, excessive scope can easily become problematic and exponentially large in the datatables themselves, too.

Now, how do I fix this? The most direct answer is to remove as many variables as possible, but that isn't too simple when some of those variables are necessary for certain situations, like the event enum- used to tell the game when a specific "event" is supposed to happen, currently only including triggering a battle.

That enum did serve a part as the basis for the solution I came up with, though. And that solution? <f>To condense a number of these variables into a single one, without using structs if possible.</f> My primary reason for avoiding structs being to make this condensed supervariable as writable as possible when editing datatables outside of the Unreal Editor, but I would also argue that it has given me greater freedom in terms of what I can make happen through the supervariable.

Now, the problem with this supervariable is one thing in particular: <f>What do I make it to store all of that information, and how do I then recover said information?</f>

My answer to that is a string, and a string parser.

It's an easier answer than it is a solution, but that's exactly what I've been working with, and working quite well with, by all accounts.
While I have only focused on one particularly small area at a time, the intent for this parser is to handle both "events" and "logic"- namely, rewards, costs, and battles, and choice requirements and battle outcomes, respectively.
In each case, the advantages of the string parser over my initial system are multifaceted, but require a good deal of work to function well- at the very least, one advantage of doing this for the story half of the game specifically is that I don't have to worry as much about performance, with there being little else to take up resources.

This post is already getting pretty long, so I won't make it too much longer (expect a second part at the very least!) and I'll round this one off with what I mean by "multifaceted":
Essentially, this system lets me perform multiple instructions simultaneously, without any of the instructions necessarily relating to any other part of the response data, or necessarily limiting how they do relate.
For example: Item requirements. While I have experimented with including item removal and leaving the player's inventory intact, I never implemented a toggle prior to this latest change, however this instruction system offers an additional set of benefits: Removing items not considered to be the requirement, and item replacement particularly. 
The former should be self-explanatory- the system does not exclusively remove the requirement for a particular response when selected, it can even remove some items without even touching the requirement, while the latter allows for a given item (if present) to be exchanged for another, without reshuffling the player's inventory- something that will become useful when the full inventory management system is added.