# mypythonproject1
import json

# Define the Book class
class Book:
    def __init__(self, book_id, title, author, year, status='available'):
        self.book_id = book_id
        self.title = title
        self.author = author
        self.year = year
        self.status = status

    def __str__(self):
        return f"{self.book_id}. {self.title} by {self.author} ({self.year}) - {self.status}"

# Define the User class
class User:
    def __init__(self, user_id, username, password):
        self.user_id = user_id
        self.username = username
        self.password = password
        self.borrowed_books = []

    def __str__(self):
        return f"User ID: {self.user_id}, Username: {self.username}"

    def borrow_book(self, book):
        if book.status == 'available':
            self.borrowed_books.append(book)
            book.status = 'borrowed'
            return f"You have successfully borrowed '{book.title}'."
        else:
            return f"Sorry, '{book.title}' is currently unavailable."

    def return_book(self, book):
        if book in self.borrowed_books:
            self.borrowed_books.remove(book)
            book.status = 'available'
            return f"You have successfully returned '{book.title}'."
        else:
            return f"You haven't borrowed '{book.title}'."
