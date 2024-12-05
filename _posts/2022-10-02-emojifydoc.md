---
layout: post
title: EmojifyDoc
subtitle: a HackMIT 2022 project
thumbnail-img: /assets/img/emoji.png
mathjax: true
---

[EmojifyDoc](https://github.com/stebvkim/EmojifyDoc) was a project some friends and I submitted for HackMIT 2022.

## Introduction

It was our first ever hackathon, so we wanted to do something light and fun, but also something with actual technical merit. After wasting hours in a classroom brainstorming ideas that led to nowhere, I came up with the following idea: **what if we took an input document, used OCR to obtain the words + their bounding boxes, and replaced them with emojis?** This was within our technical expertise -- several of us were in the CSAIL Document Processing Lab together, where we'd used OCR for some of our projects.

## Methodology

The actual process was simple:

1. We used **pdf2image** to split the input PDF into individual JPG images. Thank goodness for Python having a package for everything.

2. We then ran **pytesseract** (OCR) on each image to get its words along with their bounding boxes. This isn't the best OCR out there, but it's free and does well on documents that are purely digital (e.g. no imperfections from scanning) and require no preprocessing.

3. For each word, if an appropriate emoji could be found, we "whited out" the area defined by the word's bounding boxes by pasting a white rectangle over it. Afterwards, we simply placed the emoji in the center of the whited-out area.

#### What defines an "appropriate" emoji?

In the process of finding a relevant emoji, we first tried the **emoji-translate** package to see if a word already had a matching emoji (thank goodness for Python packages once again). If not, we checked a dictionary of pre-determined pairings that we curated by hand (e.g. the word "A/a" always being mapped to 🅰️).

Just to spice things up and throw some AI / ML in there (️‍🔥️‍🔥️‍🔥), if no emoji was found, we got the GloVe embedding for the word, found its top 10 neighbors by Euclidean distance, and tried using the **emoji-translate** package on those words as well. This resulted in some mistakes (nearby vectors doesn't always imply identical or similar meaning), but it made a LOT more words have a match, which made the output look more interesting.

## Sample Output

Here is a sample input:

![input](/assets/img/emojify_input.jpg){: .mx-auto.d-block :}

and its output after being emojified:

![output](/assets/img/emojify_output.jpg){: .mx-auto.d-block :}

## Final Thoughts

I originally wanted to create a lightweight web application using Flask, but we ran out of time. Also, no one woke up in time to present the project, so we never actually got to compete for prizes. We did get plenty of likes on the internal hackathon page with every group's project displayed though, so that's a win. 🤷
