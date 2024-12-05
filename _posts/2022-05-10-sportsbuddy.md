---
layout: post
title: SportsBuddy [WIP]
subtitle: 6.08 Final Project
thumbnail-img: /assets/img/esp32.jpg
mathjax: true
---

This was my team's final project for 6.08, Embedded Systems, where we created a live sports tracking module on an ESP32 connected to a monitor and other hardware.

## Introduction

SportsBuddy was a system for viewing live game scores and finding nearby users to watch a particular sports game with. Users were given the option to choose from a list of different sports leagues (MLB, NBA, NHL), and upon selecting one, they could manually cycle through all of the ongoing games within that league to check the up-to-date game scores for those games, or filter the results to a list of selected "favorite" teams.

If the user found a particular game that they were interested in watching with others, they had the option to look for people in their geographical vicinity who also wanted to watch the game with others, and SportsBuddy would match them.

## Methodology

Here was the general structure for SportsBuddy:

![overfit](/assets/img/block_diagram.png){: .mx-auto.d-block :}

And the full state diagram for the ESP32:

![overfit](/assets/img/608-state-diagram.png){: .mx-auto.d-block :}

We used the following technologies and hardware:

C (ESP32), Python (server-side code), REST APIs, sqlite3 (database), HTML / CSS (sign-up website), buttons, microphone

## TODO

Will update with images and videos showing how it worked.
