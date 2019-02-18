# Docker with Ghost and Caddy proxy

## How to use

### 1. create .env file

```
cp .env.sample to .env
```

Then, edit .env as you like

### 2. create storage.env

```
cp storage.env.sample to storage.env
```

Then, edit storage.env as you like. If not using any storage adapter, keep storage.env blank.

### 3. run

```
docker-compose up -d
```


### 4. (optional) install storage package

For example, using ali-oss adapter called [`ghost-oss-store`](https://github.com/goodideal/ghost-oss-store).

Find `ghost-content` folder (can change in .env file), create `adapters/storage/ghost-oss-store` folder and create `index.js`

```bash
cd ghost-content
mkdir -p dapters/storage/ghost-oss-store
cd dapters/storage/ghost-oss-store

cat << EOF > index.js
'use strict';
module.exports = require('ghost-oss-store');
EOF

npm install goodideal/ghost-oss-store

# go back to docker-compose.yml folder

docker-compose up -d
```