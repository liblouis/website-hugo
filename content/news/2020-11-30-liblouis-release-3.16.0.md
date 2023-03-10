---
categories: Liblouis
title: 'Liblouis Release 3.16.0'
date: 2020-11-30
---

This release is mostly the work of Bert Frees. He has put in a lot of work and pushed some major improvements with regards to how emphasis is handled (and how this is documented). He fixed a crash when reading URLs using computer braille. He also worked with many contributors to get their improvements in. So we have better support for UEB, Dutch, Urdu, Malayalam, Arabic, Bashkir, Uzbek, Russian computer braille and for EBAE. I\'d like to thank everybody for helping to bring liblouis forward.

For a detailed list of all the changes refer to [the list of closed issues](https://github.com/liblouis/liblouis/milestone/26?closed=1).

New features
------------

-   A new opcode `noemphchars` was added. This gives you more control over the placement and scope of various emphasis indicators. Thanks to Bert Frees.

Bug fixes
---------

-   Fix an endless loop when using `compbrlAtCursor` thanks to Bert Frees

Braille table improvements
--------------------------

-   Improvements to US EBAE conformance with BANA emphasis guidelines thanks to Benetech.org
-   Fixed a problem with apostrophe in Malayalam thanks to Jake Kyle
-   Improvements to contraction use in UEB thanks to James Bowden. In particular the checkmark (U+2713) is added, the emdash (U+2014) is fixed, the right single quote used as apostrophe between letters is fixed and finally some more accented letters have been added.
-   Improvements to Urdu Braille and Malayalam thanks to Jake Kyle
-   Add characters for Bashkir and Uzbek languages to the Russian computer braille table. Thanks to Andrey Yakuboy.
-   New table for Bashkir uncontracted braille thanks to Rustam Churagulov and Gabidullin Yunir.
-   Updated `<` and `>` symbols in the Arabic tables thanks to Ikrami Ahmad.
-   Improvements to Dutch thanks to Bert Frees.
    -   Every word part in a capitalized compound word counts in the length of a passage.
    -   `begcapsphrase` is allowed to start in a word preceded by punctuation.
-   Improved translation of ligatures in UEB thanks to Bert Frees.
-   Multiple improvements to the Russian literary braille thanks to Andrey Yakuboy and Bert Frees:
    -   Many new symbols (punctuation, bullets, math symbols, etc) have been added.
    -   The table now includes the international phonetic alphabet table.
    -   Punctuation after digits and fractions is now marked with dot 6 to avoid ambiguities.
    -   Other changes to conform better with Russian braille rules.
    -   A new table that indicates capital letters was added. This is the new recommended Russian table for braille display users.
    -   Removed the old `ru-ru-g1.utb` in favor of `ru-litbrl.ctb` and `ru-litbrl-detailed.utb`.

Other changes
-------------

-   Support for Python 2 has been removed. The python bindings now only support Python 3. The deprecation notice was announced in Release 3.13 and the removal is finally done now.
-   Improvements to the placement of emphasis and capital indicators.
-   The documentation for the emphasis opcodes has been further improved thanks to Bert Frees.

Deprecation notice
------------------

-   None

Backwards incompatible changes
------------------------------

-   `emphmodechars` can and must now be set per emphasis class.

Invisible changes
-----------------

-   The emphasis and capitalization handling code has seen major streamlining, simplification and tidying thanks to Bert Frees.

New, renamed or removed tables
------------------------------

### New

-   ba.utb
-   ru-litbrl-detailed.utb
-   en-us-emphasis.uti

### Renamed

None

### Removed

-   ru-ru-g1.utb
