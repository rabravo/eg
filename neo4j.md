# neo4j

install Neo4j (macOS with Homebrew)

    brew install neo4j


start the Neo4j server

    brew services start neo4j


stop the Neo4j server

    brew services stop neo4j


restart the Neo4j server

    brew services restart neo4j


start Neo4j in the foreground (non-service mode)

    neo4j start


stop Neo4j (non-service mode)

    neo4j stop


check Neo4j server status

    neo4j status


open the Neo4j browser UI (default port 7474)

    open http://localhost:7474


connect to Neo4j with cypher-shell (prompts for credentials)

    cypher-shell


connect with username and password

    cypher-shell -u neo4j -p password


connect to a remote instance

    cypher-shell -a bolt://hostname:7687 -u neo4j -p password


check the Neo4j version

    CALL dbms.components() YIELD name, versions RETURN name, versions;


list all databases

    SHOW DATABASES;


create a database

    CREATE DATABASE dbname;


drop a database

    DROP DATABASE dbname;


switch to a database (cypher-shell)

    :use dbname


create a node with a label and properties

    CREATE (n:Person { name: 'Alice', age: 30 });


create a relationship between two nodes

    MATCH (a:Person { name: 'Alice' }), (b:Person { name: 'Bob' })
    CREATE (a)-[:KNOWS]->(b);


find all nodes with a label

    MATCH (n:Person) RETURN n;


find a node by property

    MATCH (n:Person { name: 'Alice' }) RETURN n;


find nodes with a filter and limit

    MATCH (n:Person) WHERE n.age > 25 RETURN n LIMIT 10;


find all relationships of a type

    MATCH ()-[r:KNOWS]->() RETURN r;


find neighbors of a node

    MATCH (n:Person { name: 'Alice' })-[:KNOWS]->(neighbor) RETURN neighbor;


update a node property

    MATCH (n:Person { name: 'Alice' }) SET n.age = 31;


add a new property to a node

    MATCH (n:Person { name: 'Alice' }) SET n.email = 'alice@example.com';


remove a property from a node

    MATCH (n:Person { name: 'Alice' }) REMOVE n.email;


delete a node (must have no relationships)

    MATCH (n:Person { name: 'Alice' }) DELETE n;


delete a node and all its relationships

    MATCH (n:Person { name: 'Alice' }) DETACH DELETE n;


delete all nodes and relationships in the database

    MATCH (n) DETACH DELETE n;


count all nodes

    MATCH (n) RETURN count(n);


count nodes with a label

    MATCH (n:Person) RETURN count(n);


create an index on a label property

    CREATE INDEX FOR (n:Person) ON (n.name);


list all indexes

    SHOW INDEXES;


drop an index

    DROP INDEX index_name;


create a uniqueness constraint

    CREATE CONSTRAINT FOR (n:Person) REQUIRE n.email IS UNIQUE;


list all constraints

    SHOW CONSTRAINTS;


export the database (admin dump)

    neo4j-admin database dump dbname --to-path=/path/to/backup/


import/restore a database dump

    neo4j-admin database load dbname --from-path=/path/to/backup/ --overwrite-destination=true


exit cypher-shell

    :exit

