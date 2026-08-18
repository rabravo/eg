# plr

PL/R is a PostgreSQL procedural language extension that lets you write
database functions in R. Functions run inside the PostgreSQL server process
and have full access to R libraries.

install PL/R on Ubuntu alongside PostgreSQL and PostGIS

    sudo apt-get install -y postgresql-9.3-plr


enable the PL/R extension in a database (run as superuser)

    CREATE EXTENSION plr;


verify PL/R is installed

    \dx


create a simple PL/R function that returns a value

    CREATE OR REPLACE FUNCTION r_mean(vals float8[]) RETURNS float8 AS '
      mean(vals)
    ' LANGUAGE plr;


call a PL/R function from SQL

    SELECT r_mean(ARRAY[1.0, 2.0, 3.0, 4.0]);


create a PL/R function that queries the database with pg.spi.exec

    CREATE OR REPLACE FUNCTION r_row_count(tbl text) RETURNS int AS '
      res <- pg.spi.exec(sprintf("SELECT count(*) AS n FROM %s", tbl))
      as.integer(res$n)
    ' LANGUAGE plr;


create a set-returning PL/R function (returns a table)

    CREATE OR REPLACE FUNCTION r_squared(n int) RETURNS SETOF float8 AS '
      (1:n)^2
    ' LANGUAGE plr;


use sprintf inside PL/R to build dynamic queries

    CREATE OR REPLACE FUNCTION r_col_stats(tbl text, col text)
    RETURNS float8 AS '
      res <- pg.spi.exec(
        sprintf("SELECT %s AS val FROM %s", arg2, arg1)
      )
      mean(res$val)
    ' LANGUAGE plr;


create a Voronoi diagram function using PL/R and the deldir R library
# requires: R package deldir, PostGIS geometry type

    CREATE TYPE voronoi AS (id integer, polygon geometry);

    CREATE OR REPLACE FUNCTION r_voronoi(text, text, text)
    RETURNS SETOF voronoi AS '
      library(deldir)
      points <- pg.spi.exec(
        sprintf("SELECT ST_X(%2$s) AS x, ST_Y(%2$s) AS y FROM %1$s;", arg1, arg2)
      )
      buffer_distance = (
        (abs(max(points$x) - min(points$x)) +
         abs(max(points$y) - min(points$y))) / 2
      ) * 0.50
      buffer_set <- pg.spi.exec(
        sprintf("SELECT ST_Buffer(ST_Convexhull(ST_Union(%2$s)),%3$.6f) AS ewkb FROM %1$s;",
                arg1, arg2, buffer_distance)
      )
      voro = deldir(points$x, points$y, digits=22, frac=1e-25,
        list(ndx=2, ndy=2),
        rw=c(min(points$x) - abs(min(points$x) - max(points$x)),
             max(points$x) + abs(min(points$x) - max(points$x)),
             min(points$y) - abs(min(points$y) - max(points$y)),
             max(points$y) + abs(min(points$y) - max(points$y))))
      tiles = tile.list(voro)
      # build WKT polygons and return as voronoi type
    ' LANGUAGE plr;


call the Voronoi function and store results in a new table

    WITH output AS (
      SELECT * FROM r_voronoi('tablename', 'geom', 'id')
    )
    SELECT * INTO newtable FROM output;


install an R package from within PostgreSQL (runs as the postgres system user)

    CREATE OR REPLACE FUNCTION r_install(pkg text) RETURNS void AS '
      install.packages(pkg, repos="https://cloud.r-project.org")
    ' LANGUAGE plr;

    SELECT r_install('deldir');


check R version running inside PostgreSQL

    CREATE OR REPLACE FUNCTION r_version() RETURNS text AS '
      paste(R.version$major, R.version$minor, sep=".")
    ' LANGUAGE plr;

    SELECT r_version();


drop the PL/R extension

    DROP EXTENSION plr;

