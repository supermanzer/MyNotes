The [[projects.ndbc-reader]] software package has only a few operations, currently.  These mostly focus on retrieving and persisting data.  TThe other Functionalities are allowing access to the data stored during runtime and keeping track of data fetching operations performed and their outcome.

I am documenting these Functionalities at a high level to help me plan and design the package in a more easily maintained, more highly abstracted manner.

## Data Fetching
The primary purpose of the NDBC Data Buoy class is to simplify the fetching of monthly/annual summary data from the NDBC public websites.  These are exposed as simple `.txt` files hosted on an individual station's web page.  While there are other data archive formats and servers, I find this approach to be refreshingly direct and am sticking with it for now.

A secondary data fetching action is to parse the data station web page and collect station metadata (instrumentation, location, etc.). 

Both data fetching operations need to dynamically build the URLs fetched based on parameters specified at runtime.  They also need to track a failure to retrieve the data requested.  These features could be abstracted into a custom HTTP Client class.

The assignment of the returned data to the correct properties on the Data Buoy class could also be abstracted to a method designed for that purpose.

## Data Persistence
This is the storing of the data that comprises the state of an instance of the Data Buoy class.  Ideally researchers should be able to use this package to retrieve data and then store it in a manner they find convenient so it can be analyzed later without requiring an internet connection.

Presntly the only approach to data persistence/loading is writing to / reading from `.json` files.  I think it would make sense to abstract general data persistence to it's own class and work to add multiple methods including allowing users to specify database connection parameters and store individual Data Buoy data to either SQL or NoSQL databases.

## Data Storage/Access
