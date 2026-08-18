# typedb

install TypeDB (macOS with Homebrew — not recommended on Apple Silicon)

    brew install typedb


install TypeDB on Apple Silicon (download directly from typedb.com and unzip)

    cd typedb-all-mac-<version>
    ./typedb server


start the TypeDB server (foreground; stop with Ctrl+C)

    ./typedb server


start as a background service (Homebrew install only)

    brew services start typedb


stop the background service

    brew services stop typedb


open the TypeDB console (in a separate terminal, same directory)

    ./typedb console


connect to a remote server from the console

    ./typedb console --server=hostname:1729


set Java 11 as active JVM when TypeDB refuses to start with a newer JDK

    export JAVA_HOME=$(/usr/libexec/java_home -v 11)


list available Java versions on macOS

    /usr/libexec/java_home -V


install the TypeDB Python client (version must match the server)

    pip3 install typedb-client==2.x.x


create a database (TypeDB console)

    database create mydb


list all databases

    database list


delete a database

    database delete mydb


open a session and start a schema transaction

    transaction mydb schema write


open a session and start a data transaction

    transaction mydb data write


define a schema (inside a schema write transaction)

    define
      person sub entity,
        owns name,
        owns age,
        plays friendship:friend;
      name sub attribute, value string;
      age sub attribute, value long;
      friendship sub relation,
        relates friend;


commit a transaction

    commit


rollback a transaction

    rollback


close the current transaction without committing

    close


insert a data instance (inside a data write transaction)

    insert $p isa person, has name "Alice", has age 30;


insert a relation

    match
      $a isa person, has name "Alice";
      $b isa person, has name "Bob";
    insert (friend: $a, friend: $b) isa friendship;


query all instances of a type (data read transaction)

    transaction mydb data read
    match $p isa person; get $p;


query with attribute filter

    match $p isa person, has name $n, has age $a; $a > 25; get $p, $n, $a;


delete an instance

    match $p isa person, has name "Alice";
    delete $p isa person;


undefine a schema element

    undefine person owns age;


run a TypeQL file from the console

    source /path/to/schema.tql


exit the TypeDB console

    exit

