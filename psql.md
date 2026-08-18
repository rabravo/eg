# psql

start the PostgreSQL server (macOS with Homebrew)

    brew services start postgresql


stop the PostgreSQL server

    brew services stop postgresql


restart the PostgreSQL server

    brew services restart postgresql


start PostgreSQL (Linux systemd)

    sudo systemctl start postgresql


stop PostgreSQL (Linux systemd)

    sudo systemctl stop postgresql


log in as the default superuser

    psql -U postgres


log in to a specific database

    psql -U username -d dbname


log in to a remote host

    psql -h hostname -U username -d dbname


log in specifying a non-default port

    psql -d dbname -h hostname -p 5433 -U username


list all databases (with ownership, encoding, access privileges)

    \l


list all databases from the shell (with owner and encoding info)

    psql -h localhost -U postgres --list


create a database

    CREATE DATABASE dbname;


create a database with an owner assigned

    sudo -u postgres psql -c "CREATE DATABASE dbname OWNER username;"


drop a database

    DROP DATABASE dbname;


drop a database from the shell

    dropdb -h localhost -p 5432 -i -e dbname


connect to a different database within psql

    \c dbname


list tables in the current database

    \dt


describe a table's columns

    \d tablename


query all rows from a table

    SELECT * FROM tablename;


query with a filter and limit

    SELECT * FROM tablename WHERE column = 'value' LIMIT 10;


import a SQL file into a database

    psql -U username -d dbname -f dump.sql


export a database to a SQL dump

    pg_dump -U username dbname > dump.sql


export all databases

    pg_dumpall -U postgres > all_databases.sql


export a single table

    pg_dump -U username -d dbname -t tablename > table.sql


restore from a dump file

    pg_restore -U username -d dbname dump.dump


create a user (interactive password prompt)

    sudo -u postgres createuser -P username


create a user via psql

    sudo -u postgres psql -c "CREATE USER username;"


set or change a user's password

    ALTER ROLE username WITH PASSWORD 'newpassword';


grant all privileges on a database to a user

    sudo -u postgres psql -c "GRANT ALL PRIVILEGES ON DATABASE dbname TO username;"


elevate a user to superuser

    sudo -u postgres psql -c "ALTER ROLE username SUPERUSER;"


change ownership of all tables in a schema to a new owner (shell loop)

    for tbl in $(psql -qAt -c "SELECT tablename FROM pg_tables WHERE schemaname='public';" dbname); do \
        psql -c "ALTER TABLE \"${tbl}\" OWNER TO newowner" dbname; done


check which users are connected

    SELECT * FROM pg_user;


disconnect all connections from the current database

    SELECT pg_terminate_backend(pg_stat_activity.pid)
    FROM pg_stat_activity
    WHERE datname = current_database()
      AND pid <> pg_backend_pid();


show active connections

    SELECT pid, usename, datname, state FROM pg_stat_activity;


check installed extensions

    \dx


get column names of a table

    SELECT column_name FROM information_schema.columns WHERE table_name = 'tablename';


count rows in a table

    SELECT count(*) FROM tablename;


check PostgreSQL version

    SELECT version();


show current database

    SELECT current_database();


show client and server encoding

    SHOW client_encoding;
    SHOW server_encoding;


import CSV into a table (server-side, requires superuser)

    COPY tablename FROM '/path/to/file.csv' DELIMITER ',' CSV HEADER;


import CSV into a table (client-side, works as any user)

    \copy tablename FROM '/path/to/file.csv' DELIMITER AS ',';


export a table to CSV

    psql -U postgres -d dbname -c "COPY tablename TO stdout DELIMITER ',' CSV HEADER;" > /path/to/file.csv


backup a database with pg_dump (custom format, UTF-8, verbose)

    pg_dump dbname -p 5432 --format custom --blobs -E UTF-8 --verbose --file=/path/to/backup


backup using the full path to pg_dump when versions differ between client and server

    /path/to/correct/version/pg_dump -d dbname --format custom --blobs --encoding UTF8 --verbose --file=/path/to/backup


restore a database from a pg_dump backup

    sudo -u postgres createdb mydb
    pg_restore --clean --no-acl --dbname=mydb /path/to/backup


copy a table from one server to another (requires passwordless SSH to remote)

    pg_dump -h localhost -U username -p 5432 -C -t tablename dbname | \
        ssh -C user@remote.host "psql -h localhost -U dbuser -p 5432 dbname"


import a shapefile into PostGIS using shp2pgsql
# shp2pgsql converts ESRI shapefiles to SQL for loading into a PostGIS-enabled database;
# -s sets the SRID (coordinate system), -W sets the encoding of the source file

    shp2pgsql -s <SRID> -W <Encoding> shapefile.shp tablename dbname > output.sql


example: import a Census TIGER tract shapefile (SRID 4269, NAD83)

    shp2pgsql -s 4269 -W UTF-8 tl_2010_48113_tract10.shp tl_2010_48113_tract10 us_gisdb > tl_2010_48113_tract10.sql
    psql -d us_gisdb -p 5432 -f tl_2010_48113_tract10.sql


import shapefile SQL with error stopping enabled (useful for debugging)

    psql -d us_gisdb -p 5432 --set=ON_ERROR_STOP=on -f tl_2010_48113_tract10.sql


show psql help

    \?


exit psql

    \q

