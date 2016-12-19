---
layout: post
title: "EnergyPlus: epw Weather File Format"
date: 2016-12-18
---

From EnergyPlus Version 8.6 Documentation.  Auxiliary Programs.  September 30, 2016

COPYRIGHT (c) 1996-2016 THE BOARD OF TRUSTEES OF THE UNIVERSITY OF ILLINOIS AND THE REGENTS OF THE UNIVERSITY OF CALIFORNIA THROUGH THE ERNEST ORLANDO LAWRENCE BERKELEY NATIONAL LABORATORY. ALL RIGHTS RESERVED. NO PART OF THIS MATERIAL MAY BE REPRODUCED OR TRANSMITTED IN ANY FORM OR BY ANY MEANS WITHOUT THE PRIOR WRITTEN PERMISSION OF THE UNIVERSITY OF ILLINOIS OR THE ERNEST ORLANDO LAWRENCE BERKELEY NATIONAL LABORATORY. ENERGYPLUS IS A TRADEMARK OF THE US DEPARTMENT OF ENERGY.

## 2.9.1 Data Field Descriptions

Descriptions of the fields are taken from the IWEC manual - as descriptive of what should be contained in the data fields.

### 2.9.1.1 Field: Year

This is the Year of the data. Not really used in EnergyPlus. Used in the Weather Converter program for display in audit file.

### 2.9.1.2 Field: Month

This is the month (1-12) for the data. Cannot be missing.

### 2.9.1.3 Field: Day

This is the day (dependent on month) for the data. Cannot be missing.

### 2.9.1.4 Field: Hour

This is the hour of the data. (1 - 24). Hour 1 is 00:01 to 01:00. Cannot be missing.

### 2.9.1.5 Field: Minute

This is the minute field. (1..60)

### 2.9.1.6 Field: Data Source and Uncertainty Flags

The data source and uncertainty flags from various formats (usually shown with each field) are consolidated in the E/E+ EPW format. More is shown about Data Source and Uncertainty in Data Sources/Uncertainty section later in this document.

### 2.9.1.7 Field: Dry Bulb Temperature

This is the dry bulb temperature in C at the time indicated. Note that this is a full numeric field (i.e. 23.6) and not an integer representation with tenths. Valid values range from -70°C to 70°C. Missing value for this field is 99.9.

### 2.9.1.8 Field: Dew Point Temperature

This is the dew point temperature in C at the time indicated. Note that this is a full numeric field (i.e. 23.6) and not an integer representation with tenths. Valid values range from -70°C to 70°C. Missing value for this field is 99.9.

### 2.9.1.9 Field: Relative Humidity

This is the Relative Humidity in percent at the time indicated. Valid values range from 0% to 110%. Missing value for this field is 999.

### 2.9.1.10 Field: Atmospheric Station Pressure

This is the station pressure in Pa at the time indicated. Valid values range from 31,000 to 120,000. (These values were chosen from the standard barometric pressure for all elevations of the World). Missing value for this field is 999999.

### 2.9.1.11 Field: Extraterrestrial Horizontal Radiation

This is the Extraterrestrial Horizontal Radiation in Wh/m2. __It is not currently used in EnergyPlus calculations__. It should have a minimum value of 0; missing value for this field is 9999.

### 2.9.1.12 Field: Extraterrestrial Direct Normal Radiation

This is the Extraterrestrial Direct Normal Radiation in Wh/m2. (Amount of solar radiation in Wh/m2 received on a surface normal to the rays of the sun at the top of the atmosphere during the number of minutes preceding the time indicated). __It is not currently used in EnergyPlus calculations__. It should have a minimum value of 0; missing value for this field is 9999.

### 2.9.1.13 Field: Horizontal Infrared Radiation Intensity

This is the Horizontal Infrared Radiation Intensity in Wh/m2. If it is missing, it is calculated from the Opaque Sky Cover field as shown in the following explanation. It should have a minimum value of 0; missing value for this field is 9999.

{Equation omitted}

Example: Clear sky (N = 0 ), T drybulb = 273 + 20 = 293K , T dewpoint = 273 + 10 = 283K

ϵ = 0.787 + 0.764 * 0.036 = 0.815

Horizontal IR = {Equation omitted} = 340.6W/m 2

References (Walton, 1983) (Clark, Allen, 1978) for these calculations are contained in the references section at the end of this list of fields.

### 2.9.1.14 Field: Global Horizontal Radiation

This is the Global Horizontal Radiation in Wh/m2. (Total amount of direct and diffuse solar radiation in Wh/m2 received on a horizontal surface during the number of minutes preceding the time indicated.) __It is not currently used in EnergyPlus calculations__. It should have a minimum value of 0; missing value for this field is 9999.

### 2.9.1.15 Field: Direct Normal Radiation

This is the Direct Normal Radiation in Wh/m2. (Amount of solar radiation in Wh/m2 received directly from the solar disk on a surface perpendicular to the sun’s rays, during the number of minutes preceding the time indicated.) If the field is missing (≥ 9999 ) or invalid (< 0 ), it is set to 0. Counts of such missing values are totaled and presented at the end of the runperiod.

### 2.9.1.16 Field: Diffuse Horizontal Radiation

This is the Diffuse Horizontal Radiation in Wh/m2. (Amount of solar radiation in Wh/m2 received from the sky (excluding the solar disk) on a horizontal surface during the number of minutes preceding the time indicated.) If the field is missing (≥ 9999 ) or invalid (< 0 ), it is set to 0. Counts of such missing values are totaled and presented at the end of the runperiod.

### 2.9.1.17 Field: Global Horizontal Illuminance

This is the Global Horizontal Illuminance in lux. (Average total amount of direct and diffuse illuminance in hundreds of lux received on a horizontal surface during the number of minutes preceding the time indicated.) __It is not currently used in EnergyPlus calculations__. It should have a minimum value of 0; missing value for this field is 999999 and will be considered missing if greater than or equal to 999900.

### 2.9.1.18 Field: Direct Normal Illuminance

This is the Direct Normal Illuminance in lux. (Average amount of illuminance in hundreds of lux received directly from the solar disk on a surface perpendicular to the sun’s rays, during the number of minutes preceding the time indicated.) __It is not currently used in EnergyPlus calculations__. It should have a minimum value of 0; missing value for this field is 999999 and will be considered missing if greater than or equal to 999900.

### 2.9.1.19 Field: Diffuse Horizontal Illuminance

This is the Diffuse Horizontal Illuminance in lux. (Average amount of illuminance in hundreds of lux received from the sky (excluding the solar disk) on a horizontal surface during the number of minutes preceding the time indicated.) __It is not currently used in EnergyPlus calculations__. It should have a minimum value of 0; missing value for this field is 999999 and will be considered missing if greater than or equal to 999900.

### 2.9.1.20 Field: Zenith Luminance

This is the Zenith Illuminance in Cd/m2. (Average amount of luminance at the sky’s zenith in tens of Cd/m2 during the number of minutes preceding the time indicated.) __It is not currently used in EnergyPlus calculations__. It should have a minimum value of 0; missing value for this field is 9999.

### 2.9.1.21 Field: Wind Direction

This is the Wind Direction in degrees where the convention is that North = 0.0, East = 90.0, South = 180.0, West = 270.0. (Wind direction in degrees at the time indicated. If calm, direction equals zero.) Values can range from 0 to 360. Missing value is 999.

### 2.9.1.22 Field: Wind Speed

This is the wind speed in m/sec. (Wind speed at time indicated.) Values can range from 0 to 40. Missing value is 999.

### 2.9.1.23 Field: Total Sky Cover

This is the value for total sky cover (tenths of coverage). (i.e. 1 is 1/10 covered. 10 is total coverage). (Amount of sky dome in tenths covered by clouds or obscuring phenomena at the hour indicated at the time indicated.) Minimum value is 0; maximum value is 10; missing value is 99.

### 2.9.1.24 Field: Opaque Sky Cover

This is the value for opaque sky cover (tenths of coverage). (i.e. 1 is 1/10 covered. 10 is total coverage). (Amount of sky dome in tenths covered by clouds or obscuring phenomena that prevent observing the sky or higher cloud layers at the time indicated.) This is not used unless the field for Horizontal Infrared Radiation Intensity is missing and then it is used to calculate Horizontal Infrared Radiation Intensity. Minimum value is 0; maximum value is 10; missing value is 99.

### 2.9.1.25 Field: Visibility

This is the value for visibility in km. (Horizontal visibility at the time indicated.) __It is not currently used in EnergyPlus calculations__. Missing value is 9999.

###2.9.1.26 Field: Ceiling Height

This is the value for ceiling height in m. (77777 is unlimited ceiling height. 88888 is cirroform ceiling.) __It is not currently used in EnergyPlus calculations__. Missing value is 99999.

### 2.9.1.27 Field: Present Weather Observation

If the value of the field is 0, then the observed weather codes are taken from the following field. If the value of the field is 9, then “missing” weather is assumed. Since the primary use of these fields (Present Weather Observation and Present Weather Codes) is for rain/wet surfaces, a missing observation field or a missing weather code implies no rain.

### Table 2.15: Present Weather Observation Values

Element | Values | Definition Observation Indicator | 0 or 9 | 0 = Weather observation made; 9 = Weather observation not made, or missing

### 2.9.1.28 Field: Present Weather Codes

The present weather codes field is assumed to follow the TMY2 conventions for this field. Note that though this field may be represented as numeric (e.g. in the CSV format), it is really a text field of 9 single digits. This convention along with values for each “column” (left to right) is presented in Table 2.16. Note that some formats (e.g. TMY) does not follow this convention - as much as possible, the present weather codes are converted to this convention during WeatherConverter processing. Also note that the most important fields are those representing liquid precipitation - where the surfaces of the building would be wet. EnergyPlus uses “Snow Depth” to determine if snow is on the ground.

### Table 2.16: Weather Codes Field Interpretation

Column - Position in Field | Element Description | Possible Values | Definition
1 | Occurrence of Thunderstorm, Tornado, or Squall | 0 - 2, 4, 6- 9 | 0 = Thunderstorm - lightning and thunder. Wind gusts less than 25.7 m/s, and hail, if any, less than 1.9 cm diameter. 1 = Heavy or severe thunderstorm - frequent intense lightning and thunder. Wind gusts greater than 25.7 m/s and hail, if any, 1.9 cm or greater diameter. 2 = Report of tornado or waterspout. 4 = Moderate squall - sudden increase of windspeed by at least 8.2 m/s, reaching 11.3 m/s or more and lasting for at least 1 minute.  6 = Water spout (beginning January 1984). 7 = Funnel cloud (beginning January 1984). 8 = Tornado (beginning January .1984) 9 = None if Observation Indicator element equals 0, or else unknown or missing if Observation Indicator element equals 9.
2 | Occurrence of Rain, Rain Showers, or Freezing Rain | 0 - 9 | 0 = Light rain.  1 = Moderate rain.  2 = Heavy rain. 3 = Light rain showers. 4 = Moderate rain showers.  5 = Heavy rain showers.  6 = Light freezing rain.  7 = Moderate freezing rain.  8 = Heavy freezing rain.  9 = None if Observation Indicator element equals 0, or else unknown or missing if Observation Indicator element equals 9.  Notes:  Light = up to 0.25 cm per hour, Moderate = 0.28 to 0.76 cm per hour, Heavy = greater than 0.76 cm per hour
3 | Occurrence of Rain Squalls, Drizzle, or Freezing Drizzle | 0, 1, 3-9 | 0 = Light rain squalls.  1 = Moderate rain squalls.  3 = Light drizzle.  4 = Moderate drizzle.  5 = Heavy drizzle.  6 = Light freezing drizzle.  7 = Moderate freezing drizzle.  8 = Heavy freezing drizzle.  9 = None if Observation Indicator element equals 0, or else unknown or missing if Observation Indicator element equals 9.  Notes: When drizzle or freezing drizzle occurs with other weather phenomena: Light = up to 0.025 cm per hour, Moderate = 0.025 to 0.051 cm per hour, Heavy = greater than 0.051 cm per hour.  When drizzle or freezing drizzle occurs alone: Light = visibility 1 km or greater, Moderate = visibility between 0.5 and 1 km, Heavy = visibility 0.5 km or less.
4 | Occurrence of Snow, Snow Pellets, or Ice-Crystals | 0 - 9 | 0 = Light snow.  1 = Moderate snow.  2 = Heavy snow.  3 = Light snow pellets.  4 = Moderate snow pellets.  5 = Heavy snow pellets.  6 = Light ice crystals.  7 = Moderate ice crystals.  8 = Heavy ice crystals.  9 = None if Observation Indicator element equals 0, or else unknown or missing if Observation Indicator element equals 9.   Notes:Beginning in April 1963, any occurrence of ice-crystals is recorded as a 7.
5 | Occurrence of Snow Showers, Snow Squalls, or Snow Grains | 0 - 7, 9 | 0 = Light snow. 1 = Moderate snow showers. 2 = Heavy snow showers.  3 = Light snow squall.  4 = Moderate snow squall.  5 = Heavy snow squall.  6 = Light snow grains.  7 = Moderate snow grains.  9 = None if Observation Indicator element equals 0, or else unknown or missing if Observation Indicator element equals 9.
6 | Occurrence of Sleet, Sleet Showers, or Hail | 0 - 2, 4, 9 | 0 = Light ice pellet showers.  1 = Moderate ice pellet showers. 2 = Heavy ice pellet showers.  4 = Hail. 9 = None if Observation Indicator element equals 0, or else unknown or missing if Observation Indicator element equals 9.  Notes: Prior to April 1970, ice pellets were coded as sleet.  Beginning in April 1970, sleet and small hail were redefined as ice pellets and are coded as 0, 1, or 2.
7 | Occurrence of Fog, Blowing Dust, or Blowing Sand | 0 - 9 | 0 = Fog.  1 = Ice fog.  2 = Ground fog.  3 = Blowing dust.  4 = Blowing sand.  5 = Heavy fog.  6 = Glaze (beginning 1984).  7 = Heavy ice fog (beginning 1984).  8 = Heavy ground fog (beginning 1984).  9 = None if  Observation Indicator element equals 0, or else unknown or missing if Observation Indicator element equals 9.  Notes:These values recorded only when visibility is less than 11 km.
8 | Occurrence of Smoke, Haze, Smoke and Haze, BlowingSnow, BlowingSpray, or Dust | 0 - 7, 9 | 0 = Smoke.  1 = Haze. 2 = Smoke and haze. 3 = Dust.  4 = Blowing snow. 5 = Blowing spray. 6 = Dust storm (beginning 1984).  7 = Volcanic ash.  9 = None if Observation Indicator element equals 0, or else unknown or missing if Observation Indicator element equals 9.  Notes: These values recorded only when visibility is less than 11 km.
9 | Occurrence of Ice Pellets | 0 - 2, 9 | 0 = Light ice pellets. 1 = Moderate ice pellets. 2 = Heavy ice pellets. 9 = None if Observation Indicator element equals 0, or else unknown or missing if Observation Indicator element equals 9.

For example, a Present Weather Observation (previous field) of 0 and a Present Weather Codes field of 929999999 notes that there is heavy rain for this data period (usually hourly but depends on the number of intervals per hour field in the “Data Periods” record).

### 2.9.1.29 Field: Precipitable Water

This is the value for Precipitable Water in mm. (This is not rain - rain is inferred from the PresWeathObs field but a better result is from the Liquid Precipitation Depth field)). It is not currently used in EnergyPlus calculations (primarily due to the unreliability of the reporting of this value). Missing value is 999.

### 2.9.1.30 Field: Aerosol Optical Depth

This is the value for Aerosol Optical Depth in thousandths. __It is not currently used in EnergyPlus calculations__. Missing value is .999.

### 2.9.1.31 Field: Snow Depth

This is the value for Snow Depth in cm. This field is used to tell when snow is on the ground and, thus, the ground reflectance may change. Missing value is 999.

### 2.9.1.32 Field: Days Since Last Snowfall

This is the value for Days Since Last Snowfall. __It is not currently used in EnergyPlus calculations__. Missing value is 99.

### 2.9.1.33 Field: Albedo

The ratio (unitless) of reflected solar irradiance to global horizontal irradiance. __It is not currently used in EnergyPlus__.

### 2.9.1.34 Field: Liquid Precipitation Depth

The amount of liquid precipitation (mm) observed at the indicated time for the period indicated in the liquid precipitation quantity field. If this value is not missing, then it is used and overrides the “precipitation” flag as rainfall. Conversely, if the precipitation flag shows rain and this field is missing or zero, it is set to 1.5 (mm).

### 2.9.1.35 Field: Liquid Precipitation Quantity

The period of accumulation (hr) for the liquid precipitation depth field. __It is not currently used in EnergyPlus__.

## 2.9.2 References

Walton, G. N. 1983. Thermal Analysis Research Program Reference Manual. NBSSIR 83-2655. National Bureau of Standards, p. 21.

Clark, G. and C. Allen, “The Estimation of Atmospheric Radiation for Clear and Cloudy Skies,” Proceedings 2nd National Passive Solar Conference (AS/ISES), 1978, pp. 675-678.