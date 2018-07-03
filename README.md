# docker-compose-mongodb

## MongoDB用ネットワーク作成
```
docker network create mongodb
```

## 起動
```
docker-compose up -d
```

## mongoに接続
```
mongo 127.0.0.1:27017
```

## レプリカセットの設定を流し込み
```
config =
{
     "_id" : "my-mongo-set",
     "members" : [
          {
               "_id" : 0,
               "host" : "mongodb01:27017"
          },
          {
               "_id" : 1,
               "host" : "mongodb02:27017"
          },
          {
               "_id" : 2,
               "host" : "mongodb03:27017",
               "arbiterOnly" : true
          }
     ]
}
```

## レプリカセットの設定を有効化
```
rs.initiate(config);
```

## レプリカセットの状態を確認
```
rs.status()
```

## 停止
```
docker-compose stop
```

## 削除
```
docker-compose rm
```

## ネットワーク設定削除
```
docker network rm mongodb
```

