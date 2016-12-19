---
layout: post
title: "EnergyPlus: Weather Data"
date: 2016-12-19
---

## Weather data in EnergyPlus

While holding weather constant using TMY data and varying the building design can be interesting, the fun comes when you hold the building static (at least at first), and test the variations in performance against real weather data.  Two sources of hourly weather data are [satellite-based data](weatheranalytics.com) and [ground-based](http://gis.ncdc.noaa.gov/all-records/catalog/search/resource/details.page?id=gov.noaa.ncdc:C00532).

The EnergyPlus epw file contains the following fields:

* Dry Bulb Temperature
* Dew Point Temperature
* Relative Humidity
* Atmospheric Station Pressure
* Horizontal Infrared Radiation Intensity
* Direct Normal Radiation
* Diffuse Horizontal Radiation
* Wind Direction
* Wind Speed
* Total Sky Cover
* Opaque Sky Cover
* Present Weather Observation
* Present Weather Codes
* Precipitable Water
* Snow Depth
* Liquid Precipitation Depth

It also contains fields for the following variables, but they are listed in the documentation as 'not currently used in EnergyPlus calculations':

* Extraterrestrial Horizontal Radiation
* Extraterrestrial Direct Normal Radiation
* Global Horizontal Radiation
* Global Horizontal Illuminance
* Direct Normal Illuminance
* Diffuse Horizontal Illuminance
* Zenith Luminance
* Visibility
* Ceiling Height
* Aerosol Optical Depth
* Days Since Last Snowfall
* Albedo
* Liquid Precipitation Quantity

### Satellite-based weather data

Weatheranalytics.com offers, for a nominal fee, actual weather data in both csv and epw format.  The data includes:

* Surface Temperature
* Dew Point Temperature
* Wet Bulb Temperature
* Relative Humidity
* Barometric Pressure
* Wind Speed
* Wind Direction
* Cloud Cover
* Direct Normal Insolation
* Diffuse Horizontal Insolation
* Direct Normal IR Radiation

The historical data is based on the NOAA/NCEP Climate Forecast System Reanalysis (CFSR) model.

The only issue is that a 30-km diameter 'spot' can encompass a fairly diverse range in weather conditions in certain areas.

### Ground-based weather data

The NOAA Integrated Surface Data (ISD) is digital data set DSI-3505, archived at the National Climatic Data Center (NCDC). The ISD database is composed of worldwide surface weather observations from over 20,000 stations, collected and stored from sources such as the Automated Weather Network (AWN), the Global Telecommunications System (GTS), the Automated Surface Observing System (ASOS), and data keyed from paper forms.  Of the The EnergyPlus epw file data requirements, it contains the following fields:

* Dry Bulb Temperature
* Dew Point Temperature
* Atmospheric Station Pressure
* Wind Direction
* Wind Speed
* Total Sky Cover
* Precipitable Water
* Snow Depth

The following additional items could potentially be calculated or inferred:

* Relative Humidity
* Opaque Sky Cover
* Present Weather Observation
* Present Weather Codes
* Liquid Precipitation Depth

This leaves only the three radiation fields missing:

* Horizontal Infrared Radiation Intensity
* Direct Normal Radiation
* Diffuse Horizontal Radiation

