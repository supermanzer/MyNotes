
We currently are attempting to make double use of our BorrowedCopy data model for both tracking borrowed copies and borrowing histories as well as reservations.  **However** one borrows a particular copy of a book **but** one makes a reservation for a general Book.  Therefore this approach is silly.  It means a patron may be waiting on an overdue copy of a book while other copies sit on the shelf, ready to check out.

This is something I try to keep in mind when designing databases and/or data models:  
> **Does your model accurately represent the physical/logical entity it references?**

In our case the approach to shoehorn forward looking reservations into a model for tracking borrowing histories does not. 

Let's try to make that a bit more realistic with

## Reservation Model
![[projects.localibrary.models.refactoring.reservation]]
