# SuttaCentral Upgrade 2018: Polymer 3+

## Background

In 2017/2018, SC was completely rebuilt as a PWA on top of Polymer 2.x. In early 2018, P3 was released. This uses JS modules rather than HTML Imports, and is based on NPM. While the basic API remains the same as P2, the advantages are:

- Based on the final agreed spec for web components, so ultimately should be polyfill-free.
- Can be packed with WebPack etc.

The upgrade from P2 to P3 is automated using Polymer’s  [modulizer](https://github.com/Polymer/tools/tree/master/packages/modulizer).

In addition, the Polymer team announced the deprecation of the polymer base class, superseded by [LitElement](https://github.com/Polymer/lit-element). They now recommend that new apps build on LitElement and old apps upgrade when possible.

While building the app, we encountered a number of cases where the existing Polymer elements were buggy and apparently unmaintained. Monica of the Polymer team [has explained that](https://www.polymer-project.org/blog/2017-11-27-future-of-elements.html) the old elements were left as-is while the focus was on core development. A new generation of elements based on LitElement is being released ([MDC Web](https://github.com/material-components/material-components-web)), and has now become Google’s core element set.

As of writing, LitElement and MDC Web have not reached 1.0 release. However it is only IE11 support that is blocking 1.0 release, and otherwise the API should be stable.

## On LitElement

Since LitElement is the upgrade path for Polymer apps, we should, in time, transition the entire site over to it. This will, it is hoped, reduce code bloat and make the site more performant and flexible.

The Polymer blog says this about [upgrading to LitElement](https://www.polymer-project.org/blog/2018-05-02-roadmap-faq.html):

>Unlike the migration from Polymer 2.x to Polymer 3.0, the path to adopting LitElement is not formulaic – it will depend on how your element or app is currently implemented.
>
>That said, it’s not necessarily hard. First, thanks to the inherent interoperability of web components, you can upgrade your app or element collection one piece at a time; elements you’ve built with or upgraded to LitElement can sit alongside and interact with elements you’ve built using previous versions of the Polymer library.
>
>Elements and apps you’ve built following the basic precepts of unidirectional data flow (e.g., data flowing from above via one-way bindings) should also be straightforward (though not mechanical) to migrate.

SC uses unidirectional data flows with Redux, the same as Polymer’s PWA Starter Kit, so hopefully the upgrade path from P3 to LitElement will not be too hard.

Since we have no experience working with LitElement, it is difficult to assess how complex the upgrade path will be. Should we do this now, or wait until the next upgrade cycle? This will hopefully become clear as we work with it.

I suggest that we take advantage of the interoperability mentioned above, and upgrade each part of our app to LitElement whenever it seems useful.

This may apply in cases such as:

- Performance improvents
- Bugfixes
- New functions
- Anywhere that the LitElement alternative looks cool

As a general rule, if faced with a non-trivial problem, we should ask: will LitElement help? Or at least, if we are to invest time and effort into fixing the problem, should we not invest that time on the platform of the future?

## Late 2018 Upgrade

Starting in August 2018, SC plans to upgrade the app. There are three stages to this.

1. Core upgrades (1 month?)
2. Bug fixing (1 month?)
3. New features (2 months?)

Unlike the previous work, here the changes are incremental. For this reason, apart from the first stage, this cycle is somewhat open-ended. We can continue making improvements until we run out of ideas or money. Somehow I can guess which will come first! I estimate the entire cycle will be between 3–6 months.

We don’t need to define stage 2 & 3 very completely yet. This can be done while doing stage 1.

We will employ STXnext to implement this, as we were happy with their work last time. We anticipate using one full time developer and a part time tester. Others may be engaged as needed.

## Core Upgrades

There are four key areas we need to upgrade. These make up the basic must-have of our current cycle. I estimate each of these will take about 1 week, on average. Once these are completed to our satisfaction, we can roll the set of changes to the live site. That way we can get user feedback while we’re developing further features.

### 1. Upgrade to P3

This should in theory be entirely automatic. In theory!

### 2. Pack it and shake it

Mentioned by Hubert as one of the key advantages of P3, WebPack allows the app to be cleanly packed and supports tree-shaking. Hopefully this will result in smaller bundles and a faster app.

There are a bunch of similar libraries, we should use whatever the devs think is best.

### 3. Make it go fast

When building the site, we did not do very detailed performance testing. Personally, I am not that happy with the site performance: it is not as snappy and clean as Google’s own PWA sites. Let’s see if we can make it better!

We should do a detailed analysis of site performance in different scenarios. Optimize as much as possible and see where possible future improvements may lie.

### 4. PWA betteration

One of the best features of the site is the offline capability provided by service workers. However users report quite diverse experiences with the PWA. For some it works fine, but for many it does not. We need to test this in detail and ensure it is as robust as possible.

## Bug Fixes

Shocker, there’s a bunch of bugs on Github. Let’s spend a few weeks squashing as many as possible. Of course, there will be new ones with the upgrade!

Bug fixes should be pushed live ASAP.

## New Features

The fun stuff. There are a bunch of proposals for doing some cool new things with SC. These can be launched as each feature is ready. In no particular order:

### Audio Support

Some of our friends are making audio files from reading the Suttas. [We can do some cool stuff here.](https://github.com/suttacentral/suttacentral/issues/961)

- Aggregate the audio files on our own servers, ensure a consistent quality, URL, and so on. (Blake?)
- Implement a UI in our suttaplex cards for reading suttas. (STXnext)
- Set up podcasting.
- Set up audio suttas on demand via Alexa, Google Home, Siri, etc.

### Improving site metadata and documentation via RDF

With BDRC, [we have agreed to move towards supplying metadata for texts, etc. via RDF](https://github.com/suttacentral/suttacentral/issues/1028). Two aspects:

1. Put data in RDF format according to the BDRC schema. Start with the new texts created by SC.
2. Implement the data in our UI.
   - Use for texts in the metadata fields.
   - Use for “Language” pages (see next).

A volunteer, Anders, is looking into this. We anticipate it will take some time, and it may well be not ready for this cycle. We wouldn’t expect STXnext to do the RDF part, only the UI.

### Make it easier to find translations in your language

We have begun the process of localizing the site, and translation teams in Indonesian and Chinese are well under way. However this brings us to one of the problems that we are yet to solve: how are you to find where translations are in your language?

Here I propose [two complementary ideas to assist with this](https://github.com/suttacentral/suttacentral/issues/1078).

- Yellow Brick Road: Highlight sidebar menu items that contain translations in your language.
- Introduce a new “Languages” facility to provide detailed information on the texts available in each language. Available via Home page Tab bar?

### Create unified Setting dialog

[One central place for all settings.](https://github.com/suttacentral/suttacentral/issues/1081)

### Improve handling of references

Our complex sets of interrelated references make up one of the most powerful yet difficult areas for SC. A number of improvements have been proposed.

1. [Use standoff references in segmented texts](https://github.com/suttacentral/suttacentral/issues/1056).
2. [Simplify front end handling of references by creating three classes for references](https://github.com/suttacentral/suttacentral/issues/1055)
3. Fix incorrect reference handling in certain cases.

### Make universal elements

One of the promises of web components is that they can be just dropped in and work anywhere. The lightness of LitElement should make this better than ever. We can look at cases where SC’s elements can be used, not just on SC, but anywhere. Candidates include:

1. Suttaplexes: use SC reference IDs (MN 1, etc.) to call up the relevant suttaplex card (similar to former functionality on Discourse)
2. Pali/Chinese lookup

We could use these on Discourse (our forum) and Pootle (our translation software), and make them available to other sites. Ideally, any blog, sutta site, discussion forum or whatever could just include the web component and leverage the same functionality.

### Support comparison of multiple editions of root texts

We are currently engaged in digitizing the oldest Pali manuscripts, from the [9th](https://github.com/sujato/bendall-cv) and [13th](https://github.com/dpcv) centuries. In addition, there are multiple editions of the texts in Pali, Chinese, and Tibetan. Over time, we can add more of these to the site, implementing a convenient way to compare them.

These texts will be segmented. They can be displayed through the Textual Information dialog, which will show them segment by segment as with the translations. In addition, we can implement a diffing library to shows differences between editions.

### Support export to PDF and EPUB

A long term desideratum has been the export translations from PO to [PDF for printing](https://github.com/suttacentral/suttacentral/issues/960) and EPUB. In fact much of the back end for this is in place. The main thing is to figure out the UI.
