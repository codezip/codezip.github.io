---
layout: post
title:  "REDASH Docker 설정"
date:   2018-11-14 07:10:03 +0700
categories: [data]
---

#### REDASH 
- DashBoard 도구, 

#### REDASH 설치 
Docker Compose 설치

#### Docker 준비 
```bash
git clone https://github.com/getredash/redash.git
```

docker-compose.production.yml 

```
server, worker, redis, postgres, nginx 총 5 개의 컨테이너의 설정으로 구성되어 있다. 

```

```yml
postgres:
image: postgres:9.5.6-alpine
 volumes:
 - /codezip/postgres-data:/codezip/postgresql/data
```

```bash
docker-compose -f docker-compose.production.yml run --rm server create_db
```

#### 컨테이너 실행 
```bash
docker-compose -f docker-compose.production.yml up -d
```

#### REDASH 실행
```bash
http://localhost:5000
```

