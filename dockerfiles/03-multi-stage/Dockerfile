FROM node:20.3.1-alpine3.18 AS base

# アプリ実行用のユーザを作成する
RUN adduser -D -g nodejs nodejs

# アプリ実行用のユーザのホームディレクトリにソースコードを置き所有権を渡す
WORKDIR /home/nodejs

FROM base AS builder
# アプリの実行・ビルドに必要なファイルのみコンテナに持ち込む
COPY ./package.json /home/nodejs/
COPY ./package-lock.json /home/nodejs/
COPY ./src /home/nodejs/
RUN chown nodejs -R /home/nodejs

# アプリ実行用ユーザに切り替えて、パッケージのインストールやビルドなどを行う
USER nodejs
RUN npm ci

FROM builder AS runner
# ビルド用のステージからビルド結果を持ってくる
COPY --from=builder /home/nodejs/ /home/nodejs

# 3000番ポートを開ける
EXPOSE 3000

# アプリを実行する
ENTRYPOINT ["npm", "run", "start"]
