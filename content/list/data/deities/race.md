+++
date = "2016-08-01"
title = "RACE (Data: deities.lst)"
original_url = "list/data/deities.html#race"
categories = [ "all-tag", "deities-tag" ]
+++

## Status

Deprecated 6.05.1 - use FACT

## Syntax

`RACE:x|x`

## Parameters

-   x: Text (Race of typical Worshippers)



What it does
------------

This is used to identify the race of the typical worshippers of a Deity.

Example
-------

`RACE:Dwarf|Gnome`

The deity's typical worshippers are Dwarves and Gnomes.

**.MOD Example (Appending):**

Initial Deity: `<deity name> <tab> RACE:Elf`

Modified By: `<deity name>.MOD <tab> RACE:Halfling`

Is Equivalent To: `<deity name> <tab> RACE:Elf|Halfling`

