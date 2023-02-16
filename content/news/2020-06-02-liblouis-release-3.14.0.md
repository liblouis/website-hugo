---
categories: Liblouis
title: 'Liblouis Release 3.14.0'
date: 2020-06-02
---

This release contains major updates to Arabic, Dutch 8-dot computer braille, German, Russian computer braille, Ukrainian computer braille and Uzbek. Also there are new tables for Israeli multi-language Hebrew/Arabic/English braille and Malay. Aside from that there have been many code cleanups and bug fixes.

For a detailed list of all the changes refer to [the list of closed issues](https://github.com/liblouis/liblouis/milestone/24?closed=1).

New features
------------

-   Add new test mode in `lou_checkyaml` for testing display tables. Thanks to Bert Frees.

Bug fixes
---------

-   Work around a bug that causes an endless loop in French uncontracted braille thanks to André-Abush Clause.

Braille table improvements
--------------------------

-   Updates to the Russian computer braille table thanks to Andrey Yakuboy:
    -   Fixed diacritics, Greek letters and Hebrew.
    -   Added new Cyrillic letters.
    -   Fixed several minor bugs.
-   New table for Uzbek braille thanks to BAUM Engineering.
-   New table for Ukrainian computer braille thanks to Andrey Yakuboy and Oleh Shpai.
-   Improvements to Arabic thanks to Ikrami Ahmad and Mada, Qatar Assistive Technology Center.
    -   Added a lot of new symbols (algebra, geometry, Greek, etc.) to the grade 1 table.
    -   Changed some symbols for less conflicts with grade 2.
    -   Implemented letter sign / grade 1 indicator to cancel numbers and inhibit contractions when in grade 2.
    -   Updated 8-dot computer braille table for better (easier to memorize) presentation of basic math symbols and punctuation marks.
    -   Improved back-translation.
-   Improvement to German thanks to Bue Vester-Andersen.
    -   Removed superfluous letter sign before certain lesser-used accented letters.
-   Final version of Dutch 8-dot computer braille table thanks to Leonard de Ruijter.
-   New Israeli multi-language Hebrew/Arabic/English tables for both uncontracted and computer braille. Thanks to BAUM Engineering and Erez Kugler from TSR Gaash.
-   New table for grade 2 Malay braille (Malaysia) thanks to Herbert Koh.

Other changes
-------------

-   You can now use up to 256 `noletsign` characters in a table, thanks to Christian Egli.
-   Major improvements to the documentation for the *Standing Alone Sequences* and their related opcodes such as `seqdelimiter` and also clarifications regarding the `begcaps` and `endcaps` opcodes thanks to Bue Vester-Andersen.

Deprecation notice
------------------

-   The `class` opcode has been deprecated in favor of `attribute`, which has been enhanced to do everything `class` can do.

Backwards incompatible changes
------------------------------

None

Invisible changes
-----------------

New, renamed or removed tables
------------------------------

### New

-   uz-g1.utb
-   ar-ar-g1-core.uti
-   ar-ar-math.uti
-   he-IL.utb
-   he-IL-comp8.utb

### Renamed

None

### Removed

da-dk.dis
:   This table has long been superseded by `da-dk-octobraille.dis`.

da-lt.ctb
:   This table was a step on the way to defining a Danish 8 dot standard. The table was referring to an old Danish Braille note-taker from the 80s and 90s, which is not used any more.

fi1.ctb and fi2.ctb
:   These tables are obsolete. Use `fi-fi-8dot.ctb` instead.
