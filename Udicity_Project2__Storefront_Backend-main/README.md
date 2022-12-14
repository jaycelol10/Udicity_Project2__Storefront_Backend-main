# Storefront Backend Project

#### install all dependencies

    npm i

#### please create in your local machine two databases
    - Open the SQL Shell
    - CREATE USER postgres WITH PASSWORD 'postgres';
    - CREATE DATABASE storefront;
    - CREATE DATABASE storefront-test;
    - GRANT ALL PRIVILEGES ON DATABASE storefront TO postgres
    - GRANT ALL PRIVILEGES ON DATABASE storefront-test TO postgres

#### databases must run on

    host: localhost
    port: 5432

#### to build database schema

    npm run migrate

#### to run test script

    npm run test

#### to run the server

    npm start

#### server is running at

    localhost:3000

## Schema:

**Users**:
| Column | Type |
|--------|------|
| ID | STRING/UUID |
| Username | STRING |
| First name | STRING |
| Last name | STRING |
| Password | STRING |
| Isadmin | BOOLEAN |

**Products**:
| Column | Type |
|--------|------|
| ID | STRING/UUID |
| Name | STRING |
| Price | INTEGER |

**Orders**:
| Column | Type |
|--------|------|
| ID | STRING/UUID |
| User_id | foreign key to users(id) |
| status | STRING |

**Order_products**:
| Column | Type |
|--------|------|
| Order_id | foreign key to users(id) |
| Product_id | foreign key to users(id) |
| Quantity | INTEGER |

## users endpoints

#### user can be create account & sign in & delete user

    (post) localhost:3000/user/signup
    (post) localhost:3000/user/signin
    (delete) localhost:3000/user/:id  <userToken required>

#### admin can be show all users

    (get) localhost:3000/user/all <adminToken required>

#### to make normal user as admin

    (post) localhost:3000/user/admin <userToken required>

## products endpoints

#### admin can be create new product

    (post) localhost:3000/product/ <adminToken required>

#### user can be show all product & show one product by id

    (get) localhost:3000/product/
    (get) localhost:3000/product/:id

## orders endpoints

#### user can be create a new order& add product to order & show his orders & delete an order

    (post) localhost:3000/oreder/ <userToken required>
    (post) localhost:3000/addtoorder/ <userToken required>
    (get) localhost:3000/oreder/  <userToken required>
    (delete) localhost:3000/oreder/:id  <userToken required>

#### admin can be show all orders & update status of order to complete

    (put) localhost:3000/oreder/:id <adminToken required>
    (get) localhost:3000/oreder/all <adminToken required>

#### create file named .env and copy this environment variables to it to test project
    DB_HOST=localhost
    DB_NAME=storefront
    TEST_DB_NAME=storefront_test
    DB_USER=postgres
    DB_PASSWORD=postgres
    JWT_SECRET= ajksgfjaslkgjlaijglajweogijoiejwo
    PORT=3000
    ENV=dev
    ADMIN_SECRET=SECRET_PASSWORD
    SALT_ROUND=10

#

# https://documenter.getpostman.com/view/18849836/2s8YRcPGhm

## show this Postman API documentation to know all about requests and response shapes
