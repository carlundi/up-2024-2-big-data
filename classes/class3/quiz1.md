Write an SQL statement to create a table with these characteristics:
- table name: car_models
- columns: model_name, year, doors (int), color, brand
- primary key called "id", integer
- don't allow null in any of the columns
- add a "created_at" column as a "timestamp"

CREATE TABLE car_models (
    id INTEGER PRIMARY KEY,
    model_name TEXT NOT NULL,
    year INTEGER NOT NULL,
    doors INTEGER NOT NULL,
    color TEXT NOT NULL,
    brand TEXT NOT NULL,
    created_at TIMESTAMP NOT NULL
);

Write an SQL statement to get the average "price" of products that were launched on 2022. Use this table as reference:

CREATE TABLE products (
  id INTEGER,
  title TEXT,
  sku TEXT,
  stock INTEGER,
  price DECIMAL,
  launched_on DATE, -- e.g. '2020-05-15'
);

SELECT AVG(price) AS average_price
FROM products
WHERE launched_on >= '2022-01-01' AND launched_on <= '2022-12-31';
