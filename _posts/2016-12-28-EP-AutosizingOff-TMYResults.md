---
layout: post
title: "EnergyPlus: Results: 2: House Load (Autosizing Off) vs. TMY"
date: 2016-12-28
---

## Test house

The house selected is the residential single-family house-on-slab, gas furnace and other appliances, IECC 2006.  This first run was with autosizing on and Boston TMY data.  In this run, the autosizing results were mannually entered into the building idf file and re-run to validate turning off autosizing.  Below, the results are summarized by gas day (10am - 10am).

## Daily house gas requirements vs. HDD

Hourly gas usage is summed to the gas day.  Daily HDDs are calculated as the mean of the hourly HDD values, rounded to zero decimal places.  The load fits a degree-2 polynomial nicely.  The coefficients are effectively the same as the autosizing run output.

![Non-Autosized house load vs TMY HDD](../../../images/20161228-4-House-vs-HDD.JPG)

## Daily house gas requirements vs. EDD

Hourly gas usage is summed to the gas day.  Daily EDDs are calculated as the mean of the hourly EDD values, rounded to zero decimal places.  Since EDD incorporates wind speed, it provides a slightly better fit.  Again, the load fits a degree-2 polynomial nicely with a slight improvement in the r-squared.  The coefficients are effectively the same as the autosizing run output.

![Non-Autosized house load vs TMY EDD](../../../images/20161228-5-House-vs-EDD.JPG)

The design day, which fell nicely on the curve of load vs. HDD again deviates from the curve.
