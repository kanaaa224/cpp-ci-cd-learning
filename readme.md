実行
```
$ docker compose up -d
```

Webブラウザで
```
http://localhost:8080
```

初期パスワード取得
```
$ docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

コンテナ停止
```
$ docker compose down
```

コンテナ削除
```
$ docker compose down -v
```

ソースのビルド、実行
```
$ docker run --rm -v ${PWD}:/workspace -w /workspace gcc:13 bash -c 'mkdir -p build && for f in source/*/main.cpp; do name=$(basename $(dirname "$f")); g++ "$f" -o build/"$name" && ./build/"$name"; done'
```