# MongoDB Shell

- [MongoDB Shell](#mongodb-shell)
  - [접속](#접속)
  - [DB 지정](#db-지정)
  - [Collection 생성](#collection-생성)
  - [Collection 확인](#collection-확인)
  - [Collection 삭제](#collection-삭제)
  - [Document 추가](#document-추가)
  - [Document 삭제](#document-삭제)

## 접속

```sh
sudo docker exec -it mongo mongo --username mark --password 22636d16a3f0db19e9 --authenticationDatabase admin
```

```sh
use admin
db.getUser('root')
```

## DB 지정

```sh
use mydb
```

## Collection 생성

```javascript
db.createCollection('first_collection')
```

## Collection 확인

```javascript
db.getCollectionNames()
// [ 'first_collection', 'delete_me' ]
db.first_collection.find()
```

```javascript
// 한줄로 하면
db.getCollectionNames().forEach(collection => {
  print(`Collection: ${collection}`);
  db[collection].find().forEach(printjson);
});
```

## Collection 삭제

```javascript
// 모든 컬렉션 지우기
db.getCollectionNames().forEach(collection => {
  db[collection].drop();
});
```

## Document 추가

```javascript
db.first_collection.insertMany([
  { name: 'A', age: 10 },
  { name: 'B', age: 20 },
  { name: 'C', age: 30 },
  { name: 'D', age: 40 },
  { name: 'E', age: 50 },
  { name: 'F', age: 60 },
  { name: 'G', age: 70 },
]);
```

## Document 삭제

```javascript
// 특정 컬렉션의 전체 문서 지우기
db.first_collection.deleteMany({});
// { acknowledged: true, deletedCount: 7 }
```
