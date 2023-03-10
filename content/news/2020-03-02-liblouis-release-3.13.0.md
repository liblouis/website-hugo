---
categories: Liblouis
title: 'Liblouis Release 3.13.0'
date: 2020-03-02
---

A tremendous amount of work by lots of different people has gone into this release. Bert Frees for example added new opcodes, fixed long standing bugs (with emphasis and capitalization), made the documentation more clear and helped table contributors bringing in their improvements. Bue Vester-Andersen added major improvements to Danish and German braille. This release also contains much improved tables for Afrikaans, Russian computer braille, Urdu and Chinese.

On a personal note I\'d like to say that this is the 20th release of liblouis shipped by the current release team Bert Frees and Christian Egli. I hope we can continue to do so.

For a detailed list of all the changes refer to [the list of closed issues](https://github.com/liblouis/liblouis/milestone/23?closed=1).

New features
------------

-   The `nocross` opcode has been made into a prefix opcode, which means that it can now be used in combination not just with the `always` opcode but also with other translation opcodes such as `begword`, e.g. `nocross begword sh 146` for example. The old usage of the opcode no longer works, see [Backwards incompatible changes](#backwards-incompatible-changes).
-   Added a new opcode `rependword`, needed to implement Malay braille. Thanks to Bert Frees.
-   Emphasis and capitals can now be marked correctly in more cases. Thanks to Bert Frees.
    -   When `begemphword` (`begcapsword`) is defined but not `endemphword` (`endcapsword`), use `emphletter` (`capsletter`) to mark every character in an emphasized (capitalized) part that ends in the middle of a word.
    -   When `begemphword` (`begcapsword`) and `begemph` (`begcaps`) are both not defined, use `emphletter` (`capsletter`) to mark every emphasized (uppercase) letter.
    -   `capsnocont` has no influence anymore on whether `capsletter` is used for every uppercase letter or not, see [Backwards incompatible changes](#backwards-incompatible-changes).

Bug fixes
---------

-   Fix a crash on sparc64 thanks to Samuel Thibault.
-   Fixed a bug where the `inputPos` array was not monotonically increasing. This is a problem for language bindings that try to do hyphenation based on this information. Thanks to Bert Frees.
-   A couple of small Coverity fixes thanks to David King.
-   Fix an infinite loop involving multipass rules and backtranslation thanks to Bert Frees and Bue Vester-Andersen.
-   Fix several problems in the Python bindings thanks to Leonard de Ruijter, ??ukasz Golonka and Andr??-Abush Clause:
    -   Ensure that the mbcs encoding is always used to encode file path on Windows, especially when \'Unicode UTF-8\' feature is enabled.
    -   `getTypeformForEmphClass` was passed a decoded string on Python 3 instead of an encoded one.
    -   The same applies to `compileString`. We encoded the input string, but never used that encoded one when passing it to liblouis.
-   `begemphword` (`begcapsword`) and `endemphword` (`endcapsword`) are now used for single letters within a word when `emphletter` (`capsletter`) is not defined.
-   For backward translation the returned input length is now equal to the initial input length (as it is for forward translation) thanks to Bert Frees.

Braille table improvements
--------------------------

-   Improvements to Afrikaans thanks to Christo de Klerk
    -   Fixed back translation of some lower words.
    -   Fixed several contraction errors where contractions are based on pronunciation or occur where compound words join.
    -   Eliminated grade 1 indicator where a single letter follows a single apostrophe to indicate an abbreviated word, e.g. \'k for ek.
    -   Corrected the use of the grade 1 indicator in grade 2 with signs which would conflict with contractions, such as the trademark sign that would conflict with the contraction of tussen.
    -   Fixed the back translation conflict between the UEB circle shape indicator and words containing \$= being the contraction for \"alge\".
-   Improvements to Russian computer braille table thanks to Andrey Yakuboy.
    -   The table is now based on the Unicode character set. A lot of new characters were added that aren\'t in KOI8-R, including Greek, Hebrew, accented letters and so on.
    -   For special characters we now follow the definitions from other software (JAWS, TSS, DBT) instead of following the American standard.
-   Improvements to Urdu Braille thanks to Jake Kyle
    -   Changed definition of \x0624 (Waw with hamza above) from dots 1256 to dots 3-2456 following advice from proof reader.
    -   Added 2 character versions of letter plus diactric (previously only the one character versions defined):
-   Updates to the Danish Tables thanks to Bue Vester-Andersen:
    -   Fixed back-translation for some JAWS Braille drivers, which deliver Unicode characters to Liblouis as input from a Braille keyboard.
    -   Ensured proper use of letsign in connection with accented letters.
    -   Re-arranged and strengthened tests to include all Unicode characters defined in the tables.
-   Updates to the Chinese braille table (`zh-tw.ctb`) thanks to Bo-Cheng Jhan, Coscell Kao and Victor Cai.
-   New experimental German tables for grade 0 (Basisschrift) and grade 1 (Vollschrift) that are more suitable for back-translation, thanks to Bue Vester-Andersen.
    -   All capital letters are marked.
    -   Accented letters are translated using `de-accents-detailed.cti` to make the translation as detailed as possible.
    -   Apostrophes and single quotation marks are translated the same.

Other changes
-------------

-   The documentation for the emphasis opcodes has been reworked and is now much more clear and accurate thanks to Bert Frees.

Deprecation notice
------------------

-   Python 2 is [no longer maintained](https://www.python.org/dev/peps/pep-0373/) since the beginning of this year. The current liblouis Python bindings work with both Python 2 and 3. However the support for Python 2 will be dropped in the next release (3.14) at the beginning of June 2020. If you have code that uses the liblouis Python bindings with Python 2 then please refer to the [official porting guide](https://docs.python.org/3/howto/pyporting.html) for help with migrating it.

Backwards incompatible changes
------------------------------

-   Since the `nocross` opcode has been made into a prefix opcode, it must now be used in combination with another opcode. For example `nocross sh 146` must now be written as `nocross always sh 146`.
-   The `capsnocont` opcode can not be used anymore to control whether `capsletter` is inserted for every uppercase letter. This now depends on whether `begcaps` and `begcapsword` are defined.

Invisible changes
-----------------

New, renamed or removed tables
------------------------------

### New

-   de-g0-bidi-core.uti
-   de-g0-bidi.utb
-   de-g1-bidi-core.cti
-   de-g1-bidi.ctb

### Renamed

None

### Removed

None
