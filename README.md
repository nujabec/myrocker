# nujabec/myrocker

## 概要

- R 4.3.2
- RstudioServer(Enabel GitHub Copilot)
- オフライン環境で使うケースも想定し大量のパッケージをinstall済み

## 使い方

```bash
# renvのcache用にvolume作成(初回のみ)
docker volume create renv

# イメージの作成
docker-compose build 

# コンテナの起動
docker-compose up -d
```

## コンテナを複数台起動する場合

```bash
docker compose up -d --scale rstudio=10
```
 
# push方法

```bash
docker push nujabec/myrocker:20231110
```

## オフライン環境にdocker imageを持っていく方法

```bash
# オンライン端末でイメージを作成
# docker imageをtarファイルに変換
docker save nujabec/myrocker:20231110 > myrocker_20231110.tar
docker save nujabec/myrocker:20231116 > myrocker_20231116.tar
# オフライン端末で、tarファイルからdocker imageを読む
docker load < myrocker_20231110.tar
docker load < myrocker_20231116.tar
```
## sqlserverのODBCdriverを追加

参考
- https://qiita.com/miraijin/items/0c7bfbd70234967e87bd
- https://learn.microsoft.com/ja-jp/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-ver15&tabs=alpine18-install%2Calpine17-install%2Cdebian8-install%2Credhat7-13-install%2Crhel7-offline#microsoft-odbc-17

