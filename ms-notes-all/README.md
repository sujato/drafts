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
- Why are these marked like this, rather than simply wrapping the words in the same note? I don't know. It would make sense if the span was long, or if it covered multiple `ms` sections, but only a few do this.

Some examples.

- 1V:280.  The BN marks the beginning of the word ⁕khittacittassa, and the EN marks end of the word vedanāṭṭassa⁕. Okay, so this text appears on SC here: https://suttacentral.net/pli-tv-bu-vb-pj2/pli/ms#90. Note that the note does appear as a Variant Reading. However the markup is not properly formed. Worse, the critical part of the text is missing. The note says "the passage between these points is *not* found in these editions" (*potthakesu natthi*). But the word *natthi* is missing from our note, giving exactly the wrong meaning. Oops!
- 27Pe:15. This appears on SC at https://suttacentral.net/pe1/pli/ms#15 . The markup is not correct, but the content is there.
- 27Pe:788. At https://suttacentral.net/pe8/pli/ms#165 . Content is correct, but markup is not.

Let us take another example.

    <tr>
    <td class="ms">7D:626</td>
    <td class="note-type">Ending Notes</td>
    <td class="ms-text">…devānaṃ tāvatiṃsānaṃ paccekapallaṅkesu pallaṅkena⁕ nisīditvā deve tāvatiṃse āmantesi …</td>
    <td class="note-content">paccekapallaṅkesu paccekapallaṅkena (sī. ka.-ma.), paccekapallaṅke (syā1-3. kaṃ.)</td> </tr>
    <tr> <td class="ms">7D:626</td>
    <td class="note-type">Beginning Notes</td>
    <td class="ms-text">…tettiṃse attabhāve abhinimminitvā devānaṃ tāvatiṃsānaṃ ⁕paccekapallaṅkesu pallaṅkena nisīditvā deve …</td>
    <td class="note-content"></td> </tr>

The note starts in BN at `⁕paccekapallaṅkesu` and ends in EN at `pallaṅkena⁕`. The content says that the first stated variant is from the first set of bracketed editions, while the second stated variant is from the second set of bracketed editions. So far so good. But here’s where it gets weird.

In the MS text on SC, there are no variant readings: https://suttacentral.net/dn18/pli/ms#sc31

But there are variant readings listed on pootle: https://pootle.suttacentral.net/en/dn/translate/dn18.po#unit=43937

But they do not appear on the pootelized text: https://suttacentral.net/dn18/en/sujato#20.1

Finally, the text on SC is not the MS text! According to the table, it should read *devānaṃ tāvatiṃsānaṃ paccekapallaṅkesu pallaṅkena nisīditvā* , but in fact it reads *devānaṃ tāvatiṃsānaṃ pallaṅkena nisīditvā*.  I.e. *paccekapallaṅkesu* is missing. Thus the mainline text on SC misses the element of *pacceka* (“individual”) even though it is found in all the variants.

Fortunately I translated it according to the variants!

So there are multiple issues with the BN/EN:

- Sometimes the mainline text gets garbled.
- Sometimes notes get lost between pootle and SC.
- Sometimes content is missing from the notes.
- Sometimes markup on notes is wrong.

I propose we thoroughly review the BN/EN.

I have made a start on this by creating a new file `en-bn-dedup.html`. This contains, I believe, the whole content of the BN and EN. Here is the method I used.

1. Put each entry on one line.
2. Eliminate duplications (dedup) using http://www.text-filter.com/tools/remove-duplicate-lines/. This resulted in about 200 unique entries, down from 2112. I have done this for all the types of notes, not just bn/en. This consistently results in about 10% of the original size.
3. Sort the entries.
4. Go through each one by one and make it into a single note rather than a pair of BN/EN. Mostly this was straightforward, but in a few cases it was tricky. I consulted the original Mahasangiti files when in doubt. This resulted in the final total of 99 notes.
5. In the few cases where notes spanned more than one `ms` number, I simply marked the first phrase and indicated the scope of the variant in the notes. This avoids the gnarly problem of overlapping hierarchies in HTML. I reworded these notes in English so as to make my editorial intervention clear.
