# Admire-Sankoh-DIT1202-905005273
Object Oriented Prpogramming Method 2


[app.py](https://github.com/user-attachments/files/28268385/app.py)
from fastapi import FastAPI

app = FastAPI()

# Sample data (acts like a database)
books = [
    {"id": 1, "title": "Python Basics", "author": "John Doe", "available": True},
    {"id": 2, "title": "Web Development", "author": "Jane Smith", "available": True}
]

# Home route
@app.get("/")
def home():
    return {"message": "Welcome to the Library API"}

# Get all books
@app.get("/books")
def get_books():
    return books 

# Get a single book by ID
@app.get("/books/{book_id}")
def get_book(book_id: int):
    for book in books:
        if book["id"] == book_id:
            return book
    return {"error": "Book not found"}

# Add a new book
@app.post("/books")
def add_book(book: dict):
    books.append(book)
    return {"message": "Book added successfully", "book": book}

# Update a book
@app.put("/books/{book_id}")
def update_book(book_id: int, updated_book: dict):
    for index, book in enumerate(books):
        if book["id"] == book_id:
            books[index] = updated_book
            return {"message": "Book updated successfully"}
    return {"error": "Book not found"}

# Delete a book
@app.delete("/books/{book_id}")
def delete_book(book_id: int):
    for book in books:
        if book["id"] == book_id:
            books.remove(book)
            return {"message": "Book deleted successfully"}
    return {"error": "Book not found"}
@app.get("/")
def home():
    return {"message": "Welcome to the Library API"}
