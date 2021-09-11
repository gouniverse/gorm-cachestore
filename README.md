# Cache Store using GORM

DEPRECATED. The new library does not use GORM any more and can be found here: https://github.com/gouniverse/cachestore

Cache messages to a database table using GORM.

## Installation
```
go get -u github.com/gouniverse/cachestore
```

## Setup

```
cacheStore = cachestore.NewStore(cachestore.WithGormDb(databaseInstance), cachestore.WithTableName("my_cache"))

go cacheStore.ExpireCacheGoroutine()
```

## Usage

- Set value to cache with expiration
```
isSaved := cacheStore.Set("token", "ABCDEFGHIJKLMNOPQRSTVUXYZ", 60*60) // 1 hour
if isSaved == false {
		log.Println("Saving failed")
		return
}
```

- Get value from cache with default if not found
```
token := cacheStore.Get("token", "")
```
