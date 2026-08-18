# orientdb

install OrientDB (macOS with Homebrew)

    brew install orientdb


start the OrientDB server

    orientdb start


stop the OrientDB server

    orientdb stop


start as a background service (Homebrew)

    brew services start orientdb


stop the background service

    brew services stop orientdb


check server status

    orientdb status


open the OrientDB console

    orientdb console


connect to a local database as admin

    connect remote:localhost/dbname admin admin


connect to a remote server

    connect remote:hostname/dbname username password


create a database (console)

    create database remote:localhost/dbname admin admin plocal


list all databases

    list databases


open an existing database

    open remote:localhost/dbname admin admin


close the current database connection

    close


drop a database

    drop database remote:localhost/dbname admin admin


create a class (equivalent to a table or node type)

    create class Person


create a class that extends another (inheritance)

    create class Employee extends Person


list all classes

    list classes


create a property on a class

    create property Person.name STRING
    create property Person.age INTEGER


insert a record

    insert into Person (name, age) set name = 'Alice', age = 30


query all records of a class

    select * from Person


query with a filter

    select * from Person where age > 25


query with a limit

    select * from Person limit 10


update a record

    update Person set age = 31 where name = 'Alice'


delete a record

    delete from Person where name = 'Alice'


create a vertex (graph mode)

    create vertex Person set name = 'Alice', age = 30


create an edge between two vertices

    create edge Knows from (select from Person where name = 'Alice') to (select from Person where name = 'Bob')


traverse relationships from a vertex

    traverse out('Knows') from (select from Person where name = 'Alice')


count records in a class

    select count(*) from Person


create an index on a property

    create index Person.name on Person (name) unique


list indexes

    list indexes


drop an index

    drop index Person.name


export a database to a gzip archive

    export database /path/to/export.gz


import a database from an export archive

    import database /path/to/export.gz


check OrientDB version (console)

    info


exit the OrientDB console

    exit

