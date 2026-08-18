# hstore

hstore is a PostgreSQL extension for storing key-value pairs in a single
column. Keys and values are text strings. Useful for semi-structured or
sparse attributes without needing a full JSON column.

enable the hstore extension in a database

    CREATE EXTENSION hstore;


verify it is installed

    \dx


create a table with an hstore column

    CREATE TABLE products (
      id serial PRIMARY KEY,
      name varchar,
      attributes hstore
    );


insert a row with hstore data

    INSERT INTO products (name, attributes) VALUES (
      'Geek Love',
      'author => "Katherine Dunn", pages => 368, category => fiction'
    );


insert using the hstore() constructor from arrays

    INSERT INTO products (name, attributes) VALUES (
      'Dune',
      hstore(ARRAY['author','pages','category'], ARRAY['Frank Herbert','412','sci-fi'])
    );


cast a literal string to hstore

    SELECT 'a=>1, b=>2'::hstore;


get a single value by key (returns text, NULL if key absent)

    SELECT attributes -> 'author' FROM products;


get a value by key with alias

    SELECT name, attributes -> 'author' AS author FROM products;


filter rows by a key's value

    SELECT name FROM products WHERE attributes -> 'category' = 'fiction';


check if a key exists in an hstore

    SELECT name FROM products WHERE attributes ? 'pages';


check if all of several keys exist

    SELECT name FROM products WHERE attributes ?& ARRAY['author', 'pages'];


check if any of several keys exist

    SELECT name FROM products WHERE attributes ?| ARRAY['isbn', 'pages'];


check if an hstore contains a sub-hstore (key-value subset)

    SELECT name FROM products WHERE attributes @> 'category => fiction';


get all keys of an hstore column

    SELECT akeys(attributes) FROM products;


get all values of an hstore column

    SELECT avals(attributes) FROM products;


get keys and values as separate arrays

    SELECT skeys(attributes), svals(attributes) FROM products;


expand an hstore into rows of (key, value) pairs

    SELECT name, (each(attributes)).* FROM products;


expand an hstore into a table with named columns using crosstab (alternative)

    SELECT name, key, value FROM products, each(attributes);


add or update a key in an hstore column

    UPDATE products SET attributes = attributes || 'in_stock => true' WHERE name = 'Dune';


delete a key from an hstore column

    UPDATE products SET attributes = delete(attributes, 'in_stock') WHERE name = 'Dune';


delete multiple keys at once

    UPDATE products SET attributes = delete(attributes, ARRAY['in_stock', 'pages']);


merge two hstore values (right side wins on duplicate keys)

    SELECT 'a=>1, b=>2'::hstore || 'b=>99, c=>3'::hstore;


convert an hstore to a JSON object

    SELECT hstore_to_json(attributes) FROM products;


convert an hstore to a JSON object (loose — numbers and booleans unquoted)

    SELECT hstore_to_json_loose(attributes) FROM products;


build an hstore from a JSON object

    SELECT hstore(json_object(ARRAY['author','pages'], ARRAY['Orwell','328']));


count how many keys an hstore has

    SELECT cardinality(akeys(attributes)) FROM products;


create an index on an hstore column (GIN for key/value lookups)

    CREATE INDEX idx_products_attributes ON products USING GIN (attributes);


create a GiST index (supports containment operators @> and <@)

    CREATE INDEX idx_products_attributes_gist ON products USING GIST (attributes);


find rows where hstore contains a specific key-value pair (uses index)

    SELECT * FROM products WHERE attributes @> 'category => fiction'::hstore;


aggregate multiple hstore values into one (merging all rows)

    SELECT hstore_agg(attributes) FROM products;

