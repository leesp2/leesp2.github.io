---
title: linux에서 libev 빌드를 통해 라이브러리 얻는 방법
description: >-
  linux에서 libev 빌드를 통해 라이브러리 얻는 방법
author: leesp2
date: 2024-06-09 15:45:00 +0900
categories: [opensource, libev]
tags: [opensource, libev]
---

## linux centos7 기준 libev 최신 버전 빌드해서 라이브러리 얻는 방법

libev는 고성능 이벤트 루프를 구현하는 라이브러리이다.<br>
이벤트 루프를 통해서 개발을 하거나 많은 opensource에서 해당 라이브러리를 이용해서 개발이 되고 있다.

http://dist.schmorp.de/libev/<br>
해당 위치에서 libev 최신 버전 링크 주소를 복사해서 wget을 통해서 로컬에 다운로드한다.<br>
<br>
libev 다운로드
```console
$wget http://dist.schmorp.de/libev/libev-4.33.tar.gz
```

압축해제 및 경로로 이동
```console
$tar xvf libev-4.33.tar.gz
$cd libev-4.33
```

배포 폴더 생성 및 배포 설정, prefix를 통해서 서버 전체가 아닌 라이브러리를 쓰기 위해서 빌드 위치에 파일이 나오도록 한다.<br>
빌드할 수 있는 Makefile이 나온다.
```console
$mkdir build
$./config --prefix=$PWD/build
```

config를 통해서 os 환경에 맞게 Makefile이 작성이 되기 때문에 make로 빌드를 하고 빌드과 완료되면 make install을 통해서 빌드 결과물을 $PWD/build 폴더에서 확인할 수 있다.
```console
$make   
$make instll
```

$PWD/build/lib 폴더에서 libev 라이브러리를 얻을 수 있다.
![img-description](/assets/img/2024-06-16/2.png)