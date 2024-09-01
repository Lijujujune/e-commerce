# E-commerce backend API

This project is a backend API for an e-commerce platform, built using Node.js, Express.js, Sequelize, and PostgreSQL. The API provides CRUD operations for categories, products, and tags in the e-commerce database.

## Links:
    Github: https://github.com/Lijujujune/e-commerce.git
    Walkthrough video: https://bootcampspot.instructuremedia.com/embed/e17cb781-6f5b-4f40-a709-151cfb469b59

## Table of Contents
	•	Installation
	•	Usage
	•	Project Structure
	•	Models
	•	Routes
	•	Environment Variables
	•	License
    

## Installation

	1.	Clone the repository:
        git clone https://github.com/Lijujujune/e-commerce.git
        cd e-commerce
    
    2. 	Install dependencies:
        npm install
    
    3.	Set up your PostgreSQL database:
	    •	Make sure you have PostgreSQL installed and running.
	    •	Create a new database in PostgreSQL.

	4.	Configure environment variables:
	    •	Create a .env file in the root directory of the project.
	    •	Add environment variables to the .env file

    5.	Run database migrations and seed data:
        run schema.sql under DB file
        npm run seed

## Usage    
    1. Start the server
        npm start
    
    2. Open Insomnia to use GET/POST/PUT/DELETE functions

## Porject Structure
e-commerce/
│
├── config/
│   └── connection.js        # Database connection configuration
│
├── models/
│   ├── index.js             # Model associations
│   ├── Category.js          # Category model
│   ├── Product.js           # Product model
│   ├── Tag.js               # Tag model
│   └── ProductTag.js        # ProductTag model (junction table)
│
├── routes/
│   ├── api/
│   │   ├── category-routes.js  # Routes for categories
│   │   ├── product-routes.js   # Routes for products
│   │   └── tag-routes.js       # Routes for tags
│   └── index.js               # Main router
│
├── server.js                # Entry point of the application
├── .env                     # Environment variables (not included in version control)
└── package.json             # Project configuration and dependencies

## Models

Category

	•	id (Integer, primary key, auto increment, not null)
	•	category_name (String, not null)

Product

	•	id (Integer, primary key, auto increment, not null)
	•	product_name (String, not null)
	•	price (Decimal, not null, validates as decimal)
	•	stock (Integer, not null, default value 10, validates as numeric)
	•	category_id (Integer, references Category model’s id)

Tag

	•	id (Integer, primary key, auto increment, not null)
	•	tag_name (String)

ProductTag

	•	id (Integer, primary key, auto increment, not null)
	•	product_id (Integer, references Product model’s id)
	•	tag_id (Integer, references Tag model’s id)

Routes

Category Routes (/api/categories)

	•	GET / - Get all categories with their associated products
	•	GET /:id - Get a single category by its id and its associated products
	•	POST / - Create a new category
	•	PUT /:id - Update a category by its id
	•	DELETE /:id - Delete a category by its id

Product Routes (/api/products)

	•	GET / - Get all products with their associated categories and tags
	•	GET /:id - Get a single product by its id with its associated categories and tags
	•	POST / - Create a new product
	•	PUT /:id - Update a product by its id
	•	DELETE /:id - Delete a product by its id

Tag Routes (/api/tags)

	•	GET / - Get all tags with their associated products
	•	GET /:id - Get a single tag by its id with its associated products
	•	POST / - Create a new tag
	•	PUT /:id - Update a tag by its id
	•	DELETE /:id - Delete a tag by its id

## License

This project is licensed under the MIT License.