---
layout: post
title: "EnergyPlus: Results: House Load (Autosizing On) vs. TMY"
date: 2016-12-28
---

## Test house

The house selected is the residential single-family house-on-slab, gas furnace and other appliances, IECC 2006.  This first run is with autosizing on and Boston TMY data.  Below, the results are summarized by gas day (10am - 10am).

## Daily house gas requirements vs. HDD

Hourly gas usage is summed to the gas day.  Daily HDDs are calculated as the mean of the hourly HDD values, rounded to zero decimal places.  The load fits a degree-2 polynomial nicely.

![Autosized house load vs TMY HDD](images/2016-12-28-1-House-vs-HDD.JPG)

## Daily house gas requirements vs. EDD

Hourly gas usage is summed to the gas day.  Daily EDDs are calculated as the mean of the hourly EDD values, rounded to zero decimal places.  Since EDD incorporates wind speed, it provides a slightly better fit.  Again, the load fits a degree-2 polynomial nicely with a slight improvement in the r-squared.

![Autosized house load vs TMY EDD](images/2016-12-28-2-House-vs-EDD.JPG)

The design day, which fell nicely on the curve of load vs. HDD suddenly deviates from the curve.

## HDD vs. EDD

The load deviation is driven by the deviation of the peak day EDD from the EDD-to-HDD line.

![Boston TMY HDD vs EDD](images/2016-12-28-3-HDD-vs-EDD.JPG)
