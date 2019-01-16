# Eka = One: On the unreasonable effectiveness of consistency in sutta translation

Language is all about context. Words don’t have rigid meanings, and their precise nuance can only be inferred from where they are, and how they are used in that very particular case. For this reason it is normally the case that translators don’t translate word-for-word or literally; in fact, truly literal translation is impossible, and in my view is barely even coherent as a concept.

And this was how early generations of translations from Pali were done. Each context was taken and rendered as the translator saw fit. Within one book there may be several different renderings of the very same passage. With few qualified scholars and a large body of texts, it is perhaps unsurprising to find such looseness prevailing.

Around the middle of the 20th century, however, a young English monk named Nyanamoli developed a quite different approach. In his ten years working as a translator—cut short by his tragic death—he moved more and more towards a strict system of one-to-one rendering of Pali terms. This project remained unfinished, and certain terms—notably _dhamma_—seem destined to frustrate any such attempt. Nyanamoli’s project was taken up by Bhikkhu Bodhi, who used a similar approach, albeit more tempered and flexible. But still, by and large he maintained the use of a single consistent rendering for terms, especially those of doctrinal significance.

I have always enjoyed this approach. My first suttas were Nyanamoli’s translations. Despite the sometimes rigid and elusive phrasing, I always felt that such an approach gave me a confidence that it represented the underlying text quite precisely. Going to more fluid translators I felt an unease; it seemed like more of the translator was coming through, rather than the text.

Despite this, when I started my translation project, my thought was that I would not prioritize consistency so greatly. I wanted to make my translation more fluid and idiomatic, so in some cases I abandoned the more formally consistent terms used by Bhikkhu Bodhi. For example, he uses “visual form” to stand for _rūpa_ as the thing that is seen; to me, the normal English word for this is “sight”, so that’s what I use. This is more idiomatic, at the expense of losing connection with “form” in the five aggregates.

However, as I proceeded, I found that again and again, my attempts at a more flexible approach were undone by the texts themselves. It turned out that often, what I thought was flexibility was really just an excuse for not paying attention. Contexts that I assumed were separate turned out, in another place, to be closely related. And so in many cases I returned to a more consistent approach.

Sometimes people seem to think that using a consistent approach stems from a rigid and naive theory of language, or a dogmatic fear of incorrectness. But that’s just not the case: it evolves from the experience of actually translating thousands of suttas.

Let me give an example of the kind of situation that I mean. I’m going to use a made-up example here for simplicity. But this kind of thing occurs throughout the suttas.

Let’s say we have a sutta that says:

> *Rāgo pahātabbo, lobho pahātabbo, chando pahātabbo*

Taking the most literal translation we might say:

> Lust is to be given up, greed is to be given up, desire is to be given up.

Now, we might prefer to avoid the passive voice in English. Also, it seems reasonable to combine the three terms:

> One should give up lust, greed, and desire.

And that’s probably how I would translate it. But of course these three terms are synonyms, and one might think there is nothing to be gained by presenting all three synonyms. And this is fair enough: there are plenty of cases where it makes sense. So maybe we could say:

> One should give up desire.

Or maybe:

> One should give up all forms of desire.

And I think that any of these would, all things being equal, be a fine translation.

But then suppose that down the track—maybe in another nikaya—we find the same phrase repeated again. Except this time, it is broken up into three separate suttas. This kind of thing happens a lot in AN especially.

1.  *Rāgo pahātabbo.*
2. *Lobho pahātabbo.*
3. *Chando pahātabbo*

Now what to do? You can’t just say the same thing in every sutta. If you want to represent the three suttas accurately, you have to present a different term each time:

1. One should give up lust.
2. One should give up greed.
3. One should give up desire.

But the text is, in fact, identical with the previous case. There’s no variation in context that would justify a different rendering. It just happens to be split across three texts. So you end up translating exactly the same thing in different ways, purely because of the formal features of how the text is divided. In this way the translation loses accuracy; information is eroded.

Now, surely we can find a way to manage this case. And there are contexts where such flexibility is warranted. But what I found was that by maintaining the 1-to-1 translation approach, I was able to solve countless similar problems. It is a simple technique that solves a wide range of different kinds of problems.

In science, such a solution is described as “elegant”. And there is something to elegance, or so it seems. Surely the fact that a method is so effective is no mere accident; it reveals something about the subject.

Since I have been coding suttas in HTML for so long, it seems to me natural to make an analogy with how HTML works. Beware: geekiness follows!

Normally on an HTML page, everything can affect everything else. Things have a global scope; that is to say, context rules. So if I have a paragraph of text on one page, it might display with a sans serif font and a grey color. Then I paste the same paragraph into another page, which has serif font and blue color; the paragraph will inherit the styling of the new context. This is how we get things looking consistent on web pages.

This all works fine in many cases, but sometimes you want something to not inherit the styles from around it. Maybe you want to use a widget, say a drop-down menu, but the styles from the rest of the page conflict, so things behave unexpectedly. What to do? Well, to solve such issues some smart people invented the idea of “web components”. These are specially-defined HTML elements that live inside what’s called a ShadowDOM. There, they neither affect nor are affected by anything that happens elsewhere on the page. A web component is just a set of files that contain whatever HTML, CSS, or JS that you like. You can import a web component and just drop it into any page or framework, and it will look and behave in exactly the same way.

To look at it less technically: most HTML is like play-doh, while web components are like lego. Play-doh is nice and malleable, you can do whatever you want with it; but it tends to get wobbly and fragile, especially when there are lots of details. You push in at one place and it bulges out at another. Lego, by contrast, is easy and robust: snap the parts into place and off you go. The cost is that you lose flexibility and creativity. The problem with this analogy, though, is that you can’t mix up play-dough and lego, but  regular HTML and web components can be mixed as you like.

Okay, so the point is this: when we normally use language, it’s much like HTML, or if you prefer, play-doh. It’s flexible and contextual, with words and phrases taking on nuances and implications that vary each time. Such a use of language is powerful, but fragile; it’s easy to break meaning by misreading a nuance. So if you want to accurately and robustly preserve meaning, you sacrifice some of that flexibility and use language rather more like web components, or if you like, lego. Words, phrases, and passages have a set and consistent meaning. The sense is not derived from the immediate context, but from *somewhere else*. They are defined in one place and just dropped “as-is” into different contexts. And just as we can make many different web pages—or lego toys—by clicking together the individual components in different ways, we can make many different suttas by recombining components.

Sometimes such an approach is decried as being “artificial”. But I don’t really think this is accurately describing what is going on. There’s nothing more or less “natural” or “artificial” about either approach. One is more specialized than the other, true, but really they are just different aspects of how language is used. This is why I like the HTML analogy: web components are a part of the HTML spec; they are just as much “native” HTML as anything else. Or consider a child playing “in nature”: they might build a wall for their castle by shaping up mud; or they might take a stone of the right shape and just use it “as-is”. Both are perfectly natural.

I suspect if we were to carefully analyze spoken language we would find variations on the degree of contextuality. In the suttas it is the same, it is just that the weight and emphasis is shifted, quite considerably, in the direction of “components”.

That is not to say that words are never affected by context. Obviously they are, and a careful translator will always be testing and checking what applies in a given context. There are even places where a word or phrase has the same meaning, but a different rendering is required, because the semantic ranges of different languages don't map one-to-one.

There are plenty of cases like this where different approaches are required. But a sutta translator, aware of the degree to which texts are “componentized”, should be always on the lookout for defining contexts that make the meaning clear. By weighting consistency more highly than usual, and preserving a certain resistance to adjusting renderings in different contexts, I found, on the whole, that it pays off in the end, forestalling all kinds of problems that I didn't even anticipate. I have rarely encountered a case where I used a consistent rendering and later found that it had to be inconsistent; on the other hand, I frequently found that a formerly inconsistent rendering was better served by making it consistent.
