# A More Systematic Approach to References on SC

## Background

SC inherits tens of thousands of texts, with probably hundreds of different referencing systems. Dealing with these elegantly and predictably is one of the hardest problems that we face. We have over the years discussed this many times, and spent a great deal of time and effort during development to get it right. Nevertheless, the system as it is is deeply flawed. I’ve been trying to think of ways to improve it, and I think I have an idea.

## The problem

We inherit multiple different numbering systems, and they need to be handled in various ways. Ensuring that our system does this correctly in all cases has turned out to be trickier than we thought. Perhaps the problem lies with an insufficient degree of abstraction. We have been doing things case-by-case, and it has not worked out as well as I had hoped.

## A proposed solution

I suggest that we introduce a set of three classes of references. For each item, I give a tick or cross to indicate whether I think it is currently being handled properly. Of course I may be wrong! We can discuss each case in more detail, but this is simply to indicate what areas I think need attention.

1. **First class references:** Each text *must* have one—and only one—set of first-class references.
  - Use for all internal SC coding, processes, and data. ☒
  - Use as the basis for segmenting. ☑
  - Display as “Textual Information” both in unsegmented and segmented views. ☑
  - Use as unprefixed numbering in URLs, eg. `dn1/en/sujato#4.5`. ☒
     - (Prefixed numbering, of course, should work as well, i.e. `dn1/en/sujato#pts-cs4.5` = `dn1/en/sujato#4.5`.)
  - Is the recommended reference system for users. ☒
2. **Second class references:** Each text *may* have zero or more sets of second class references.
  - Display as “Textual Information” in unsegmented view only. ☒
  - Has a URL with prefixed numbering. ☑
  - Maintained for backwards compatibility with older references. ☑
3. **Third class references:** Each text *may* have zero or more sets of third class references.
  - Do not display in “Textual Information”. ☑
  - Maintained as inherited metadata in texts, but is rarely if ever used for referencing. ☑
  - Users can only access them through the raw data, not the UI. ☑

## How to do it

As you know, my understanding of how it all works is very basic, so here are just some thoughts if they are useful.

1. Go through all the texts, identify all the referencing systems in them, and assign them to one of the three classes.
  - Keep this in a new file, `reference-classes.json`?
2. On the front end, inject a `css` class for each reference as appropriate, i.e. `first-class-ref`, etc.
3. Refactor the handling of references throughout the code, so that instead of dealing with each individual kind of reference tag, we simply deal with the three classes.
4. The only time the system needs to know the specifics of the individual references is for naming them.

## UI

Make this system transparent to users, and allow them to choose how to interact with it via the “Textual Information” dialogue.

Replace the current toggle switch with radio buttons (like the text-view buttons). Give three options, with explanation. Note that this UI governs more than just references, so the explanation must reflect that.

>### View textual information
>
>Display information such as reference numbers, variant readings, and other textual apparatus.
>
>1. None.
>    - Just the text.
>2. Display, including first-class references.
>    - Shows textual apparatus, including the standard reference numbers for SuttaCentral. Use this to refer or link to our texts.
>3. Include second-class references.
>    - The same as the previous, but also displays various legacy reference numbers. Use this if you’re looking something up from a source that uses a different system, such as the PTS volume/page numbers.

## Pitfalls and problems

Well, when you refactor things, it’s always complicated. So there’s that!

Also, we should carefully consider the use cases, to ensure that the three classes will be sufficient to work in all cases.
