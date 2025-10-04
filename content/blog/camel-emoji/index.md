+++
date = '2025-10-04'
title = 'Why are there two camel emojis?'
+++

No really, it's kind of weird, right?
Emojis don't just appear --- if you want a new animal emoji, you have to [submit a detailed proposal](https://www.unicode.org/emoji/proposals.html) to prove that your animal meets criteria for novelty and usage frequency to justify its addition to a global standard.
{{< marginnote >}}
We don't even get an emoji for [North America's most beloved marsupial](https://en.wikipedia.org/wiki/Opossum)!
{{< /marginnote >}}
Despite these requirements, we ended up with
two almost identical species of the same type of animal: the one-humped [dromedary camel](https://en.wikipedia.org/wiki/Dromedary) 🐪 and the two-humped [Bactrian camel](https://en.wikipedia.org/wiki/Bactrian_camel) 🐫.

The most widely known and used emojis are defined in [Unicode](https://en.wikipedia.org/wiki/Unicode).
If you're not familiar with Unicode, it's a standard that maps characters, like letters or emojis, to unique numerical values called codepoints.
{{< marginnote >}}
If you want, you can also ["adopt" a Unicode character](https://aac.unicode.org/adopt) on their website. There are currently 4 camel emoji sponsors, all at the lowest tier ($100), one of which is [OCaml](https://en.wikipedia.org/wiki/OCaml).
{{< /marginnote >}}
[Almost all text on the internet](https://w3techs.com/technologies/cross/character_encoding/ranking) is represented using UTF-8, a way of translating these codepoints to bits.
The Unicode standard has included emojis since 2010.

New animal emojis get added to Unicode every year (most recently the [orca](https://www.unicode.org/L2/L2024/24249-orca-emoji.pdf)), so my first thought was that maybe we started with one camel and added the other later.
In the standard for [Unicode 6.0](https://www.unicode.org/versions/Unicode6.0.0/), the first one that includes emojis, there are 44 full-body animal emojis
(codepoints `U+1F400` to `U+1F42C`).
In the most recent standard released this year, Unicode 17.0, I counted 96 full-body animals, over double the 6.0 count.
{{< marginnote >}}
In Unicode 17.0, the animals aren't in contiguous blocks anymore. I found animals in the ranges `U+1F400`--`U+1F42C`, `U+1F980`--`U+1F9AD`, `U+1FAB0`--`U+1FABF`, `U+1F43F`, `U+1F577`, and `U+1FACD`--`U+1FACF`.
{{< /marginnote >}}
However, Unicode 6.0 already includes emojis for _both_ camels --- the animals are almost 5% camels!

So where did the emojis in Unicode 6.0 come from?
Pictographs were originally proposed to be added to Unicode in 2000 as a [response](https://www.unicode.org/L2/L2000/00152-pictographs.txt) to the Japanese phone company NTT DoCoMo releasing a set of pictographs that were added to Shift JIS, another character encoding used in Japan.
Between this proposal and the release of Unicode 6.0, other Japanese phone companies like KDDI and SoftBank were introducing their own sets of icons.
Maintaining compatibility between Unicode and other encodings is a priority for Unicode, hence the eventual inclusion of emojis.

We can see the importance of compatibility in one of the files in the Unicode 6.0 release:
`EmojiSources.txt` "maps the emoji symbols to their original Japanese telco source sets."
So are the camels in `EmojiSources.txt`?
The Bactrian camel at `U+1F42B` appears in the set, but there's no dromedary camel at `U+1F42A`:

> ```
> (format: unicode;DoCoMo;KDDI;SoftBank)
> ...
> 1F429;;F6B8;
> 1F42B;;F3E6;FBD0
> 1F42C;;F3DC;FBC0
> ...
> ```

I didn't see any more documentation in the release that specifically mentioned the camels or why there are two of them, but the release isn't the only documentation online.
In a [Unicode article on emojis](https://www.unicode.org/reports/tr51/#Introduction), we can see a selection of proposals for emojis, including the one from 2000 I mentioned above.
There are two important camel proposals here: in [document L2/09-026R (page 8)](https://www.unicode.org/L2/L2009/09026r-emoji-proposed.pdf), published in 2009, only one camel emoji is present, the dromedary camel.
In [document L2/10-132 (page 45)](https://www.unicode.org/L2/L2010/10132-emojidata.pdf), published in 2010, there's still only one camel, but this time it's the Bactrian camel!

{{< figure
  src="proposed-camels.png"
  label="proposed-camels"
  caption=`The two proposed camels: the first on top, the second below. The second camel is assigned the codepoint it has today.`
  ind="⊕"
  alt="Two proposed camel emojis"
>}}

In the 2010 document, we can also see the corresponding KDDI and SoftBank icons which clearly depict the Bactrian camel.

{{< figure
  src="kddi-softbank-camels.png"
  label="old-camels"
  caption=`Original KDDI camel (left) and SoftBank camel (right). らくだ, romanized as "rakuda", of course means "camel" in Japanese. I've also included non-squished versions of both icons (sources: [KDDI](http://emoji.digital/kddi-au/), [SoftBank](https://emojipedia.org/softbank/2006/two-hump-camel)).`
  ind="⊕"
  alt="Two older camel symbols"
>}}

{{< figure
  src="camel-art.jpg"
  type="margin"
  label="camel-art"
  caption=`I really enjoy this 19th-century Japanese art from [The Met](https://www.metmuseum.org/art/collection/search/77012) of (dromedary) camels being brought to Japan by the Dutch.`
  ind="⊕"
  alt="Japanese art depicting two camels and their Dutch owners"
>}}
It's interesting that the KDDI and SoftBank camels are Bactrian camels.
When I hear "camel," I think of one-humped dromedary camels trekking through desert sand dunes.
I'm not surprised that the "default" camel is different in Japan, though.
The Bactrian camel is native to the steppes of central Asia, which is closer to Japan than the current range of the dromedary in northern Africa and the Arabian Peninsula.
The Bactrian camel was also an important animal used for [transporting goods on the Silk Road](https://depts.washington.edu/silkroad/culture/animals/animals.html), especially in eastern Asia, which could've had a cultural impact on which camel people are more familiar with in Japan.

So now it's pretty clear why the Bactrian emoji is in our set, but still nothing on the dromedary, which was ostensibly removed between 2009 and 2010.
Fortunately, there are even more public emoji documents --- Unicode has maintained a [registry](https://www.unicode.org/L2/) of documents like proposals and reviews, sorted by year, since 1990.
Unfortunately, even though I'm super curious to see the first Unicode document, the earliest documents have been made member-only at the owners' request.
<!-- {{< marginnote >}}
If any Unicode members are reading this, please send me a copy of X3L2/90-1, I won't tell anyone!
{{< /marginnote >}} -->

I looked through every proposal with a title containing "emoji" published in 2009 and 2010, but only found a couple camel-related documents.
In a [review](https://www.unicode.org/L2/L2009/09272-emoji-review-of-pdam8.pdf) of one of the previous emoji proposals, someone noticed the camel mismatch:

> **Mistake in U+1F420 CAMEL**
>
> The glyph for proposed symbol U+1F420 (e-1D6) CAMEL shows a one-hump camel (that is, a
dromedary camel). However, it represents KDDI #723 "two-hump camel" and Softbank #119 "camel"
which both have images of a two-hump camel (that is, a Bactrian camel).
>
> We recommend a US ballot comment to change the glyph to show a two-hump (Bactrian) camel.

This is obviously the reason the camel emoji changed between the 2009 and 2010 proposals above, but still gives us nothing about why we ended up with _two_ camels!

The only other document I found is [this one](https://www.unicode.org/L2/L2009/09114-n3607-emoji.pdf),
{{< marginnote >}}
This document mentions that there have been "many critics" of the proposed addition of emojis to Unicode "due to the somewhat whimsical nature of a subset of the characters being proposed."
{{< /marginnote >}}
which proposes a number of character modifications and additions, including to the animal inventory.
Additions include the deer, moose, and Bactrian camel (this document was published before the correction I mentioned above).
This is the only document I could find with both camels.
They offer a rationale for some additions, but nothing about the two camels!
Maybe they also noticed the KDDI and SoftBank Bactrian camels, but didn't want to erase the proposed dromedary camel and ended up just adding both.

None of these documents mention why both camels ended up in the final version of Unicode 6.0.
Even the last one was seemingly erased in the later 2010 document that only includes the Bactrian camel!
The dromedary camel addition could just be a mistake, but I think that's unlikely.
This documentation is meticulous --- people are quibbling over the [orientation of the bookmark emoji](https://www.unicode.org/L2/L2009/09272-emoji-review-of-pdam8.pdf), there wouldn't be two camels if someone didn't intend there to be.

I think there are two most likely explanations: the first is a possible reluctance to remove the dromedary camel proposed in 2009 combined with a convenient codepoint gap: `U+1F42A`, the current dromedary camel codepoint, is unassigned in the [2010 document](https://www.unicode.org/L2/L2010/10132-emojidata.pdf) that only has the Bactrian camel.


Another possibility is that the authors of the 2010 document did intend to take the earlier document with both camels into account, but the dromedary camel was left out by accident.
I don't see any other single-codepoint gaps, so maybe that's more likely than an unassigned codepoint remaining at that point.
On the other hand, the Unicode 6.0 standard doesn't include any of their other animal additions, and it'd be weird to only include the redundant camel.

Or maybe it _was_ just an oversight, and nobody wanted two camels.
It's kind of disappointing not to have found a definitive answer (or a document where people fought over which camel to add), but it was fun to read a bunch of old Unicode documents.
{{< marginnote >}}
Probably the first time anyone's called Unicode documents "fun."
{{< /marginnote >}}
And I still think that if we can have two camel emojis, we can justify a single opposum emoji!
