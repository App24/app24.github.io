---
name: Wings Bot
tools: [Typescript, Discord.js, MongoDB]
description: A discord bot for a server I take part in.
source_code: https://github.com/App24/Winx-Bot
year_from: 2020
year_to: Present
---

# Wings Bot

---

In early to mid 2020 I started creating Discord bots for fun and experimenting what I could do and could be done through a bot. In mid 2020 I was contacted by a friend that had recently taken over a newly made server for a TV show and they wanted a bot that had XP leveling system that also implemented ranks depending on a person's level.

Throughout the years it has seen many rewrites and improvements and new features. First starting as a very simple bot with few scripts and written in Javascript, as I kept both learning Javascript and Discord.js, it kept expanding and the technical debt caught up to me. Once I learnt the existance of Typescript, I knew that it would be a total game changer for the bot and gave me an opportunity to rewrite the bot and give it much more improvements.

The bot started out storing all its data in a MySQL database stored locally, as I did not know anything about hosting databases online and how to connect to them. I later found out about MongoDB and how it has a free tier and decided to switch to it, as it would allow me to access the database without the need to SSH into my laptop.

Features:
- XP Leveling System
- Custom card creation
- Rank based leveling