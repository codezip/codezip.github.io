---
layout: post
title:  "ElasticSearch 유사어/금지어"
date:   2018-11-10 05:10:03 +0900
categories: [ElasticSearch]
---

금지어(불용어)의 경우 색인 데이터로 의미가 없는 조사,접속사 등을 제외시켜주는 역할을 한다. 

조사, 부사, 접속사 같은 경우는 보통 시스템 금지어(불용어)로 분류되어 관리되어 진다. 

사용자 금지어(불용어)의 경우 욕설이나 특정 키워드에 대해서 검색 대상에 제외시키는 방법이다. 

해당 시스템이나 정책에 따라 관리를 하면 된다. 

유사어의 경우 사용자가 codezip 을 검색을 했지만 "코드집"에 대해서도 검색 결과에 반영해 주는 역할을 한다. 
한글/영문에 대한 부분 / 혼돈하기 쉬운 오타등 다양하게 활용할 수 있다. 

검색 서비스의 경우 다양한 방법으로 해법을 찾을 수 있다. 

다음은 ES에서 제공해 주는 설정하는 방법을 해 볼 예정이다. 

```json
"analysis":{  
   "filter":{  
      "nGram_filter":{  
         "type":"nGram",
         "min_gram":2,
         "max_gram":20,
         "token_chars":[  
            "letter"
         ]
      },
      "synonym":{  
         "type":"synonym",
         "synonyms_path":"synonyms.txt"
      },
      "stopword":{  
         "type":"stop",
         "stopwords_path":"stopwords.txt"
      }
   },
   "analyzer":{  
      "korean":{  
         "type":"custom",
         "tokenizer":"mecab_ko_standard_tokenizer",
         "filter":[  
            "lowercase",
            "synonym",
            "stopword"
         ]
      },
      "nGram_analyzer":{  
         "type":"custom",
         "tokenizer":"whitespace",
         "filter":[  
            "lowercase",
            "asciifolding",
            "synonym",
            "nGram_filter"
         ]
      },
      "synonym":{  
         "tokenizer":"whitespace",
         "filter":[  
            "synonym"
         ]
      }
   }
}
```

stopwords_path / synonyms_path 의 디폴트 디렉토리는 ES 설치 디렉토리의 config 디렉토리이다. 
해당 디렉토리에 해당 파일이 존재하면 된다. 임의대로 변경 할 수 있다. 

```json
properties:{  
   title:{  
      "type":"string",
      "index_analyzer":"korean",
      "search_analyzer":"korean",
      boost:10
   },
}
```

stopwords.txt 파일 구조(라인 단위로 키워드 입력)

```bash
개소리
멍멍이
욕설
```

synonyms.txt 파일 구조(유사 키워드 , 단위로 입력)

```bash
babootaeng, 바부탱
codezip, 코드집
```