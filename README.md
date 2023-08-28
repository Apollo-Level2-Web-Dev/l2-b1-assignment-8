# l2-b1-assignment-8

# Build a Book Catallog Backend Assignment

<!-- ### Create Private Repo with this [link](https://classroom.github.com/a/le5T8iGk)
[https://classroom.github.com/a/le5T8iGk](https://classroom.github.com/a/le5T8iGk) -->

<hr>
### Assignment No: 08

### Assignment Name:

You have been assigned the task of building the backend for a Book Listing Application. The main focus of this assignment is to implementCRUD operations, pagination and filtering using Express , PostgreSQL and Prisma .

### Technology Stack:

- Use TypeScript as the programming language.
- Use Express.js as the web framework.
- Use Prisma as the Object Realtion Model (ORM)
- Use postgreSQL as the database

### Model:

### User Model:

- name
- email
- password
- role → admin / customer
- contactNo
- address
- profileImg

### Category Model:

- title

### Book Model:

- title
- author
- price
- genre
- publicationDate
- categoryId

### ReviewAndRating:

- review
- rating
- userId
- bookId

### Orders

- userId
- orderedBooks → Array of book ids
- status → ‘pending’/ ‘shipped’/’delivered’ → default shoulb be “pending”
- createdAt

# Main Part:

## Implement Create, Read, Update, and Delete Operations for Users Listing

### User Sign Up

Route: /api/v1/auth/signup (POST)

Request body:

### Sample Data:

```json
{
  "name": "Jhon Doe",
  "email": "john@example.com",
  "password": "john123",
  "role": "customer",
  "contactNo": "1234567890",
  "address": "Dhaka, Bangladesh",
  "profileImg": "user.jpg"
}
```

Response: The newly created user object.

Response Sample Pattern:

```json
Firoz

```

### Get All Users → Only Allowed For Admin

Route: /api/v1/users (GET)

Request body:

Response: The user's array of objects.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Users retrieved successfully",
  "data": [{}, {}]
}
```

### Get a Single User → Only Allowed For Admin

Route: /api/v1/users/:id (GET)

Request Param: :id

Response: The specified user object.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "User getched successfully",
  "data": {}
}
```

### Update a Single User → Only Allowed For Admin

Route: /api/v1/users/:id (PATCH)

Request Param: :id

Response: The updated user object.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "User updated successfully",
  "data": {}
}
```

### Delete a User → Only Allowed For Admin

Route: /api/v1/users/:id ( DELETE)

Request Param: :id

Response: The deleted user object.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Uers deleted successfully",
  "data": {}
}
```

## Implement Create, Read, Update, and Delete Operations for Category Listing

### Create Category

Route: /api/v1/categories/create-category (POST) → Only Allowed For Admin

Request body:

### Sample Data:

```json
{
  "title": "Fiction"
}
```

Response: The newly created category object.

Response Sample Pattern:

```json
 Firoz
```

### Get All Categories

Route: /api/v1/ategories (GET)

Request body:

Response: The categoryies array of objects.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Categories fetched successfully",
  "data": [{}, {}]
}
```

### Get a Single Category

Route: /api/v1/users/:id (GET)

Request Param: :id

Response: The specified user object.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Category fetched successfully",
  "data": {}
}
```

### Update a Category → Only Allowed For Admin

Route: /api/v1/categories/:id (PATCH)

Request Param: :id

Response: The updated category object.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Category updated successfully",
  "data": {}
}
```

### Delete a Category → Only Allowed For Admin

Route: /api/v1/categories/:id ( DELETE)

Request Param: :id

Response: The deleted category object.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Category deleted successfully",
  "data": {}
}
```

## Implement Create, Read, Update, and Delete Operations for Book listings.

### Create a New Book

Route: /api/v1/books/create-book (POST) → Only Allowed For Admin

Request body:

```json
{
  "title": "The Catcher in the Rye",
  "author": "J.D. Salinger",
  "genre": "Fiction",
  "price": 350.75,
  "publicationDate": "1951-07-16",
  "categoryId": "a3c7b742-6a34-4c6f-b6b0-58f41d48d5c6"
}
```

Response: The newly created book object.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Book created successfully",
  "data": {
    {
      "id": "abm45888vbvbb5667",
      "title": "The Catcher in the Rye",
      "author": "J.D. Salinger",
      "genre": "Fiction",
      "price": 350.75,
      "publicationDate": "1951-07-16",
      "categoryId": "f1234573-sfkjsf-45332"
    }
  }
}
```

### Get All Books

Route: /api/v1/books (GET)

Request body:

Response: The books array of objects with paginated metadata.

Response Sample Pattern:

```json
  {
      "success": true,
      "statusCode":200,
      "message": "Books fetched successfully",
      "meta": {
        "page": 3,
        "size": 10,
        "total":95,
        "totalPage":10
        }
      "data": [{},{}] ,
  }
```

### Seraching and filtering book listings: ( You do not need to implement searching and pagination as we implemented, you can do as your own )

Route: /api/v1/books?

Query parameters: (Case Insensitive)

- page: The page number for pagination (e.g., ?page=1).
- size: The number of book listings per page (e.g. ?limit=10).
- sortBy: The field to sort the cow listings (e.g. ?sortBy=price).
- sortOrder : The order of sorting, either 'asc' or 'desc' (e.g. ?sortOrder=asc).
- minPrice: The minimum price for filtering (e.g. ?minPrice=1000).
- maxPrice: The maximum price for filtering (e.g. ?maxPrice=5000).
- category: Filter using category id (e.g : ?category=f1234573-sfkjsf-45332)

- search: The search query string for searching books (e.g., ?title="Programmig"). (Search Fields should be title,author,genre)

Response: An array of books listing objects that match the provided filters, limited to the specified page ,size and total page.

Response Sample Pattern:

```json
  {
      "success": true,
      "statusCode":200,
      "message": "Books fetched successfully",
      "meta": {
        "page": 3,
        "size": 10,
        "total":63,
        "totalPage":7
        }

      "data": [{},{}],
  }
```

### Get Books By CategoryId

Route: /api/v1/books/:categoryId (GET)

Request Param: :categoryId

Response: The books array of objects with paginated metadata.

Response Sample Pattern:

```json
  {
      "success": true,
      "statusCode":200,
      "message": "Books with associated category data fetched successfully",
      "meta": {
        "page": 1,
        "size": 10,
        "total":25,
        "totalPage":3
        }
      "data": [{},{}] ,
  }
```

### Get a Single Book

Route: /api/v1/books/:id (GET)

Request Param: :id

Response: The specified book object.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Book fetched successfully",
  "data": {}
}
```

### Update a Single Book → Only Allowed For Admin

Route: /api/v1/books/:id (PATCH)

Request Param: :id

Response: The updated book object.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Book is updated successfully",
  "data": {}
}
```

### Delete a book → Only Allowed for admins

Route: /api/v1/books/:id ( DELETE)

Request Param: :id

Response: The deleted book object

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Book is deleted successfully",
  "data": {}
}
```

### Implement Create, Read Operations for Order Listings.

Route: /api/v1/orders/create-order (POST) → Only Allowed For Customer

Request body:

```json
{
  "userId": "u458-456vc-34dsa-vvcf",
  "orderedBooks": [
    {
      "bookId": "abm45888vbvbb5667",
      "quantity": 3
    },
    {
      "bookId": "xyv8991ghdjd9881",
      "quantity": 2
    }
  ]
}
```

Response: The newly created order object.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Book is deleted successfully",
  "data": {
    "id": "o567-xyz8-ddxy6-dd2f",
    "userId": "u458-456vc-34dsa-vvcf",
    "orderedBooks": [
      {
        "bookId": "abm45888vbvbb5667",
        "quantity": 3
      },
      {
        "bookId": "xyv8991ghdjd9881",
        "quantity": 2
      }
    ],
    "status": "pending",
    "createdAt": "2023-08-28T10:00:00Z"
  }
}
```

Route: /api/v1/orders (GET) → Only Allowed For Admins

Response: The ordered array of objects.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Orders retrieved successfully",
  "data": [{},{},....]
}
```

Route: /api/v1/orders (GET) → Only Specific For Customer

Request Headers: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiY3VzdG9tZXIiLCJ1c2VySWQiOiJvNTc3LXg4ODgtZGQ4Ni1kZDJmIiwiaWF0IjoxNTE2MjM5MDIyfQ.MejYWi-cw0zf5zFiJ5R09-PrCWOj8auEqAz2XY9im1Q"

Decoded Token:

```json
{
  "role": "customer",
  "userId": "o577-x888-dd86-dd2f",
  "iat": 1516239022   → "Please set the iat at least 1 year"
}
```

Response: The ordered array of objects.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Orders retrieved successfully",
  "data": [{},{},....]
}
```

# Bonus Part:

Route: /api/v1/orders/:orderId (Get) → Only for specific customer and admins

Request Headers: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiY3VzdG9tZXIiLCJ1c2VySWQiOiJvNTc3LXg4ODgtZGQ4Ni1kZDJmIiwiaWF0IjoxNTE2MjM5MDIyfQ.MejYWi-cw0zf5zFiJ5R09-PrCWOj8auEqAz2XY9im1Q"

Decoded Token:

```json
{
  "role": "customer",
  "userId": "o577-x888-dd86-dd2f",
  "iat": 1516239022   → "Please set the iat at least 1 year"
}
```

Please follow these steps to access the specific order:

- If the user's role is an admin, no further checks are required.

- If the user's role is a customer, verify that the order's userId matches the userId of the customer who placed the order. This step ensures that only customers who ordered individually will be able to see the specific order.

Route: /api/v1/profile (Get) → Only for specific user (customer and admin)

Request Headers: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiY3VzdG9tZXIiLCJ1c2VySWQiOiJvNTc3LXg4ODgtZGQ4Ni1kZDJmIiwiaWF0IjoxNTE2MjM5MDIyfQ.MejYWi-cw0zf5zFiJ5R09-PrCWOj8auEqAz2XY9im1Q"

Decoded Token:

```json
{
  "role": "customer",
  "userId": "o577-x888-dd86-dd2f",
  "iat": 1516239022   → "Please set the iat at least 1 year"
}
```

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Orders retrieved successfully",
  "data": {
    "name": "Jhon Doe",
    "email": "john@example.com",
    "password": "john123",
    "role": "customer",
    "contactNo": "1234567890",
    "address": "Dhaka, Bangladesh",
    "profileImg": "user.jpg"
  }
}
```

Please follow these steps to access the specific profile:

- Decode the token to extract the userId. If the userId exists, compare it with the userId in the User Model to find a match.

### Deadline:

- 60 Marks 3 Days (Till 3rd September Sunday 11.59 PM)
- 50 Marks 1 Day (Till 4th September Monday 11.59 PM)

`** In order for your assignment to be evaluated, it is essential to have a minimum of 15 meaningful commits. Please note that unnecessary commits will not be considered as part of the evaluation process.**`

### What to submit

1. Your Github Private Repository Link
2. Deployed Live Link (Vercel / Railway / Heroku or any other platform)
   - `** Do not use a logger. It will not work on the free hosting platforms **`
3. Must include all the routes into Readme.md file.
   - `** You must follow provided API Endpoints  for creating routes. Otherwise, you will lose your marks **`
     You can follow the pattern given below to enlist your application routes in the readme.md file:

### Live Link: https://example.com

### Application Routes:

#### User

- api/v1/auth/signup (POST)
- api/v1/users (GET)
- api/v1/users/6177a5b87d32123f08d2f5d4 (Single GET) Include an id that is saved in your database
- api/v1/users/6177a5b87d32123f08d2f5d4 (PATCH)
- api/v1/users/6177a5b87d32123f08d2f5d4 (DELETE) Include an id that is saved in your database

#### Cows

- api/v1/cows (POST)
- api/v1/cows (GET)
- api/v1/cows/6177a5b87d32123f08d2f5d4 (Single GET) Include an id that is saved in your database
- api/v1/cows/6177a5b87d32123f08d2f5d4 (PATCH)
- api/v1/cows/6177a5b87d32123f08d2f5d4 (DELETE) Include an id that is saved in your database

### Pagination and Filtering routes of Cows

- api/v1/cows?pag=1&limit=10
- api/v1/cows?sortBy=price&sortOrder=asc
- api/v1/cows?minPrice=20000&maxPrice=70000
- api/v1/cows?location=Chattogram
- api/v1/cows?searchTerm=Cha

#### Orders

- api/v1/orders (POST)
- api/v1/orders (GET)
