---
layout: post
title:  "ElasticSearch Template"
date:   2018-11-09 04:10:03 +0900
categories: [ElasticSearch]
---

#ElasticSearch Template

#### Template 생성
```bash
	curl -XPUT http://localhost:9201/_template/template_product
	{
	  "template": "product*",
	  "settings": {
	    "number_of_shards": 8
	  },
	  "version": 1
	}
```
product로 생성되는 index에 shard를 8개 생성한다. 
매핑정보와 공통되는 부분을 작업하면 편하다. 

#### Template 조회
```bash
	curl -XGET http://localhost:9201/_template
```

#### Template 삭제
```bash
	curl -XDELETE http://localhost:9201/_template/template_product?pretty
```
