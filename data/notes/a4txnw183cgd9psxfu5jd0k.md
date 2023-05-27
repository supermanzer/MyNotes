_Applying the domain model to the NDBC Python package_

---

> The _domain_ is a fancy way of saying _the problem you're trying to solve_


This chapter focuses on naming classes and methods in a manner that utilizes "business jargon" both to help the software components map to user needs as well as make deciding where to add functionality clear.

This is already partly implemented in the naming of the main class (`DataBuoy`) and the exposed method names.  This chapter also includes examples of building tests of increasing complexity to reflect the required functionalities of the software.  However, let's try to be a bit more rigorous about defining the responsibilities of the `DataBuoy` class and then evaluate whether the current testing suite does a good job of capturing all this functionality or if there is anything missing/extra.

## Problem
Accessing data from NDBC data stations is cumbersome and not easily scripted.

## DataBuoy responsibilities - for now
* Allow users to request NDBC data packages for a given station for any time period.
    * Return data package as `pandas DataFrame` if it exists
    * Return a warning message if it does not

* Allow users to save the current state of a DataBuoy object to disk
* Allow users to search for data stations based on geographic coordinates

Presently the tests in `test_databuoy.py` appear to cover all of these aspects of the domain.  However, one aspect covered in this chapter has not been addressed.  That is whether a DataBuoy object should be treated as an Entity or a Value Object.  How should we implement equality?  Two objects could have the same `station_id` but different data packages and/or time periods.  Hmmmmmm......


![[projects.ndbc-reader.design.domain.models]]

