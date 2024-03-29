+++
date = "2016-08-01"
title = "PREDEITYALIGN (Global: PRErequisite)"
original_url = "list/global/pre.html#predeityalign"
categories = [ "all-tag", "pre-tag" ]
+++

## Status

None

## Syntax

`PREDEITYALIGN:x`

## Parameters

-   x: LG,LN,LE,NG,TN,NE,CG,CN,CE
    (Alignment abbreviation).
-   x: 0,1,2,3,4,5,6,7,8 (Alignment array number).



What it does
------------

-   Requires the PC to have a deity with a particular alignment.
-   Alignment names are defined in the *statsandchecks.lst*
    gameMode file.
-   The Alignment abbreviation is the prefered method of identifying the
    required alignments.
-   The Alignment array number, based on the order the Alignments are
    presented in the *statsandchecks.lst* file with the first one
    being 0.
-   If NO alignments are defined in GameMode, all PREALIGN tags will
    return TRUE.
-   In the 3e and 35e gameModes these are the listed Alignments: 0=LG,
    1=LN, 2=LE, 3=NG, 4=TN, 5=NE, 6=CG, 7=CN, 8=CE, 9=None, 10
    Deity's Alignment.

Example
-------

`PREDEITYALIGN:0`

Character must have chosen a Lawful Good deity.

`PREDEITYALIGN:LG,NG,CG`

Character must have chosen a deity of any Good alignment.

