_Definitions for the files in the `/src/NDBC` directory comprising the functionality of the NDBC package_

---

* `NDBC.py` - This file contains the highest level class(es) of the package and exposes the API intended for use in retrieving and analyzing NDBC station data.
* `models.py` - This file defines the classes specific to the domain of this software, focused on encapsulating the representation of an NDBC data station.
* `api.py` - This file defines the classes/methods involved with making the HTTP requests to retrieve NDBC data and parsing the responses.
* `repository.py` - This file defines the classes/methods used to save and load the state of a particular instance of an NDBC data station.  It will encapsulate different methods for different approaches to data storage such as text files (`.json`, `.csv`) or SQL/NoSQL DBs.
* `constants.py` - This file defines all the hard-coded constant values used in the NDBC package