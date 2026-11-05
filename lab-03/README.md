# Lab 3: REST API, query parameters, validation, debugging

**Name:** SOMULA SUDHARSHAN REDDY  
**Registration Number:** 252U1R1231  
**Section:** CSE-CORE-2E


## Objective
Turn the Lab 2 book routes into a REST API supporting title search, sorting, pagination, price filtering, input validation, correct status codes, consistent JSON errors, and debugging of common issues.

## Technologies
- Node.js
- Express.js
- SQLite
- `sqlite` and `sqlite3`
- Nodemon
- VS Code REST Client or Postman

## Installation and setup

Install packages:

```bash
npm install
```

Create the database directory (already included in this folder):

```powershell
mkdir database
```

Create the database and seed the table using SQLite CLI from the `lab-03` folder:

```powershell
sqlite3 database/bookStore.db
```

At the SQLite prompt, execute:

```sql
.read database/seed.sql
```

Then exit:

```sql
.exit
```

If SQLite CLI is not in PATH, invoke it using its full path, for example:

```powershell
& "C:\sqlite\sqlite3.exe" database/bookStore.db
```

## Run

```bash
npm run dev
```

The server uses port `3000` by default. Set the `PORT` environment variable to use a different port. No other environment variables are required.

## Endpoints

| Method | Path | Description |
|---|---|---|
| GET | `/books` | Retrieve books with optional search, sort, pagination and price filters |
| GET | `/books/:bookId` | Retrieve a book by ID |
| POST | `/books` | Validate and create a book |
| PUT | `/books/:bookId` | Validate and update a book |
| DELETE | `/books/:bookId` | Delete a book |

### GET /books query parameters

| Parameter | Default | Description |
|---|---|---|
| `search_q` | empty | Partial title search using SQL `LIKE` |
| `order_by` | `title` | Sort field: `id`, `title`, `author`, `price`, `pages` |
| `order` | `ASC` | Sort direction: `ASC` or `DESC` |
| `limit` | `10` | Number of records to return; must be integer >= 1 |
| `offset` | `0` | Number of records to skip; must be integer >= 0 |
| `min_price` | not applied | Inclusive minimum price |
| `max_price` | not applied | Inclusive maximum price |

## HTTP status codes
- `200`: successful retrieval, update, or delete
- `201`: book created
- `400`: invalid input or query parameter
- `404`: requested book or route not found
- `500`: unexpected server/database error

Error responses use JSON format:

```json
{
  "message": "Book not found"
}
```

## Test list
Use `lab-03.http` with the VS Code REST Client extension or Postman. It includes successful and failure cases:
- GET all, title search, sort, pagination, and price range
- GET book by ID and missing ID
- POST valid book, missing title, and non-numeric price
- PUT successful update and missing record
- DELETE successful delete and missing record
- Invalid sort direction and limit



## Notes: problems and solutions
- **EADDRINUSE (port already in use):** stop the other process/server or set a different `PORT`.
- **Wrong import path:** check the relative path and exact filename in `require(...)`.
- **No such table:** verify the database filename/path and ensure `database/seed.sql` has been executed against `bookStore.db`.
- **Missing await:** await asynchronous database calls before sending the HTTP response.
- SQLite queries use parameter placeholders for values. The `order_by` field is selected from an allowlist because SQL identifiers cannot be safely passed as ordinary bound values.
- `node_modules/` and `.env` must not be committed.

## GitHub submission
Place this folder as `lab-03/` in the course repository. Commit meaningful changes and share the public repository link or give faculty access.
