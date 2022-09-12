---
id: il0d3buqdbkcmgbgfovas0p
title: Desired Functionalities
desc: ''
updated: 1662394741122
created: 1662229443237
---
The [[projects.ndbc-reader]] software package has only a few operations, currently.  These mostly focus on retrieving and persisting data.  TThe other Functionalities are allowing access to the data stored during runtime and keeping track of data fetching operations performed and their outcome.

I am documenting these Functionalities at a high level to help me plan and design the package in a more easily maintained, more highly abstracted manner.

## Data Fetching
The primary purpose of the NDBC Data Buoy class is to simplify the fetching of monthly/annual summary data from the NDBC public websites.  These are exposed as simple `.txt` files hosted on an individual station's web page.  While there are other data archive formats and servers, I find this approach to be refreshingly direct and am sticking with it for now.

A secondary data fetching action is to parse the data station web page and collect station metadata (instrumentation, location, etc.). 

Both data fetching operations need to dynamically build the URLs fetched based on parameters specified at runtime.  They also need to track a failure to retrieve the data requested.  These features could be abstracted into a custom HTTP Client class.

The assignment of the returned data to the correct properties on the Data Buoy class could also be abstracted to a method designed for that purpose.

## Data Persistence
This is the storing of the data that comprises the state of an instance of the Data Buoy class.  Ideally researchers should be able to use this package to retrieve data and then store it in a manner they find convenient so it can be analyzed later without requiring an internet connection.

Presently the only approach to data persistence/loading is writing to / reading from `.json` files.  I think it would make sense to abstract general data persistence to it's own class and work to add multiple methods including allowing users to specify database connection parameters and store individual Data Buoy data to either SQL or NoSQL databases.

## Data Storage/Access
The NDBC `DataBuoy` class is operates as a data storage and access API during runtime after data has been retrieved from NDBC servers.  Keeping this data organized in a way that makes sense is something that desrves serious consideration.  

### Data Types:
* **Station Metadata:** This represents information about the intrument platform itself.  While often not the subject of analyses, this information can be necessary to various research operations such as placing the station in a geographic coordinate plane, transforming wind speed and direction into wind stress, and making valid comparisons between instrument platforms.
    * This is stored in a `station_info` property of the class

* **Summary Data:** This data represents monthly/annual summary data for one of the supported data packages.  This is the primary data used for analyses.  The class must support incremental addition to this data while still providing access to the entire amount in a single interface.  An example of this is as follows:

A user instantiates a buoy class and retrieves the last 3 full months of data.  The user can examine any measurement for the entire timespan covered in a single columnar vector.  If the user then wants to add the previous 12 months they should be able to do so while still being able to examine the full 15 months of data as a single data property.  Maintaining clear and consistent access to this data is crucial to the utility of this package.

* **Realtime Data:** This is the most recent, non-summarized data collected by the platform.  While the measurements are the same as the Summary Data, this data has not gone through NDBC QA/QC processes and should be kept separate from summary data and clearly labeled.
