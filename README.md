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

## オフライン環境にdocker imageを持っていく方法

```bash
# オンライン端末でイメージを作成
# docker imageをtarファイルに変換
docker save -o myrocker_20231110.tar nujabec/myrocker:20231110 
# オフライン端末で、tarファイルからdocker imageを読む
docker load -i myrocker_20231110.tar
```
