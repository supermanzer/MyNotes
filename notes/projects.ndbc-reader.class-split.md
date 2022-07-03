---
id: b235045c-af65-4673-9aca-c29083c8556c
title: Class Split
desc: >-
  Desribing the concepts and issues around splitting the NDBC Reader into
  multiple classes
updated: 1622504828566
created: 1622482980052
---


The idea to break up the `DataBuoy` class in the `NDBC` package came from a desire to separate the concerns and de-couple the functionality relating to
1. Handle web requests/responses to and from NDBC servers
1. Parse, store, and save station data.

I imagine that there may be usecases where researchers are only interested in a limited subset of the functionality present in the `DataBuoy` class.  In that respect _I hope_ this effort will be more useful that just helping me simplify the process of modifying the existing code base.  However, it has caused me to have to rethink the way the core processes of the `DataBuoy` class due to the way in which NDBC server request functionality is tightly coupled with data parsing and storage.  Let's take a look at the new structure by examing the classes and their functionality

- #### `StationWebManager`: Manages interactions with NDBC web servers.
    - Stores constants related to web requests (e.g. `DATA_PACKAGES`, `STATION_URL`, etc.)
    - Creates station URLs for each month/year requested and checks to see whether they exist on the NDBC server.
    - Fetches/parses station metadata.
    - Performs station search requests
    - Fetches specified data packages for time periods requested

- #### `DataManager`: Handles data parsing, storing, saving, and access.
    - Performs data type asignments
    - Parses date part columns into Python datetime values
    - Checks for NDBC "bad data" flags (all digits set to 9) and replaces bad data with NumPy `NaN` value.
    - Saves parsed data to `data` attribute.

- #### `DB2`: Coordinates Subclass functionality - eventually renamed to `DataBuoy` class once all tests pass.
    - Coordinates the use of `StationWebManager` request/response methods with `DataManager` parsing and storage methods behind a simple interface.
    - Provide simplified data access using `@property` decorated functions.


## Outstanding Questions:

The current implementation allows a user to make a request for a data package without specifying months or years.  In this case the function starts at the current month/year and checks for valid data, stepping back one month for reach failed request until either 
  - A valid monthly summary can be found and returned
  - All months in the current and previous year have been queried.

The revised approach for fetching data (shown below) is designed to make a request for a single time period

![[projects.ndbc-reader.class-split.station-web-manager#fetch_data]]
