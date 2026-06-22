---
layout: post
title: "TAP corpus: hard annotation cases"
date: 2025-02-18
description: "A walkthrough of borderline annotation decisions in the temporal adverbial phrase corpus — when does a phrase set a frame vs. mark continuity?"
tags: [corpus linguistics, annotation, TAPs]
---

The TAP annotation scheme has five categories: single-word adverbs, temporal conjunctions, durative phrases, frame-setting phrases, and continuity markers. Most tokens are easy. A handful are not.

## Frame-setting vs. continuity

The hardest boundary is between **frame-setting phrases** (FSP) and **continuity markers** (CM). Both appear at clause boundaries. Both modify temporal reference. The difference is whether they introduce a new temporal frame or signal that the current one persists.

Compare:

> *W tamtym roku* pojechałem do Warszawy. — **FSP** (introduces a specific year as the frame)

> *Nadal* mieszkał w Warszawie. — **CM** (signals continuity with a previously established frame)

Clear enough in isolation. But then you get cases like:

> *Przez kolejne trzy lata* kontynuował badania.

Is *przez kolejne trzy lata* a durative phrase (it specifies duration) or a continuity marker (it foregrounds continuation)? I've been coding these as **durative** when the duration is specified and the continuation reading is derivable, and as **CM** only when duration is unspecified and continuation is the primary meaning.

## Single-word adverbs that resist categorisation

*Już* and *jeszcze* are the main trouble spots. Both can function as temporal adverbs, but they also carry aspectual and scalar meanings that don't fit neatly into any TAP category.

For now I'm tagging them as single-word adverbs with a secondary note field, and I'll revisit them at the analysis stage.

## A note on methodology

These decisions are documented in the annotation manual, which I'm keeping as a living document alongside the corpus. If you're working on a similar project and want to compare schemes, I'd be happy to share.
