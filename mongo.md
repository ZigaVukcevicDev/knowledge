## Mongo
```
sudo service mongodb start
sudo service mongodb stop
sudo service mongodb restart

brew services start mongodb
brew services stop mongodb
```

## Client
```
mongo
```

### Showing databases (with at least one record)
```
show dbs
```

### Using specific database
```
use test
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
db.users.insert({"name" : "ziga"})
```

### Showing documents
```
db.users.find().pretty()
```
