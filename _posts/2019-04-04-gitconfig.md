---
layout: post
title:  "gitconfig 개인계정과 회사계정 분리 관리하기 "
date:   2019-04-04 02:10:03 +0900
categories: [tool]
---

### .gitconfig
 - 개인계정과 회사계정을 분리관리하는 방법이 여러가지 있지만 디렉토리별로 관리하는게 편해서 아래와 같이 사용한다. 

## 설정 
~/.gitconfig
```plain
[includeIf "gitdir:~/git/"]
 path = ~/.gitconfig-work

[includeIf "gitdir:~/private/"]
 path = ~/.gitconfig-private

```

### 회사계정 정보
~/.gitconfig-work
```plain
[user]
  email = 
  name = 
```

### 개인계정 정보
~/.gitconfig-private
```plain
[user]
  email = 
  name = 
```  
  
참고
[includeIf](https://git-scm.com/docs/git-config#_conditional_includes){:target="_blank"}

