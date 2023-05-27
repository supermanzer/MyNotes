---
id: 9rc96ih5efxhs5mitfnwlrl
title: Automated Analysis
desc: 'THis project focuses on automating the collection, visualization, and analysis of oceanographic data'
updated: 1679864809388
created: 1679859726257
---

## Motivation
After a break in early spring storms I noticed a vivid bloom of phytoplankton along the Monterey peninsula coast.  When I first saw it the stratification of the water masses was pretty extreme. I realized that the timing appeared to line up with the delivery of previously upwelled water that I described in my M.Sc. thesis.  This led me to wish I could visualize the timing and geographic spread of this event to see if it really lined up with a relaxation after a fully established upwelling circulation pattern had been established.  Given that almost all the data I used was easily publicly accessible, this is something that _should_ be a candidate for automation.  With that I started thinking how I would go about it.

## Purpose
This project should produce a a codebase that permits the automating the collection, visualization, and analysis of oceanographic data to identify upwelling patterns.  To do this it will examine wind patterns, surface currents, and sa surface temperature in the Nonterey Bay area.  

## Data Sources
* Wind
    * NDBC 46042 (https://www.ndbc.noaa.gov/station_page.php?station=46042)
* Surface Currents (HF Radar) - 2KM resolution
    * NOAA THREDS (https://dods.ndbc.noaa.gov/thredds/hfradar.html?dataset=hfradar_uswc_2km)
* Sea Surface Temperature
    * NDBC 46042 (https://www.ndbc.noaa.gov/station_page.php?station=46042)
    * NDBC 46240 (https://www.ndbc.noaa.gov/station_page.php?station=46240)
    * NASA PODAAC (https://podaac.jpl.nasa.gov/dataaccess)

## Outstanding Questions
* **File format** - The different data sources do not all use consistent formats.  Determining how to access each file type and get the data loaded into memory for analysis is something that will need to be addressed.
* **Graph types** - MatLab (the software used for my thesis analysis) had a lot of built in scientific graphing functionality.  Finding the correct libraries and approaches to building something similar in Python - NO MORE LICENSED SOFTWARE!

## Design Ideas

### API Service
All the data used for this project is accessible via some form of HTTP or FTP request.  Thus it makes sense to design an API service that, based on resource being retrieved, makes the appropriate API request and returns the data.

### Data Service
I'm not sure what the correct design pattern name is here but basically this service should abstract the loading of data into memory based on the file type.  It should expose a single function that returns the data from the API service in a format suitable for analysis and visualization.  The business logic of this service is to handle accessing the file based on the type (e.g. NetCDF, HFD, CSV) as well as retrieving the data of interest.  The level of nesting a metadata will vary between data sources and this should be handled here too.

### Computed Data Service

The purpose of this service is to calculate those vectors that are necessary for the eventual analysis but not directly measured and captured in the data sources themselves.  The clearest example is calculating wind stress from wind speed and direction as well as decomposing wind stress into alongshore and cross-shore vectors.  This service should also handle any transformations necessary so that the data product returned is ready to visualization and analysis.

### Visualization Service

This service does the work of generating all the desired data visualizations. 

### Statistical Service

This should perform all the statistical analyses (e.g. correlation, timing) required to identify whether or not upwelling events and reversals have occurred during the time period of interest.