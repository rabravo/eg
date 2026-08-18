# sqlite3

open or create a database file

    sqlite3 mydb.db


open a database and run a single command

    sqlite3 mydb.db "SELECT * FROM tablename;"


open a database in read-only mode

    sqlite3 -readonly mydb.db


list all tables

    .tables


describe a table's schema

    .schema tablename


show all schemas

    .schema


turn on column headers in output

    .headers on


set output mode (column, csv, json, line, list, table)

    .mode column
    .mode csv


query all rows from a table

    SELECT * FROM tablename;


query with a filter and limit

    SELECT * FROM tablename WHERE column = 'value' LIMIT 10;


create a table

    CREATE TABLE tablename (id INTEGER PRIMARY KEY, name TEXT, value REAL);


insert a row

    INSERT INTO tablename (name, value) VALUES ('example', 3.14);


update a row

    UPDATE tablename SET value = 2.71 WHERE name = 'example';


delete a row

    DELETE FROM tablename WHERE name = 'example';


drop a table

    DROP TABLE tablename;


create an index

    CREATE INDEX idx_name ON tablename (column);


import a CSV file into a table

    .mode csv
    .import data.csv tablename


export a table to CSV

    .headers on
    .mode csv
    .output export.csv
    SELECT * FROM tablename;
    .output stdout


run SQL from a file

    .read script.sql


dump the entire database to SQL

    .dump


dump to a file

    .output dump.sql
    .dump
    .output stdout


restore from a SQL dump

    sqlite3 newdb.db < dump.sql


show database file info

    .dbinfo


show current settings

    .show


exit sqlite3

    .quit

