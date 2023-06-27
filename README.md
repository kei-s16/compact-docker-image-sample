## これはなにか
軽量なDockerfileを作っていくデモ  

## やってみよう
下記のコマンドに従ってイメージを作りつつ、  

- `docker images` コマンドを使ってイメージのサイズを比較したり
- ビルド時間を計測したり

して遊んでください  

### とりあえず動くやつ
```zsh
% docker buildx build -f ./dockerfiles/01-plain/Dockerfile -t hono-example:plain .
% docker run -it -p 3000:3000 hono-example:plain
```

### ベースイメージをAlpineにしたやつ
```zsh
% docker buildx build -f ./dockerfiles/02-alpine/Dockerfile -t hono-example:alpine .
% docker run -it -p 3000:3000 hono-example:alpine
```

### マルチステージビルドにしたやつ
```zsh
% docker buildx build -f ./dockerfiles/03-multi-stage/Dockerfile -t hono-example:multi .
% docker run -it -p 3000:3000 hono-example:multi
```

## コンテナの動作チェック
```zsh
% curl http://localhost:3000
Hello Hono!
```
