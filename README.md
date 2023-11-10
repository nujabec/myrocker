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
# push方法

```bash
docker push nujabec/myrocker:20231110
```

## オフライン環境にdocker imageを持っていく方法

```bash
# オンライン端末でイメージを作成
# docker imageをtarファイルに変換
docker save nujabec/myrocker:20231110 > myrocker_20231110.tar
# オフライン端末で、tarファイルからdocker imageを読む
docker load < myrocker_20231110.tar
```
