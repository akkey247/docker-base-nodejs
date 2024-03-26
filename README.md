# 使い方

## 起動

### コンテナのビルド＆起動

```
$ docker-compose up -d --build
```

### コンテナに入る

```
$ docker-compose exec app bash
```

### コンテナに停止

```
$ docker-compose down
```

## 各種インストール

※ WSL環境でコンテナを立ち上げた場合パーミッションの設定も必要になる。  

### Remix

#### インストール

```
$ docker-compose exec app pnpm dlx create-remix@latest .
$ docker-compose exec app pnpm dlx create-remix@latest . --template remix-run/remix/templates/remix
```

インストール後、 `package.json` の記述を `"dev": "remix vite:dev --host --port 3000",` に変更する必要がある。  

#### 起動

```
$ docker-compose exec app pnpm run dev
```

### Storybook インストール

```
$ docker-compose exec storybook pnpm dlx storybook@latest init
```

インストール直後にビルトインサーバーが起動してアクセスできるようになる。  
以降、起動するときは `docker-compose exec storybook pnpm run storybook` を使う。  

### 5. サイトにアクセスする

[サイト]
http://localhost:3000/

[Storybook]
http://localhost:6006/

[PhpMyAdmin]
http://localhost:8080/

[mailhog]
http://localhost:8025/

## その他

### コンテナを停止＆イメージ削除

```
$ docker-compose down --rmi all --volumes
```

### コンテナの中身のデータを削除(ソース・DB)

```
$ docker-compose exec app clear-data
```
