Answer 1 = Relationship between "Product" and "Product_Category":
The relationship between "Product" and "Product_Category" is most likely a foreign key relationship. In the "Product" entity, there is a column named category_id which is an integer type. This column likely serves as a foreign key referencing the id column in the "Product_Category" entity. This establishes a link between each product and its corresponding category.

Answer 2 = Ensuring each product has a valid category:
To ensure that each product in the "Product" table has a valid category assigned to it, you can set up a foreign key constraint between the category_id column in the "Product" table and the id column in the "Product_Category" table. This constraint will enforce referential integrity, meaning that every value in the category_id column of the "Product" table must exist in the id column of the "Product_Category" table. This ensures that each product is associated with a valid category.

Here's an example SQL statement to create the foreign key constraint:
ALTER TABLE Product
ADD CONSTRAINT fk_product_category
FOREIGN KEY (category_id)
REFERENCES Product_Category(id);

Answer 3 = Schema (using SQL for PostgreSQL):

-- Product table
CREATE TABLE Product (
    id SERIAL PRIMARY KEY,
    name VARCHAR,
    desc TEXT,
    SKU VARCHAR,
    category_id INT REFERENCES Product_Category(id),
    inventory_id INT REFERENCES Product_inventory(id),
    price DECIMAL,
    discount_id INT REFERENCES discount(id),
    createted_at TIMESTAMP,
    modified_at TIMESTAMP,
    deleted_at TIMESTAMP
);

-- Product_Category table
CREATE TABLE Product_Category (
    id SERIAL PRIMARY KEY,
    name VARCHAR,
    createted_at TIMESTAMP,
    modified_at TIMESTAMP,
    deleted_at TIMESTAMP
);

-- Product_inventory table
CREATE TABLE Product_inventory (
    id SERIAL PRIMARY KEY,
    quantity INT,
    createted_at TIMESTAMP,
    modified_at TIMESTAMP,
    deleted_at TIMESTAMP
);

-- discount table
CREATE TABLE discount (
    id SERIAL PRIMARY KEY,
    name VARCHAR,
    desc TEXT,
    discount_percent DECIMAL,
    active BOOLEAN,
    createted_at TIMESTAMP,
    modified_at TIMESTAMP,
    deleted_at TIMESTAMP
);


