# The Repository Pattern

## What is a Repository Pattern?
This is a layer of abstraction/encapsulation that provides a simple and clean interface between persistent storage (RDMS, CSV files, etc.) and the dommain model without causing the domain model to be dependent on the structure of the persistent storage.

## Why Do It?
This is more work up front that directly implementing an ORM and defining your models in your database.  But as the complexity of the business domain increases, the amount of work required to keep your data models and business logic up to date will scale well and require less work over time to maintain.

This is handled in the `repository.py` file and in this abstraction we simply create a light wrapper around the SQLAlchemy ORM and how we implement creating, retrieving, and listing our data.  This will get more complicated as we go.


