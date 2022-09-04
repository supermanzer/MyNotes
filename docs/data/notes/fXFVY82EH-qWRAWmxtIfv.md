Since this aspect of the application will utililze both front and back-end features, I'm not splitting it out into either the Models or Nuxt sections.

## Types of Notifications
Let's think through the kinds of notifications we would want to send a user and where in their experience with the application this would take place.

### A Note on API Design
Since both of these kinds of information represent user-specific data, I think we shoud nest the routes for retrieving all of this data within the general `user/:id/` endpoint.  This is a good place to use the [`@action` decorators for Django-REST-Framework viewsets](https://www.django-rest-framework.org/api-guide/viewsets/#marking-extra-actions-for-routing)

### Late Fees
Less than fun for the user, this notification would alert a user of the total amount of fees owed to the library.  Now what do we need to make this happen?
* **Home page**: This should be presented to the user under our banner on the home page.  We will want a component that makes a request to the API and, if the fees returned are greater than 0. display a warning.  Right now I think this should just have a link to the user's profile page since the intent of that page is to handle all user-specific features.
* **Snack bar**:  We want to get paid right?  So we'll put it up in their face.  This will also give me exposure to integrating more buttons on the Snack bar element besides the `Close` feature.
* **Pay Fee Component**:  This would be a simple form that displays each instance of a Borrowed copy for which we have an outstanding late fee and request the user to pay their fees.
* **API**:  Rather than fecthing all the books associated witha user and performing some `reduce()` operation to get the total late fees, I think we can do this in the database.  It may not be best practice because generalized approaches are usually preferred but I'm in charge here and I say we're using the PostgreSQL server for this!  

### Reservations
Now here's something our patrons will enjoy a bit more.  We want to notify them when a book they have reserved has been returned to circulation.  For a refresher on this workflow take a peek [[here|projects.localibrary.models.dependent-status.approaches]].  Alright so how should this work?

I'm thinking the same snack bar/home page element approach as I would want multiple chances to encounter the notification that a book I was waiting on is available.  We don't need any mechanism to pay fees and we can re-use the checkout functionality currently available for book instances.  

The real question here is how to identify when this is the case for a given user's `BorrowedCopy` record.  The back end allows any number of users to create reservations for books that are not currently available.  We need to ensure we apply a FIFO strategy to these reservations **and** we have a way to to query our `BorrowedCopy` records by user and _only_ return records that are valid for checkout.  I smell more query annotations!

