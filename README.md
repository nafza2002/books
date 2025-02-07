1. Introduction:  
The Books Management System is a centralized system designed to manage and provide access to book inventory in a bookstore. The system allows users to retrieve book-related data through a RESTful API built using MuleSoft, with data stored in a relational database. 

This system ensures efficient book management, allowing users to: 

Retrieve a list of all available books. 

Search for a specific book by its ID. 

Filter books by category. 

Handle error scenarios gracefully, such as when a book is not found. 

 

1.1 Technologies Used 

MuleSoft (Mule 4) → API development & integration. 

Database (MySQL/PostgreSQL) → Stores book inventory. 

MUnit → Automated testing for API validation. 

Solution Design 

3.1  Database Design 

Table: books 

 CREATE TABLE books ( 
    id INTEGER PRIMARY KEY, 
    title VARCHAR(200), 
    author VARCHAR(100), 
    category VARCHAR(50), 
    price DECIMAL(10,2), 
    quantity INTEGER, 
    last_updated TIMESTAMP DEFAULT CURRENT_TIMESTAMP 
); 
 

 

3.2  API Specifications 

1. Get All Books 

Method: GET /api/books 

Response: Returns a list of all books. 

2. Get Specific Book 

Method: GET /api/books/{id} 

Response: Returns details of a specific book or an error if not found. 

3. Get Books by Category 

Method: GET /api/books/category/{category} 

Response: Returns books matching the category. 

 

3.3 Error Handling Strategy 

404 Not Found – Book does not exist. 

200 Found – Book exist 

 

Error Response Example: 

{ 
    "error": "Book not found", 
    "timestamp": "2025-02-05T10:00:00Z" 
} 

6. Unit Testing 
6.1 Positive Test Cases 

  Get All Books: Validate if all books are fetched correctly. 

  Get Specific Book by ID: Ensure correct book details are returned for a valid ID. 

  Get Books by Category: Check if books matching the category are retrieved. 

6.2  Negative Test Cases 

  Book Not Found: Simulate an invalid book ID and expect a 404 error. 

  Database Connection Failure: Simulate DB downtime and check if a 500 error is returned. 

 
REST API → Data retrieval & management. 
