## Mongo

Running services

```
sudo service mongodb start
sudo service mongodb stop
sudo service mongodb restart
```

or

```
brew services start mongodb
brew services stop mongodb
```

## Client

Run client

```
mongo
```

### Showing databases (with at least one record)
```
show dbs
```

### Using specific database
```
use myDatabase
```

### Showing collections
```
show collections
```

### Create collection
```
db.createCollection("users", { autoIndexID : true })
```

### Insert document
```
db.users.insert({"name" : "John"})
```

### Showing documents
```
db.users.find().pretty()
```
