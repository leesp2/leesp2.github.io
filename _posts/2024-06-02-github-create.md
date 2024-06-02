---
title: jekyll-theme-chirpy 테마를 이용한 Github 블로그 세팅
description: >-
  jekyll-theme-chirpy 테마 github 블로그 세팅 방법
author: leesp2
date: 2024-06-02 12:56:00 +0900
categories: [Github blog]
tags: [getting started]
---

2024년 6월 2일 기준으로 https://github.com/cotes2020/jekyll-theme-chirpy 테마를 가지고 만들었다.<br>
해당 테마를 가지고 만든 여러 블로그들이 있는데 이전에 만든 정보들이라서 최신 정보와 맞지 않는다.<br>
또한 추후에 해당 테마가 업데이트가 될 수 있고 업데이트가 되면 또한 빌드 방법등에 대해서 변경이 있을 수 있어 작성날짜보다 너무 오래되었다면 git의 위키를 보는 것을 추천한다.<br>

## 준비
준비가 필요한 내용들은 따로 설명을 안하고 진행할 예정
<br>
1. github 계정
2. 로컬에 git 환경 설치
3. ruby 설치
4. jekyll 설치
5. node.js 설치

## Github 블로그 세팅

### 테마 fork
먼저 https://github.com/cotes2020/jekyll-theme-chirpy 로 가서 fork 를 한다.<br>
(<span style="color:red">!! fork안하고 소스를 다운받으면 제대로 되지 않을 수 있으니 무조건 fork로 해야한다.</span>)
![img-description](/assets/img/2024-06-02/1.png)
<br>
<br>
repository name에 사용자이름.github.io 라고 만들고 create를 한다.
![img-description](/assets/img/2024-06-02/2.png)

### git clone 및 스크립트 실행
로컬에 fork 한 git을 clone 받는다.
```
git clone https://github.com/leesp2/leesp2.github.io.git
```
<br>
clone 받은 후에 이제 다음 코드를 실행해야 한다.
```
bash tools/init.sh
```

윈도우의 cmd에서 init.sh를 호출하면 파일이름만 변경을 하고 있어 git bash를 이용해서 작업을 해야 한다.<br>
로컬에 git을 설치하면 git bash라는 프로그램이 깔려 있으므로 이를 통헤 실행을 한다.<br>
![img-description](/assets/img/2024-06-02/3.png)
<br>
git clone한 루트가지 이동해서 위의 명령을 실행하면 git을 clone 받고 설치를 하고 마지막에 commit을 자동으로 해준다.
설치가 완료가 됐으면 /assets/js/dist 폴더 하위에 파일들이 있는지 확인한다.
스크립트를 통해서 commit까지 완료했으니 push를 한번 해준다.
```
git push origin master
```

### 로컬에서 실행
ruby를 설치했다면 Start Command Prompt with Ruby 프로그램이 있을것이고 해당 프로그램을 실행한다.
![img-description](/assets/img/2024-06-02/4.png)
<br>
clone 받은 폴더의 루트로 이동해서 bundle 명령어를 실행하면 Gemfile을 통해서 필요한 프로그램을 설치한다.
완료 되면 다음 명령어를 실행해서 서버를 띄우면 로컬에서 페이지를 접속할 수 있다.
```
bundle exec jekyll s
```
http://127.0.0.1:4000 을 통해서 접속하면 테마가 설치된 github 블로그를 접속할 수 있다.
![img-description](/assets/img/2024-06-02/5.png)
<br>
### 웹에서 접속
여기까지 완료되었으면 아까 git push를 하면서 자동적으로 git actions 통해서 build하고 deploy까지 되어서 http://{USERNAME}.github.io 로 접속해보면 로컬에서 접속한 결과와 동일하게 접근 할 수 있다.
