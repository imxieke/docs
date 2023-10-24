# Redis
String
```
set name val
get name
get *
```

Hash
```
hmset name1 val1 name2 val2 
hget name1 
```

List
```
lpush name val
lrange name start->end (0 3)
```

Set
```
sadd name val
smembers name
```

Sorted Set
```
zset name number(0) val
zrangebyscore name start->end (0 3)
```