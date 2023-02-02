## 環境構築手順 / Instruction

イメージのビルド
```
docker-compose build
```

コンテナのビルド→create-next-app実行
```
docker-compose run --rm app npx create-next-app tmp \
&& mv tmp/* . && mv tmp/.* . && rm -r tmp
```
展開用のディレクトリにルートを指定すると、Dockerfileとdocker-compose.ymlによりコンフリクトが発生するため、一時的にtmpディレクトリに作成し、その後ルートへ展開させる。
(ルートに展開しないと、package.jsonがルートディレクトリに無い旨のエラーにより、ホスティングサービスへのデプロイが失敗するというケースがあるらしい)  

上記コマンド実行後、以下のように質問されるので、自身のプロジェクトに応じた回答をする。
```
Would you like to use TypeScript with this project? … No / Yes
Would you like to use ESLint with this project? … No / Yes
Would you like to use `src/` directory with this project? … No / Yes
Would you like to use experimental `app/` directory with this project? … No / Yes
What import alias would you like configured? … @/*
```

コンテナ起動
```
docker-compose up
```

## 動作確認
http://localhost:3000  
Next.jsの初期画面が表示されればOK!