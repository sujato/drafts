# Nilakkhana: SuttaCentral Markdown extension

Markdown is eating the world. Great! I love using it. By focusing on a specific and limited set of features it avoids the bloat of complex markup languages.

I propose that we develop our own extension of Markdown. This is a specialized implementation that will make use of only part of the Markdown spec, while requiring non-standard features. It will generally aim to be compatible with MD philosophy and specifics, but may assign special functions to things that differ from MD.

We don’t need to work out Markdown solutions for everything, but can evolve it on a case by case basis. The main scope is to use for inline markup in segmented texts. Ultimately it should be replaced with standoff properties.

Use the [CommonMark spec](https://commonmark.org/) as the starting point.

## Basics

- **Emphasis**. Markdown treats `*asterisks*` and `_underscores_` as synonyms, both generating `<em>` tags. Let us distinguish them so that `*asterisks*` = `<em>` and `_underscores_` = `<i>`, used for foreign words.
- **Numbered lists**. As per Markdown, use 1. … 2. … 3. … to mark the start of numbered list items. These occur inline with no line break in segments.

In certain texts, mainly in the Anguttara Fours, I use lists within a segment. Markdown uses `\n\d.\s` or `\n\d)\s`. Since we do not have line breaks inside a segment, the logic is: If a segment starts with `1.\s`, then that and any following occurrences of `\d.\s` indicate the start of a numbered list item. Note that if each list item is a segment, standoff markup is used instead.

## Text-critical

Traditionally, text-critical markup is often indicated with plain-text conventions. This may be seen on GRETIL, and we used it for bendall-cv. Given the range of text-critical markup, it will be a challenge to represent it all. I am thinking here specifically about what can be used by our typists for DPCV.

In the MD spirit, our conventions should aim to fulfill three requirements:

1. Easy to type, which means sticking to symbols directly on keyboards.
2. Pleasant to read, saying close to familiar conventions.
3. Unambiguous.

It's not easy to achieve all of these goals. To get around it we can relax the first condition in the case of conventions used in texts adopted from outside, rather than those we type ourselves. This applies mostly to areas involving editorial intervention: marking text that is apparently incorrect (sic!) or corrected or reconstructed. In such cases we can use glyphs from the broader Unicode palate.

I give more-or-less equivalents to HTML or CSS. Note, however, that these marks will *not* convert directly to HTML, but to standoff markup. Therefore there is no need to be concerned about the overlapping hierarchy problem, eg. what to do if unclear text crosses paragraphs. These issues are dealt with when converting standoff to HTML or another markup language.

We shall treat text-critical MD as a separate set of conventions. Our transcribed texts do not have added punctuation, only the native punctuation (usually `|`) in the manuscript.

Note that the deleted/inserted/substitution and incorrect/corrected/correction triplets are essentially the same thing, except one is by the scribe and one by the editor. Thus they are indicated with similar glyphs, doubled in the case of the modern editor.

Mark | Definition | Note | Markup
---|---|---|---
`{`abc`}`  | extra text  | Use when the new edition has significantly more text than the reference edition. It will be inspected later and if necessary new segments created. Use {curly brackets} because this is a “set” of segments. |
`(`abc`)` | unclear text | Text damaged to an extent that makes the reading (un)certain. BUT () is used in MS edition. |  `.unclear`
`+` | unreadable akṣara | An akṣara so damaged that it cannot be read, but a rough count of the number of akṣaras can be made.| `.gap`
`[++++]` | unreadable span | A span of unreadable akṣaras of undetermined length. Use exactly four +. | `.gap`
`-[++++]-` | unreadable line | The line or part of it is visible but unreadable. Use exactly four +. | `.gap`
`^` | missing akṣara | An akṣara that has broken off from the manuscript, but a rough count of the number of akṣaras can be made. The caret is often used to indicate something is missing. | `.gap`
`[^^^^]` | missing span | A span of missing akṣaras of undetermined length. Use exactly four ^. | `.gap`
`-[^^^^]-` | missing line | An entire line is missing due to manuscript loss. Use exactly four ^. | `.gap`
`#`123 | reference number  | If the manuscript has any reference numbers, indicate with #. | `.counter`
`-` | new line | Indicate line break in manuscript. Don’t write the numbers, they will be calculated later. | `<br>`
`@` | new page  | Indicate page break in manuscript. Don’t write the numbers, they will be calculated later. | CSS `page-break-after`
`~`abc`~` | deleted text  | Text crossed out or otherwise marked for deletion `~deletion~` by a scribe.  | `.del`, `<del>`
`>`def`<` | inserted text | Text overwritten >or added to the main text< by a scribe. | `.add`, `<ins>`
`~`abc`~>`def`<` | substitution  | Text `~croslsed~>crossed<` out and replaced by a scribe. Arrow indicates direction. | `.del`, `<del>` + `.add`, `<ins>`
`≈`abc`≈` | apparently incorrect text | Text identified by an editor as being ≈uncorrect≈, such as a misspelling. |  `.sic`
`⪢`def`⪡` | corrected text | Corrected version made by an editor of text that appeared to be ⪢incorrect⪡ in the manuscript. |  `.corr`
`≈`abc`≈⪢`def`⪡` | correction | Text that was apparently ≈uncorrect≈⪢incorrect⪡, but for which an editor offers a correction. |  `.sic`, `.corr`
`[`abc`]` | restored text | Text rec[onst]ructed by an editor from damaged or lost portion of manuscript. |  ``
`⟦`abc`⟧` | uncertain restoration | Text c⟦onjectural⟧ly reconstructed by an editor from damaged or lost portion of manuscript. |  ``
`⟨`abc`⟩` | inserted text | Text ⟨omitted by mistake by the⟩ scribe and inserted by a modern editor. |  ``
`⟪`abc`⟫` | uncertain insertion | Text omitted by mistake by the scribe and ⟪conjecturally⟫ inserted by a modern editor. |  ``
`«`abc`»` | speaker | A note in the text identifying the speaker.  | `.speaker`
`←`abc`→`  | pe, peyyala  | Sign of expansion. An indication in the text that text is to be expanded. Do not use for every simple "pe", only when there are instructions in the text.  | `.pe`

### New line and new page

When it comes to marking new line `-` and new page `@`, spacing needs to be handled consistently.

Manuscripts do not have any special way of treating end of line, they simply continue on. Thus words can be broken, and sometimes those words may be very long. So when adding breaks inside words, leave no space. Using the hyphen `-` for line breaks imitates the normal conventions for line breaks in modern texts and minimizes visual disruption.

If the break occurs between words, however, a space must be added. Since most agents strip trailing spaces but not starting spaces, it is best to add a single space *before* the mark. This applies also in the case of a mark for missing or unreadable line.

We also must consider the case when a line or page break occurs at the same point as a new segment. In such cases, leave the break mark at the end of the prior segment.

Hence, in the case of both new line `-` and new page `@` breaks, do the following:

- **Inside a word, leave no space**:
  -  like th-is or th@is.
- **In between words, leave a single space before the mark**:
  - like -this or @this.
- **For missing or unreadable lines, leave a single space before the mark**:
  - like -[^^^^]-this.
- **On segment breaks, place mark at the end of the prior segment**:
 - like this.-
 - or like this.@

### Spanning segments

It will frequently occur that a marked span will cross over more than one segment. No special treatment is required, simply mark as usual.

    : Here is some text, (and some that is
    : uncertain) and it becomes clear again.

The same applies if it covers multiple segments.

    : Here is some text (and some that is
    : uncertain and even more
    : that is uncertain) and it becomes clear again.

When marking unreadable or missing aksaras, treat the two halves of the mark as an opening and closing pair.

    : This text is followed by an unreadable span [++
    : ++] and later it is readable again.

If the span covers multiple segments, leave the intervening segments blank.

    : This text is followed by an unreadable span [++
    :
    : ++] and later it is readable again.

Unreadable lines are treated exactly the same.

    : This text is followed by an unreadable line -[++
    :
    : ++]-and later it is readable again.

For missing spans or lines, do the same, using ^ instead of +.
