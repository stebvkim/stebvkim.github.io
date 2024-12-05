---
layout: post
title: EmojifyDoc
subtitle: a HackMIT 2022 project
thumbnail-img: /assets/img/emoji.png
mathjax: true
---

[EmojifyDoc](https://github.com/stebvkim/EmojifyDoc) is a project some friends and I made for HackMIT 2022.

## Introduction

It was our first ever hackathon, so we wanted to do something light and fun, but also something with actual technical merit. After wasting hours in a classroom brainstorming ideas that led to nowhere, I came up with the following idea: **what if we took an input document, used OCR to obtain the words + their bounding boxes, and replaced them with emojis?** This was within our technical expertise -- several of us were in the CSAIL Document Processing Lab together, where we'd used OCR for some of our projects.

## Methodology

The actual process is simple:

1. We use **pdf2image** to split the input PDF into individual JPG images. Thank goodness for Python having a package for everything.

2. We then run **pytesseract** (OCR) on each image to get words along with their bounding boxes. This isn't the best OCR out there, but it's free and does well on documents that are purely digital (e.g. no imperfections from scanning) and require no preprocessing.

3. For each word, if an appropriate emoji can be found, we "white out" the area defined by the word's bounding boxes by pasting a white rectangle over it. Afterwards, we simply place the emoji in the center of the whited-out area.

#### What defines an "appropriate" emoji?

In the process of finding a relevant emoji, we first try the **emoji-translate** package to see if it already has a matching emoji (thank goodness for Python once again). Then, we check a dictionary of pre-determined pairings that we curated by hand (e.g. the word "A/a" always being mapped to 🅰️).

Just to spice things up and throw some AI / ML in there (️‍🔥️‍🔥️‍🔥), if no emoji is found, we get the GloVe embedding for the word, find its top 10 neighbors by Euclidean distance, and try using the **emoji-translate** package on them as well. This results in some mistakes (nearby vectors doesn't always imply identical or similar meaning), but it makes a LOT more words get converted, which makes the output look nicer.

## Sample Output

Here is a sample input:

![input](/assets/img/emojify_input.jpg){: .mx-auto.d-block :}

and its output after being emojified:

![output](/assets/img/emojify_output.jpg){: .mx-auto.d-block :}

## Final Thoughts

I originally wanted to create a web application using Flask, but we ran out of time. Also, no one woke up in time to present the project, so we never actually got to compete for prizes. We did get plenty of likes on the internal hackathon page with every group's project displayed though, so that's a win. 🤷
