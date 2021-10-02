---
layout: post
---
An explainer on how event strings work.

This is that part two I mentioned last time- and though I will go over the system broadly, this will also be a much more technical explanation, including examples!

To start, a warning: Some of the terms I'll use here may not be the best terms for what they do, no matter how much sense they make to me- so if you see anything off, please do point it out to me!

<h3>What goes into an event string</h3>

To start, an example:
<code>add hidden item(goods=2) trait(trader), remove item(ore)</code>

The question I expect people to be asking is "What does any of that mean?"- which in my defense is the point of this post.

Let's break it down piece by piece. First, this string consists of two specific commands:
<code>add hidden item(goods=2) trait(trader)</code>
And;
<code>remove item(ore)</code>
As you can see, these two commands are comma-seperated, but these two are not equal in terms of functional length and content.

Both of these commands contain the two things contained by the vast majority of event strings, however: Keys and declared variables.
Keys are used by the string parser to control its behaviour, and in this example, three are present: "Add" and "Remove" at the start of the two commands, and "Hidden" included in the Add command.
Add and Remove are two of the three inventory-related commands- and tell the parser to use the declared variables to, as the names would suggest, add or remove specific items from the player's inventory. For both of these, variables follow the following structure:
<code>type(itemID=count)</code>
Where type is the item list and inventory type to interact with, current valid options including "Item", "Trait", and "Ship", where itemID is the row name for the item in relevant datatables, and where count is the amount to add- one if not present, as with the "Trait(Trader)" and "Item(Ore)" variables in the example.

But what about that "Hidden" key?

Well, sometimes a key will have access to one or a number of secondary keys, depending on their needs. In 
this case, "Hidden" is a secondary key used to exclude that command from pre-emptive checks, such as the ones
 used to preview a choice's rewards when it is presented to the player. Note that keys like this apply to the command, but not the entire string- so if someone wanted to change the "Add" command in the example to only display the added items, they would instead have to put in the following:
 <code>add item(goods=2), add hidden trait(trader)</code>

At this point, it is also worth noting that any number of individual commands can be put into a single event string, <f>but commands with matching keys generally should be condensed into a single command, as with the original example.</f>