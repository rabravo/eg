# redis-cli

start the Redis server (macOS with Homebrew)

    brew services start redis


stop the Redis server

    brew services stop redis


restart the Redis server

    brew services restart redis


start Redis (Linux systemd)

    sudo systemctl start redis


stop Redis (Linux systemd)

    sudo systemctl stop redis


connect to local Redis instance

    redis-cli


connect to a remote host

    redis-cli -h hostname -p 6379


connect with a password

    redis-cli -a password


ping the server to check connectivity

    PING


select a database (0-15, default is 0)

    SELECT 1


set a key

    SET mykey "myvalue"


get a key

    GET mykey


set a key with expiration in seconds

    SET mykey "myvalue" EX 3600


check time to live on a key

    TTL mykey


delete a key

    DEL mykey


check if a key exists

    EXISTS mykey


list all keys matching a pattern

    KEYS *
    KEYS user:*


get all key-value pairs matching a pattern

    SCAN 0 MATCH user:* COUNT 100


increment a numeric value

    INCR counter
    INCRBY counter 5


append to a list (left or right)

    LPUSH mylist "value"
    RPUSH mylist "value"


get a range of list elements

    LRANGE mylist 0 -1


add members to a set

    SADD myset "member1" "member2"


get all members of a set

    SMEMBERS myset


set a hash field

    HSET myhash field1 "value1"


get a hash field

    HGET myhash field1


get all fields and values in a hash

    HGETALL myhash


add to a sorted set with a score

    ZADD myzset 1.0 "member"


get members of a sorted set by rank

    ZRANGE myzset 0 -1 WITHSCORES


flush the current database

    FLUSHDB


flush all databases

    FLUSHALL


save the dataset to disk

    BGSAVE


show server info and stats

    INFO


show connected clients

    CLIENT LIST


monitor all commands in real time

    MONITOR


export data to an RDB dump (via config)

    CONFIG GET dir
    BGSAVE


exit redis-cli

    EXIT

