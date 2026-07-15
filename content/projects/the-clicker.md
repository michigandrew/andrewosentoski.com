---
title: "The Clicker"
date: 2026-07-14
draft: false
summary: "Skip or mute the commercials in streaming sporting events"
link: "https://github.com/michigandrew/the-clicker"
---

TL;DR - I hate ads and
[built a thing](https://github.com/michigandrew/the-clicker) to make them suck
less in sports broadcasts.

I am, unfortunately, a big college football fan. Not even just my team (Go
Blue!), but like, the whole sport. In other words,
[I'm a college football sicko](https://247sports.com/article/college-football-sickos-committee-175054533/).
The biggest downside to this lifestyle is that I have to put up with a deluge of
ads every Saturday. I've found it especially vexing now that it seems like half
the ads are trying to get me to gamble on the games.

In light of this I started recording games via YouTube TV and sitting down to
watch them about an hour and a half after kickoff. This allows me to skip
through commercials and halftime and catch up to the live broadcast somewhere in
the fourth quarter. I'd always wondered whether it would be possible to build a
system that can do this for me automatically, and it turned out it was!

With the help of Claude I put together a system that allows me to automatically
skip ahead when a commercial or halftime is detected. The basic setup is an
Apple TV with an HDMI splitter - one split goes to the TV like normal, the other
runs to a capture card connected to a little linux box. I build a little profile
for the game by selecting the logo in a sample frame, and building a color
histogram based on ~30s of gameplay. The box checks frames against this profile,
and if it's too dissimilar, it sends the "skip" signal to the Apple TV via
[pyatv](https://github.com/postlund/pyatv). There's a little more to it than
that (debouncing, in/out thresholds, etc), but that's the gist! I've also
included an option to simply mute the TV rather than skip if you're watching the
live broadcast.

The setup is surprisingly effective! Being a data scientist, I of course tried a
few more ML-y solutions, but the simple threshold version is much more intuitive
and tunable. Football season hasn't started yet, so I've only used the system to
watch the NBA playoffs. It worked beautifully! I'm excited to have a slightly
less DraftKings fall.
