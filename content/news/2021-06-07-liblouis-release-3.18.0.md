---
categories: Liblouis
title: Liblouis Release 3.18.0
date: 2021-06-07
---

This release brings support for many new languages: There is support for six new languages from South Africa, Northern Kurdish, Kazakh, Tatar, Yakut, Bulgarian literary braille and finally Khmer, Burmese and Vietnamese. Aside from that there are also major improvements to Afrikaans, Russian literary braille, Uzbek and Hebrew Computer Braille.

I\'d like to thank everybody for helping to bring liblouis forward.

For a detailed list of all the changes refer to [the list of closed issues](https://github.com/liblouis/liblouis/milestone/28?closed=1).

Bug fixes
---------

-   Don\'t silently ignore the last line of a table when it doesn\'t end with a new line character. Thanks to Bert Frees.

Braille table improvements
--------------------------

-   New contracted braille table for the isiXhosa and isiZulu languages created by Christo de Klerk and Laurent Cadet de Fontenay at the request and under the auspices of the South African Braille Authority.
-   New contracted braille table for the Sesotho, Setswana and Sepedi languages created by Christo de Klerk at the request and under the auspices of the South African Braille Authority.
-   New braille table for Northern Kurdish thanks to Imam Kahraman.
-   Fix a problem with \'\]\' in Finnish 8 dot braille thanks to Christian Egli. The real problem was an unintended continuation line.
-   Major update to the grade 2 Afrikaans table. It now implements the new Afrikaans rules adopted and implemented recently by the South African Braille Authority. The rule changes simplify and rationalize the rules, especially those based on pronunciation. 571 of the list of 25912 test words were impacted by the changes and all have been corrected.
-   Improvements to the Russian literary braille tables thanks to Andrey Yakuboy and Bert Frees:
    -   Fixed a bug in ru-litbrl-detailed.utb that was causing a capital sign to be missing for Cyrillic uppercase letters after Latin letters.
    -   Fixed a bug in ru-litbrl-detailed.utb that was causing a number sign to be missing in some cases.
    -   Added more accented letters
-   New tables for Kazakh uncontracted, Tatar uncontracted and Yakut uncontracted braille thanks to Andrey Yakuboy.
-   Added more apostrophe symbols to English Computer Braille Code table thanks to BAUM Engineering.
-   Small fix to Italian computer braille thanks to Simone Dal Maso
-   New table for Bulgarian literary braille thanks to Румяна Каменска.
-   Fixes to Uzbek grade 1 thanks to BAUM Engineering.
    -   capital sign for Roman numbers
    -   signs (math, parentheses and other)
    -   sh and ch inside a word
    -   g and o with different accent marks
-   Major overhaul of the 8 dot Hebrew Computer Braille table thanks to Adi Kushnir
    -   Fixed Hebrew input to properly work. It did not work at all before.
    -   Added Russian support
    -   Added special European characters
    -   Fixed Arabic support.
    -   Fixed some symbols to comply with the Israeli standard for computer Braille.
    -   Changed display name from Israeli Multilingual to just indicate Hebrew.
-   New tables for Khmer, Burmese (contracted and uncontracted) and Vietnamese (uncontracted, partially and fully contracted, as well as a variant for Southern Vietnam) thanks to Dang Hoai Phúc.

Other changes
-------------

-   Brilliant simplification of the table parser internals thanks to Bert Frees

New, renamed or removed tables
------------------------------

### New

-   kk.utb
-   sah.utb
-   tt.utb
-   xh-za-g1.utb
-   xh-za-g2.ctb
-   zu-za-g1.utb
-   zu-za-g2.ctb
-   nso-za-g1.utb
-   nso-za-g2.ctb
-   sot-za-g2.ctb
-   tsn-za-g2.ctb
-   bg.utb
-   kmr.tbl
-   vi-vn-g0.utb
-   vi-vn-g1.ctb
-   vi-vn-g2.ctb
-   vi-saigon-g1.ctb
-   my-g1.utb
-   my-g2.ctb
-   km-g1.utb

### Renamed

None

### Removed

-   he.ctb -\> superseded by he-IL-comp8.utb
-   vi-g1.ctb -\> superceded by vi-vn-g1.ctb
