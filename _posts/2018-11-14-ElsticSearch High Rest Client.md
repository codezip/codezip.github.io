---
layout: post
title:  "ElasticSearch High Rest Client"
date:   2018-11-14 04:10:03 +0900
categories: [ElasticSearch]
---

##ElasticSearch JAVA REST CLIENT
#### Match Query
```json
{
  "query": { "match": { "url.keyword": "/sentence/view" } }
}
```
```java
QueryBuilder queryBuilder = QueryBuilders.matchQuery("url.keyword", "/sentence/view");
```



