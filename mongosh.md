# mongosh

start the MongoDB server (macOS with Homebrew)

    brew services start mongodb-community


stop the MongoDB server

    brew services stop mongodb-community


restart the MongoDB server

    brew services restart mongodb-community


start MongoDB (Linux systemd)

    sudo systemctl start mongod


stop MongoDB (Linux systemd)

    sudo systemctl stop mongod


connect to local MongoDB instance

    mongosh


connect to a specific database

    mongosh dbname


connect to a remote host

    mongosh "mongodb://hostname:27017/dbname"


connect with authentication

    mongosh "mongodb://username:password@hostname:27017/dbname"


list all databases

    show dbs


create or switch to a database

    use dbname


drop the current database

    db.dropDatabase()


list collections in the current database

    show collections


create a collection

    db.createCollection("collectionname")


drop a collection

    db.collectionname.drop()


insert a single document

    db.collectionname.insertOne({ key: "value" })


insert multiple documents

    db.collectionname.insertMany([{ key: "value1" }, { key: "value2" }])


query all documents in a collection

    db.collectionname.find()


query with a filter

    db.collectionname.find({ key: "value" })


query and pretty-print results

    db.collectionname.find().pretty()


limit results

    db.collectionname.find().limit(10)


update a single document

    db.collectionname.updateOne({ key: "value" }, { $set: { key: "newvalue" } })


update multiple documents

    db.collectionname.updateMany({ key: "value" }, { $set: { key: "newvalue" } })


delete a single document

    db.collectionname.deleteOne({ key: "value" })


delete multiple documents

    db.collectionname.deleteMany({ key: "value" })


count documents in a collection

    db.collectionname.countDocuments()


export a collection to JSON

    mongoexport --db dbname --collection collectionname --out export.json


import a JSON file into a collection

    mongoimport --db dbname --collection collectionname --file export.json


dump an entire database

    mongodump --db dbname --out ./dump


restore a database from a dump

    mongorestore --db dbname ./dump/dbname


create a user with read/write access

    db.createUser({ user: "username", pwd: "password", roles: [{ role: "readWrite", db: "dbname" }] })


show current database

    db


exit mongosh

    exit

