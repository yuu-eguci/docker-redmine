README_DEV
===

これは開発用の README です。
README_ORIGINAL.md は、 docker-redmine repository のオリジナルです。

WARN: これは fork repository です。なので private repository にすることは不可。

```bash
# 開発環境用の .env を適用してコンテナを起動。
rm -rf ./srv/*
mkdir -p ./srv/docker/redmine
cp .env.develop .env
docker compose -f docker-compose-mysql.yml up
# --> http://localhost:10083
```

## Deployment

```bash
# デプロイしたい image の ID を取得
docker images

# Container Registry 用のタグをつける
docker tag 524f035e0feb REGISTRY_NAME.azurecr.io/REGISTRY_REPOSITORY:2024.03.28.a

# Container Registry へログインする
az acr login --name REGISTRY_NAME

# Container Registry へ push する
docker push REGISTRY_NAME.azurecr.io/REGISTRY_REPOSITORY:2024.03.28.a

# App Service の slot に production 用の環境変数をセット

# MySQL のほうに redmine_production schema を作る

# App Service Deployment Center で Image を REGISTRY_REPOSITORY:2024.03.28.a にする
```
