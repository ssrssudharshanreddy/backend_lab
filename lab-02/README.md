
# Lab 2: SQLite Database and CRUD Routes

## Student Details

- **Name:** SOMULA SUDHARSHAN REDDY
- **Registration Number:** 252U1R1231
- **Section:** CSE-CORE-2E

## Objective

To connect an Express server to a SQLite database and implement CRUD operations using HTTP routes.

## Technologies Used

- Node.js
- Express.js
- SQLite
- sqlite3
- Nodemon
- JavaScript

## Project Structure

```text
lab-02/
├── database/
│   └── bookStore.db
├── screenshots/
├── .gitignore
├── lab-02.http
├── package.json
├── package-lock.json
├── README.md
└── server.js
```

## Installation

Install the required dependencies:

```bash
npm install
```

## Database Setup

Create the database folder:

```bash
mkdir database
```

Create the SQLite database:

```bash
sqlite3 database/bookStore.db
```

Create the `book` table and insert the sample records using the SQL commands provided in the lab implementation.

## Running the Application

Start the server using Nodemon:

```bash
npm run dev
```

The server runs at:

http://localhost:3000/

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | /books/ | Get all books |
| GET | /books/:bookId/ | Get a book by ID |
| POST | /books/ | Add a new book |
| PUT | /books/:bookId/ | Update a book |
| DELETE | /books/:bookId/ | Delete a book |

## HTTP Status Codes

| Status Code | Description |
|---|---|
| 200 | Request successful |
| 201 | Book created successfully |
| 404 | Book not found |

## Screenshots

### 1. GET All Books

![GET All Books](screenshots/get-all-books.png)

### 2. GET Book by ID

![GET Book by ID](screenshots/get-book-by-id.png)

### 3. POST Add Book

![POST Add Book](screenshots/post-book.png)

### 4. PUT Update Book

![PUT Update Book](screenshots/put-book.png)

### 5. DELETE Book

![DELETE Book](screenshots/delete-book.png)

### 6. SQLite Database

![SQLite Database](screenshots/database.png)

## Notes

- Used SQLite to store book information.
- Implemented five CRUD operations using Express routes.
- Used parameterized queries with `?` placeholders.
- Tested the endpoints using HTTP requests.
- Nodemon automatically restarts the server when changes are made.
- The database is updated after POST, PUT and DELETE operations.

## Deployment

Live link: Not deployed. The application is tested locally.

## Conclusion

Successfully connected an Express server to a SQLite database and implemented five CRUD operations. Tested the API endpoints and verified database changes.
