# Domain Model

The domain is the problem you are trying to solve or the activities you are looking to support through your software. In the scenario where you are building a piece of software to support a business the domain represent the aspects of running the business.

It is well worth the time to spend the first part of designing the software discussing the problem to be solved with the subject matter experts.  This includes learning the domain specfic terminology (Domain Language) and the processes they represent.  You will want to integrate this into your software in order to better map software functionality to the problems you are solving.

## Concrete Example
For this book we will be using the example of an online furniture retailer as the business we are looking to support. To support this business we be building software to handle purchasing stock (furniture) from suppliers, allocating stock (either to the warehouse or to placed orders), taking sales online, and tracking stock in a warehouse.

### Example Domain
We have defined what the software should do.  So the domain of our problem is the necesary pieces to hanlde that.  In this case are building out 
1. A series of data models to support what we need
    1. `Batch` represents a lot of stock units purchased from a supplier
    1. `OrderLine` represents a line item purchased by a customer
    1. Functionallity to implement stock allocation that follows the business rules defined by subject matter experts

So far we have a useful data model that is easy to inspect, test, and modify

