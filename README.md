# Hotwax
Assignments
#Assignment-1

CREATE DATABASE hotwax;

USE hotwax;

CREATE TABLE products (
    product_id VARCHAR(26) PRIMARY KEY,
    product_name VARCHAR(100),
    product_description TEXT,
    product_returnable VARCHAR(10),
    OWNER VARCHAR(100)
);

CREATE TABLE users (
    user_id VARCHAR(20) PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    pincode VARCHAR(16) UNIQUE 
);

CREATE TABLE address (
    pincode VARCHAR(16) PRIMARY KEY,
    city VARCHAR(25),
    state VARCHAR(25),
    FOREIGN KEY (pincode) REFERENCES users(pincode)
);

CREATE TABLE orders (
    order_id VARCHAR(45) PRIMARY KEY,
    product_id VARCHAR(45),
    user_id VARCHAR(45),
    total DOUBLE,
    DATE DATE,
    STATUS VARCHAR(50),
    FOREIGN KEY (product_id) REFERENCES products(product_id),
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);

INSERT INTO users (user_id, first_name, last_name, pincode)
VALUES ('21', 'Aditya', 'Gupta','452010');

INSERT INTO address (pincode,city,state)
VALUES ('452010', 'Indore', 'MP');

INSERT INTO products (product_id, product_name,product_description,product_returnable, OWNER)
VALUES 
('11', 'airpods', 'apple gen2','No','Adi'),
('12','shirt','puma-xl','YES','Adi') ;

INSERT INTO orders (order_id,product_id, user_id, total,DATE,STATUS)
VALUES ('90', '11', '21','900','2024-11-11','confirm');

**#QUERIES#**

SELECT STATUS FROM orders WHERE order_id='90';

SELECT SUM(total) FROM orders WHERE order_id='90';

UPDATE address SET city = 'Bhopal' WHERE pincode = '452010';

UPDATE products SET product_description='puma-xxl' WHERE product_id='12';

SELECT * FROM products WHERE product_returnable = 'yes';

![ER DIAGRAM](https://github.com/user-attachments/assets/3cc6aba8-2813-4f66-8c69-2c7a93637efb)

