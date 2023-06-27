FROM node:20.3.1

# アプリ実行用のユーザを作成する
RUN useradd -m -r -U nodejs

# アプリ実行用のユーザのホームディレクトリにソースコードを置き所有権を渡す
WORKDIR /home/nodejs
COPY ./ /home/nodejs/
RUN chown nodejs -R /home/nodejs

# アプリ実行用ユーザに切り替えて、パッケージのインストールやビルドなどを行う
USER nodejs
RUN npm ci

# 3000番ポートを開ける
EXPOSE 3000

# アプリを実行する
ENTRYPOINT ["npm", "run", "start"]
