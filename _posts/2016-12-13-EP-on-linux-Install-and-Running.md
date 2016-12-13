---
layout: post
title: "EnergyPlus: Installation and Running on Linux"
date: 2016-12-13
---
EnergyPlus [Linux installation instructions](https://energyplus.net/installation-linux) are available on energyplus.net.  No issues there.  The current version is 8.6.0 and it is no longer password protected.

Running EnergyPlus on Linux is a pill.  Once your models get into using the preprocessors or you'd like to use the postprocessor for the output data, you have to learn that the 'runenergyplus' shell script is your friend.  I had read that it was deprecated.  While this may be true on Windows (since you use EPLaunch there), it is still __the__ way to run EnergyPlus on Linux.

