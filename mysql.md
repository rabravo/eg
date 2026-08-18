# mysql

start the MySQL server (macOS with Homebrew)

    brew services start mysql


stop the MySQL server

    brew services stop mysql


restart the MySQL server

    brew services restart mysql


start MySQL manually (Linux systemd)

    sudo systemctl start mysql


stop MySQL (Linux systemd)

    sudo systemctl stop mysql


log in as root

    mysql -u root -p


log in as a specific user to a specific database

    mysql -u username -p dbname


log in to a remote host

    mysql -h hostname -u username -p


list all databases

    SHOW DATABASES;


create a database

    CREATE DATABASE dbname;


drop a database

    DROP DATABASE dbname;


select a database to use

    USE dbname;


list tables in the current database

    SHOW TABLES;


describe a table's columns

    DESCRIBE tablename;


query all rows from a table

    SELECT * FROM tablename;


query with a filter and limit

    SELECT * FROM tablename WHERE column = 'value' LIMIT 10;


import a SQL dump into a database

    mysql -u username -p dbname < dump.sql


export a database to a SQL dump

    mysqldump -u username -p dbname > dump.sql


export all databases

    mysqldump -u username -p --all-databases > all_databases.sql


export a single table

    mysqldump -u username -p dbname tablename > table.sql


create a user and grant privileges

    CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
    GRANT ALL PRIVILEGES ON dbname.* TO 'username'@'localhost';
    FLUSH PRIVILEGES;


change a user's password

    ALTER USER 'username'@'localhost' IDENTIFIED BY 'newpassword';


show currently running queries

    SHOW PROCESSLIST;


check MySQL server status and version

    SHOW STATUS;
    SELECT VERSION();


exit the MySQL shell

    EXIT;

