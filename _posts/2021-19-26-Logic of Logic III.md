---
layout: post
---
Alternatively; Logic Cubed- An explainer on logic strings.

As a preface, during making logic strings I updated my parsing standard to be semicolon ( ; ) seperated for individual instructions, as opposed to comma ( , ) seperated. While it did work for what I was doing, this change to seperation makes individual instructions clearer to me, and makes including structs within commands much easier.

The same warning from part 2 applies, but to repeat it: Some of the terms I'll use here may not be the best terms for what they do, no matter how much sense they make to me- so if you see anything off, please do point it out to me!

<h3>What goes into a logic string</h3>

While generally in writing format, logic strings are different from event strings on the fundamental principle that they are designed to output a boolean, or series thereof, instead of actively doing things themselves.

How it gets that boolean is through the truthiness of the rules and groups inscribed within the string in question. Like last time, I have an example:
<code>add groupA item(ore>=2) item(mininggear); exc groupA trait(miner); exc groupB ship(length>=2)</code>

Now, this does make the breakdown slightly out of reading order, but the first thing I want to break these down with are those "groupA" and "groupB" keys. My example might make it more evident than practical usage, but these keys define the <i>group</i> each rule exists in. Other traits of a rule are generally done in relation to a rules group, and a group can be given any name- provided it does not conflict with other strings used in reading rules. For instance, "ore" and "fleet" could replace "groupA" and "groupB" in this example, and still function.

If we seperated the original by groups, we would have two strings that look like this:
<code>add item(ore>=2) item(mininggear); exc trait(miner)</code>
<code>exc ship(length>=2)</code>
Both of these sets are able to have a single boolean output, and in this example both would need to be true for the entire rule to be considered true. If it was part of a system that made use of "<f>Dictionary Outputs</f>", then those outputs could be used individually, but more on that later.

To start breaking down their functions more properly, we must now look to what each individual rule starts with. Specifically, those in this example start with either "add" or "exc": These define how the rule is output in relation to other rules and themselves. More specifically, rules that start with "<f>add</f>" (or <f>additive more</f>) <f>must have all checked variables output as true, for the entire rule to be true</f>. Inversely, rules that start with "<f>exc</f>" (<f>exclusive mode</f>) <f>only require one variable to be true for the entire rule to be true</f>, overriding other false exclusive variables, <f>and even false additive variables</f>.

In this example, there is only one <f>additive</f> rule set, and two <f>exclusive</f> rule sets, with one in the same group as the additive.
For that one additive to pass, both "<f>item(ore>=2)</f>" and "<f>item(mininggear)</f>" must also be true- but can be overriden by "<f>trait(miner)</f>" if that is true instead. In laymans terms, the player needs to have both 2 or more "ore" items <i>and</i> at least one "mininggear" item, or have the "miner" trait, for groupA to pass it's half of the check.
Because it is seperated into groupB however, regardless of how groupA passes its check, the player will need to pass the "ship(length>=2)" check- have 2 or more ships within their fleet.

This check may only have been for a single, and relatively unrestricted, choice option, but there was still plenty going into it- and plenty more than can be done with this system. Primarily, that will be through "Dictionary outputs", as mentioned earlier- or to be more accurate to Unreal's naming of them, "Map outputs".
Dictionary outputs are a series of unique potential outputs, generally strings, with an attached list of desired rule groups (formatted as "group; group; group"), whose collective truthiness describes the truthiness of that particular output. Generally, any system using dictionary outputs will take the longest (in terms of how many rule groups are checked), completely true output (all checked groups are themselves true), and can default to the first listed output if none are completely true, or take the most true output available. The latter option is generally not used, as that can create continuity errors, but it is an option.