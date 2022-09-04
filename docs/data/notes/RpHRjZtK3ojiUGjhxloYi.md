
I have identified that the `BorrowedCopy` model is not the correct way to allow patrons to reserve a Book since it will only place a reservation on a specific copy of a book.  Patrons do not care whether they have copy A or B as long as it's the book that they want to read.  So let's take a look at the definition for this model.

```python
# catalog/models.py
class Reservation(models.Model):
    """Defines a reservation for a book by library patron"""
    ... # date created/modified yada yada yada
    patron = models.ForeignKey(
        User, on_delete=models.SET_NULL, related_name='reservations')
    book = models.ForeignKey(
        Book, on_delete=models.CASCADE, related_name='reservations'
    )
    borrowed_copy = models.ForeignKey(
        BorrowedCopy, on_delete=moodels.CASCADE, related_name='reservations'
    )
    canceled = models.BooleanField(
        verbose_name='Reservation Canceled', default=False,
        help_text='Cancel if this reservation is no longer requested'
    )

    class Meta:
        ordering=['patron_id', 'date_created', 'id']

```

The `canceled` field is added to track the cancelation of reservations by patrons prior to fulfilling them.  This approach is taken rather than simply deleting the specific `Reservation` record because it will allow library staff to capture demand for a particular book.  Perhaps they can use this information when determining which, if any, existing books to buy more copies of.
