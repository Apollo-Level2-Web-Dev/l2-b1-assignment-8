# l2-b1-assignment-8

# Build a Book Catallog Backend Assignment

<!-- ### Create Private Repo with this [link](https://classroom.github.com/a/le5T8iGk)
[https://classroom.github.com/a/le5T8iGk](https://classroom.github.com/a/le5T8iGk) -->

<hr>

### Assignment No: 08

### Assignment Description:

You have been assigned the task of building the backend for a Book Listing Application. The main focus of this assignment is to implement CRUD operations, pagination and filtering using Prisma, Postgres and Express.

### Technology Stack:

- Use TypeScript as the Programming Language.
- Use Express.js as the web framework.
- Use Prisma as the Object Realtion Model (ORM)
- Use postgreSQL as the database

### Model:

### User Model:

- id
- name
- email
- password
- role → admin / customer
- contactNo
- address
- profileImg

### Category Model:

- id
- title

### Book Model:

- id
- title
- author
- price
- genre
- publicationDate
- categoryId

### ReviewAndRating:

- id
- review
- rating
- userId
- bookId

### Orders

- id
- userId
- orderedBooks → Array of Object and object contains book Id and quantity
- status → ‘pending’/ ‘shipped’/’delivered’ → default should be “pending”
- createdAt

# Main Part:

## API End points and Sample Data:

## Implement Create, Read, Update, and Delete Operations for Users Listing

### User Sign Up

Route: /api/v1/auth/signup (POST)

Request body:

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

Response Sample Data:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "User created successfully!",
  "data": {
    "id": "2d267d12-6b9c-4ee0-a8e5-0d8f6c5c1e3b",
    "name": "John Doe",
    "email": "john@example.com",
    "role": "customer",
    "contactNo": "1234567890",
    "address": "Dhaka, Bangladesh",
    "profileImg": "user.jpg"
  }
}
```

### Get All Users → Only Allowed For Admin

Route: /api/v1/users (GET)

Request body:

Response: The user's array of objects.

Response Sample Data:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Users retrieved successfully",
  "data": [
    {
      "id": "2d267d12-6b9c-4ee0-a8e5-0d8f6c5c1e3b",
      "name": "John Doe",
      "email": "john@example.com",
      "role": "customer",
      "contactNo": "1234567890",
      "address": "Dhaka, Bangladesh",
      "profileImg": "user.jpg"
    },
    // More users...
  ]
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

Request Body: 
```json
{
  "name": "John Doe1",
  "email": "john1@example.com",
  "contactNo": "01234567890",
  "address": "Khulna, Bangladesh",
  "profileImg": "user1.jpg"
}
```

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
  "title": "Programming"
}
```

Response: The newly created category object.

Response Sample Pattern:

```json
 {
  "success": true,
  "statusCode": 200,
  "message": "Category created successfully",
  "data": {
    "id": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d",
    "title": "Programming"
  }
}

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

Response: The specified category object and books array of object.

Response Sample Data:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Category fetched successfully",
  "data": {
    "id": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d",
    "title": "Fiction",
    "books": [
      {
        "id": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
        "title": "The Catcher in the Rye",
        "author": "J.D. Salinger",
        "genre": "Fiction",
        "price": 350.75,
        "publicationDate": "1951-07-16"
      },
      {
        "id": "c9b2d566-1d8a-4fe1-8d15-07ed4f7c5dc9",
        "title": "To Kill a Mockingbird",
        "author": "Harper Lee",
        "genre": "Fiction",
        "price": 299.99,
        "publicationDate": "1960-07-11"
      }
      // More books...
    ]
  }
}

```

### Update a Category → Only Allowed For Admin

Route: /api/v1/categories/:id (PATCH)

Request Param: :id

Request Body: 
```json
{
  "title": "Fiction"
}
```

Response: The updated category object.

Response Sample Data:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Category updated successfully",
  "data": {
    "id": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d",
    "title": "Fiction"
  }
}

```

### Delete a Category → Only Allowed For Admin

Route: /api/v1/categories/:id ( DELETE)

Request Param: :id

Response: The deleted category object.

Response Sample Data:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Category deleted successfully",
  "data": {
    "id": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d",
    "title": "Fiction"
  }
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

Response: The newly created book object with category details.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Book created successfully",
  "data": {
    "id": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
    "title": "The Catcher in the Rye",
    "author": "J.D. Salinger",
    "genre": "Fiction",
    "price": 350.75,
    "publicationDate": "1951-07-16",
    "categoryId": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d",
    "category": {
      "id": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d",
      "title": "Fiction"
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
  "statusCode": 200,
  "message": "Books fetched successfully",
  "meta": {
    "page": 3,
    "size": 10,
    "total": 95,
    "totalPage": 10
  },
  "data": [
    {},{},
    // More books...
  ]
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
        },
      "data": [
        {},{},
        // More books
        ]
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
  "statusCode": 200,
  "message": "Books with associated category data fetched successfully",
  "meta": {
    "page": 1,
    "size": 10,
    "total": 25,
    "totalPage": 3
  },
  "data": [
    {},{},
    // More books...
  ]
}

```

### Get a Single Book

Route: /api/v1/books/:id (GET)

Request Param: :id

Response: The specified book object.

Response Sample Data:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Book fetched successfully",
  "data": {
    "id": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
    "title": "The Catcher in the Rye",
    "author": "J.D. Salinger",
    "genre": "Fiction",
    "price": 350.75,
    "publicationDate": "1951-07-16",
    "categoryId": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d"
  }
}

```

### Update a Single Book → Only Allowed For Admin

Route: /api/v1/books/:id (PATCH)

Request Param: :id

Request Body: 
```json
{
  "title": "The Catcher in the Rye Part-1",
  "author": "J.D. John",
  "genre": "Programming",
  "price": 340.75,
}
```

Response: The updated book object.

Response Sample Data:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Book updated successfully",
  "data": {
    "id": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
    "title": "The Catcher in the Rye Part-1",
    "author": "J.D. John",
    "genre": "Programming",
    "price": 340.75,
    "publicationDate": "1951-07-16",
    "categoryId": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d"
  }
}

```

### Delete a book → Only Allowed for admins

Route: /api/v1/books/:id ( DELETE)

Request Param: :id

Response: The deleted book object

Response Sample Data:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Book is deleted successfully",
  "data": {
    "id": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
    "title": "The Catcher in the Rye Part-1",
    "author": "J.D. John",
    "genre": "Programming",
    "price": 340.75,
    "publicationDate": "1951-07-16",
    "categoryId": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d"
  }
}
```

### Implement Create, Read Operations for Order Listings.

### Create Order → Only Allowed For Customer

Route: /api/v1/orders/create-order (POST) 

Request body:

```json
{
  "userId": "b2e06b3e-87bf-4b11-a74a-29c66f8f48df",
  "orderedBooks": [
    {
      "bookId": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
      "quantity": 3
    },
    {
      "bookId": "c9b2d566-1d8a-4fe1-8d15-07ed4f7c5dc9",
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
  "message": "Order created successfully",
  "data": {
    "id": "fe659812-5b10-4b6d-b88d-7b9e60902a67",
    "userId": "b2e06b3e-87bf-4b11-a74a-29c66f8f48df",
    "orderedBooks": [
      {
        "bookId": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
        "quantity": 3
      },
      {
        "bookId": "c9b2d566-1d8a-4fe1-8d15-07ed4f7c5dc9",
        "quantity": 2
      }
    ],
    "status": "pending",
    "createdAt": "2023-08-28T10:00:00Z"
  }
}
```

### Get all Order → Only Allowed For Admins

Route: /api/v1/orders (GET)

Response: The ordered array of objects.

Response Sample Pattern:

```json
{
  "success": true,
  "statusCode": 200,
  "message": "Orders retrieved successfully",
  "data": [
    {},
    // More orders...
  ]
}
```

### Get all Order for specific Customer → Only Specific For Customer

Route: /api/v1/orders (GET) 

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
  "data": [
    {},
    // More orders...
  ]
}

```

# Bonus Part:

### Get single order by Id → Only for specific customer and admins

Route: /api/v1/orders/:orderId (Get) 

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

Sample Response Data:
```json
{
  "success": true,
  "statusCode": 200,
  "message": "Order fetched successfully",
  "data": {
    "id": "fe659812-5b10-4b6d-b88d-7b9e60902a67",
    "userId": "b2e06b3e-87bf-4b11-a74a-29c66f8f48df",
    "orderedBooks": [
      {
        "bookId": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
        "quantity": 3
      },
      {
        "bookId": "c9b2d566-1d8a-4fe1-8d15-07ed4f7c5dc9",
        "quantity": 2
      }
    ],
    "status": "pending",
    "createdAt": "2023-08-28T10:00:00Z"
  }
}

```

### Get User Profile Data → Only for specific user (customer and admin)

Route: /api/v1/profile (Get) 

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
- api/v1/profile (GET)

### Category

- api/v1/categories/create-category (POST)
- api/v1/categories (GET)
- api/v1/categories/6177a5b87d32123f08d2f5d4 (Single GET) Include an id that is saved in your database
- api/v1/categories/6177a5b87d32123f08d2f5d4 (PATCH)
- api/v1/categories/6177a5b87d32123f08d2f5d4 (DELETE) Include an id that is saved in your database

### Books

- api/v1/books/create-book (POST)
- api/v1/books (GET)
- api/v1/books/:categoryId (GET)
- api/v1/books/:id (GET)
- api/v1/books/:id (PATCH)
- api/v1/books/:id (DELETE)

### Orders

- api/v1/orders/create-order (POST)
- api/v1/orders (GET) 
- api/v1/orders/:orderId (GET)

