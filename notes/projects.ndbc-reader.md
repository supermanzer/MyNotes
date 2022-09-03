---
id: 6fc953db-7d86-483d-82c4-40e1675f6d1f
title: NDBC Reader
desc: >-
  A Python software package designed to simplify the retrieval of data from NDBC
  data stations
updated: 1662229426383
created: 1622482415473
---

* **Project:** 

These notes are being added only after the project's complexity has reached a point where I feel the need to jot things down in order to keep track of everything in my head.  Additionally, even though these are notes to myself about my own software projects, I still write as if I'm explaining these ideas to someone else.  It's a habit I picked up when I started coding in grad school and, since it works for me, I do not feel any need to change. Alright, on to the confusing bits!

---
## Next steps

This project has been neglected since I changed jobs and have had to spend more of my free time learning different programming languages and paradigms in order to keep up.  However that comes with a bonus of exposure to more enterprise grade software architecture.  With that in mind I plan to make a more rigorous effort to use a more design pattern driven approach to the NDBC Reader package.  

What follows is a first draft of the patterns and approaches I think would make sense to employ in this effort.

* **Data Store/Data Transfer Object:** This is a more codified approach to storing the various elemets of the data that the NDBC Reader project is the focus of.  This will also encapsulate saving a Data Buoy object to disk and re-instantiating from saved data.
* **Repository:** The repository pattern encapsulates the logic required to create, delete, and update the data.  
* **API Services:** These services will encapsulate the logic required to make specific API requests.  
* **Analysis Service:** This will encapsulate the rudimentary analyses that will be added to the NDBC Reader package and the Data Buoy class.
* **Unit of Work:** This will abstract the communication between the API services (fetching data) and the repository (storing data).

