# postgis

PostGIS is a spatial extension for PostgreSQL that adds support for
geographic objects, coordinate systems, and spatial queries.

install PostGIS on Ubuntu

    sudo apt-get install -y postgis postgresql-9.3-postgis-2.1


install PostGIS on macOS with Homebrew

    brew install postgis


check the GEOS library version (geometry engine used by PostGIS)

    geos-config --version


check the GDAL version (raster/vector data library used by PostGIS)

    gdal-config --version


enable PostGIS in a database (run as superuser inside psql)

    CREATE EXTENSION postgis;


enable additional PostGIS extensions

    CREATE EXTENSION postgis_topology;
    CREATE EXTENSION fuzzystrmatch;
    CREATE EXTENSION postgis_tiger_geocoder;


enable all at once on a named database from the shell

    sudo -u postgres psql -c "CREATE EXTENSION postgis; CREATE EXTENSION postgis_topology; CREATE EXTENSION fuzzystrmatch; CREATE EXTENSION postgis_tiger_geocoder;" dbname


verify PostGIS is installed

    \dx


check PostGIS version

    SELECT PostGIS_version();
    SELECT PostGIS_Full_Version();


get the SRID of a geometry column in a table

    SELECT Find_SRID('public', 'tablename', 'geom');


list all geometry columns in the database

    SELECT * FROM geometry_columns;


list all spatial reference systems

    SELECT srid, srtext FROM spatial_ref_sys LIMIT 10;


add a geometry column to an existing table

    SELECT AddGeometryColumn('public', 'tablename', 'geom', 4326, 'POINT', 2);


create a table with a geometry column

    CREATE TABLE locations (
      id serial PRIMARY KEY,
      name text,
      geom geometry(Point, 4326)
    );


insert a point (longitude, latitude)

    INSERT INTO locations (name, geom)
    VALUES ('Campus', ST_SetSRID(ST_MakePoint(-83.0, 42.6), 4326));


insert a point from WKT

    INSERT INTO locations (name, geom)
    VALUES ('Campus', ST_GeomFromText('POINT(-83.0 42.6)', 4326));


get coordinates of a point

    SELECT ST_X(geom) AS lon, ST_Y(geom) AS lat FROM locations;


get the WKT representation of a geometry

    SELECT ST_AsText(geom) FROM locations;


get the GeoJSON representation of a geometry

    SELECT ST_AsGeoJSON(geom) FROM locations;


calculate distance between two points in meters (geography type)

    SELECT ST_Distance(
      ST_GeogFromText('POINT(-83.0 42.6)'),
      ST_GeogFromText('POINT(-84.0 43.0)')
    );


find all rows within a distance (meters) of a point

    SELECT * FROM locations
    WHERE ST_DWithin(
      geom::geography,
      ST_GeogFromText('POINT(-83.0 42.6)'),
      1000
    );


reproject geometry to a different SRID

    SELECT ST_Transform(geom, 3857) FROM locations;


compute the centroid of a polygon

    SELECT ST_Centroid(geom) FROM polygons;


compute the area of a polygon (in SRID units)

    SELECT ST_Area(geom) FROM polygons;


compute the area in square meters (cast to geography)

    SELECT ST_Area(geom::geography) FROM polygons;


compute the convex hull of a set of geometries

    SELECT ST_ConvexHull(ST_Union(geom)) FROM locations;


buffer a geometry by a distance (in SRID units)

    SELECT ST_Buffer(geom, 500) FROM locations;


check if two geometries intersect

    SELECT ST_Intersects(a.geom, b.geom) FROM table1 a, table2 b WHERE a.id = 1 AND b.id = 2;


clip geometry to an intersecting geometry

    SELECT ST_Intersection(a.geom, b.geom) FROM table1 a, table2 b;


create a spatial index on a geometry column

    CREATE INDEX idx_locations_geom ON locations USING GIST (geom);


import a shapefile into PostGIS with shp2pgsql

    shp2pgsql -s 4326 -W UTF-8 input.shp tablename dbname > output.sql
    psql -d dbname -p 5432 -f output.sql


import shapefile and pipe directly into the database (no intermediate file)

    shp2pgsql -s 4326 -W UTF-8 input.shp tablename | psql -d dbname -U username


export a PostGIS table to a shapefile with pgsql2shp

    pgsql2shp -f /path/to/output -h localhost -u username dbname tablename


export a PostGIS query result to a shapefile

    pgsql2shp -f /path/to/output -h localhost -u username dbname "SELECT * FROM tablename WHERE condition"

