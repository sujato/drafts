# Notes on notes

In our source files for the Mahasangiti edition, we found the folder `studies.worldtipitaka.org_all_note`, which contained 806 HTML files. These contain what appear to be the complete text-critical apparatus of the Mahasangiti edition, under the title “Nānāpāṭha (Variant Readings & Reference Vols. 1 - 40)”.

The data is, unfortunately, is not in raw form, but is embedded in the HTML scraped from the MS website. This was used by Blake and Vimala as the basis for the variant readings and cross-references found on SuttaCentral.

Here I have extracted the raw data in table form. Each table row contains:

1. The `ms` reference number.
2. The type of note, of which there are four.
    1. Variant readings.
    2. Cross references
    3. Beginning Notes
    4. Ending notes.
3. The text as found in the MS edition, together with an ⁕ indicating the exact position of the note. (Currently changed from `*` so as to avoid confusing markdown.)
4. The note content.

I have made some minor editorial corrections to the punctuation.

## Beginning & Ending

The Variant Readings and Cross references seem straightforward enough. But the Beginning Notes and Ending Notes (BN and EN) are obscure, and so here I will explain what they mean.

- The BN and EN make up just one note, which begins at the point marked in the BN and ends at the point marked in the EN.
- The content of the note is in the EN, while the BN is empty.
- The note content is sometimes a variant reading, sometimes a note explaining that the passage is absent from various editions. Semantically, this can be considered as a kind of variant reading.
- The note content includes both the explanation and the codes for the various editions. When the edition codes appear as simple references, they are (in brackets), but where they appear as part of a sentence in Pali they are not in brackets.
- Not every note explicitly mentions editions. Sometimes we get, eg. *etthantare pāṭho katthaci natthi*, "the included passage is not found everywhere."
- Exactly the same note appears multiple times. No idea why.
- Sometimes the BN and EN appear next to each other, other times not.
- In the version we have on SC, the markup appears often malformed, and sometimes content is incorrect.
- Why are these marked like this, rather than simply wrapping the words in the same note? I don't know. It would make sense if the span was long, or if it covered multiple `ms` sections, but it doesn't, or at least, I haven't found any cases like this.

Some examples.

- 1V:280.  The BN marks the beginning of the word ⁕khittacittassa, and the EN marks end of the word vedanāṭṭassa⁕. Okay, so this text appears on SC here: https://suttacentral.net/pli-tv-bu-vb-pj2/pli/ms#90. Note that the note does appear as a Variant Reading. However the markup is not properly formed. Worse, the critical part of the text is missing. The note says "the passage between these points is *not* found in these editions" (*potthakesu natthi*). But the word *natthi* is missing from our note, giving exactly the wrong meaning. Oops!
- 27Pe:15. This appears on SC at https://suttacentral.net/pe1/pli/ms#15 . The markup is not correct, but the content is there.
- 27Pe:788. At https://suttacentral.net/pe8/pli/ms#165 . Content is correct, but markup is not.
