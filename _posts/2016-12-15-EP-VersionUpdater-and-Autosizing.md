---
layout: post
title: "EnergyPlus: Version Updater and Autosizing"
date: 2016-12-15
---

## Version Updater

For my project, I'm using [residential prototype building models](https://www.energycodes.gov/development/residential/iecc_models) prepared by the Pacific Northwest National Laboratory (PNNL).  Reviewing the .idf files, they are listed as version 5.  Beginning with v8.4.0 Update 1, the EnergyPlus installers include all transition programs from v7.2.0 to current.  To run under the current (8.6.0) version of EnergyPlus, I found that Michael Witte had posted a [version updater](http://energyplus.helpserve.com/knowledgebase/article/View/86/46/windows---programs-for-converting-older-pre-v720-idf-files-to-current-or-intermediate-versions) which runs on Windows and it contains transition programs from v1.0 to v8.3.0.  The transition from 8.3 to 8.6 can be handled by the installed Version Updater that comes with EnergyPlus.

## Autosizing

The PNNL models are used with TMY .epw files and, in my work, I'm going to be running various weather scenarios.  The PNNL models autosize:

* Sizing:System
* AirLoopHVAC
* AirLoopHVAC:UnitaryHeatCool
* Coil:Heating:Fuel
* Coil:Cooling:DX:SingleSpeed
* Fan:OnOff
* Pump:VariableSpeed
* WaterHeater:Mixed
* PlantLoop

Since I want to fix the HVAC system for the various weather scenarios, I ran the .idf file using the TMY .epw file under autosize.  Here's where I learned that the .eio file can be your friend.  The .eio file listed all of the System and Component Sizing values developed under the initial run.  Text-editing the original .idf file, one can replace each occurrence of 'autosize' with the values found in the original .eio file.  Then, in SimulationControl, turning off:

* Zone Sizing Calculation
* System Sizing Calculation
* Plant Sizing Calculation
* Run Simulation for Sizing Periods

and running the modified .idf file against the original .epw file, one sees only an insignificant difference in heating fuel consumption presumably driven by truncated differences in the .eio file values.


