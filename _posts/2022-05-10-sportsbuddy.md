---
layout: post
title: SportsBuddy [WIP]
subtitle: 6.08 Final Project
thumbnail-img: /assets/img/esp32.jpg
mathjax: true
---

This was my team's final project for 6.08, Embedded Systems, where we created a live sports tracking module on an ESP32.

## Introduction

SportsBuddy is a system for viewing live game scores and finding nearby users to watch a particular sports game with.

As a general overview, users will be given the option to choose from a list of different sports leagues (MLB, NBA, NHL).

After choosing a sports league, the user can manually cycle through all of the ongoing games within that league to check the up-to-date game scores for those games, or filter the results to a list of selected favorite teams.

If the user finds a particular game that they are interested in watching with others, they will have the option to look for people in their geographical vicinity who also want to watch the game with others, and SportsBuddy will match them.

## Methodology

Here is the general structure for SportsBuddy:

![overfit](/assets/img/block_diagram.png){: .mx-auto.d-block :}

And here is the full state diagram:

![overfit](/assets/img/608-state-diagram.png){: .mx-auto.d-block :}

We used the following technologies and hardware:

C (ESP32), Python (server-side code), REST APIs, sqlite, HTML, CSS, buttons, microphone

## TODO

Update with images and videos.
