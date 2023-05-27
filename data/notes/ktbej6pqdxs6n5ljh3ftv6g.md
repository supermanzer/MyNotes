_This section is intended to capture design decisions for a potential Android application as part of the Recipes Server_

---

One of the important choices to make is how much data to store locally, if at all.  The book I am working through to build Android apps is making use of the [Room API](https://developer.android.com/jetpack/androidx/releases/room) to perform CRUD operations with an SQLite DB saved locally on the Android device's file system.  This makes me start to question an entirely API reliant design.

## Data Storage question
My question for this app is whether it would make more sense to use the local server just for performing the [[projects.local-recipe-server.services.text-parsing]] and [[projects.local-recipe-server.services.text-assigment]] functionality and store the final recipe record 
locally or whether I should rely on the REST API entirely.  While this would simplify application design it would mean the apps functionality would entirely depend on the health and availability of a Raspberry Pi runningon my local network

### Initial decision
* Proceed with entirely REST API driven approach 
* Be prepared to transition to more data storage in the Android device itself as I become more familiar with caching and synchronizing local data with the canonical server database.