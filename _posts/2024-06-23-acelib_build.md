---
title: linux에서 ACE library 빌드를 통해 라이브러리 얻는 방법
description: >-
  linux에서 ACE library 빌드를 통해 라이브러리 얻는 방법
author: leesp2
date: 2024-06-23 15:45:00 +0900
categories: [opensource, ACE]
tags: [opensource, ACE]
---

## linux centos9 기준 ACE library 빌드 방법

ACE 라이브러리가 버전이 올라가면서 gcc 버전이 4.8 이상이어야 빌드가 된다. <br>
centos7은 gcc가 4.8.5 인데 빌드가 안되어서 gcc를 버전올려야 한다. gcc 빌드는 다음에 문서로 남기기로 하고 centos9 버전으로 빌드를 해보려고 한다.<br>
centos9버전은 gcc 11 버전으로 ACE 라이브러리 빌드가 가능하다. <br>

[ACE library 다운로드 경로](https://download.dre.vanderbilt.edu/)<br>
해당 위치에서 ACE library 최신 버전 링크 주소를 복사해서 wget을 통해서 로컬에 다운로드한다.<br>
<br>
ACE library 다운로드
```console
$wget https://github.com/DOCGroup/ACE_TAO/releases/download/ACE%2BTAO-7_1_0/ACE-7.1.0.tar.gz
```
<br>
압축해제 및 경로로 이동
```console
$tar xvf ACE-7.1.0.tar.gz
$cd ACE_wrappers
```
<br>
배포 폴더 생성 및 배포 설정, ACE_ROOT 환경변수 설정
```console
$mkdir build
$export ACE_ROOT=$PWD
```
<br>
헤더 추가
```console
$vi $ACE_ROOT/ace/config.h
```
#include "ace/config-linux.h" 추가
<br><br>
파일 추가
```console
$vi $ACE_ROOT/include/makeinclude/platform_macros.GNU
```
include $(ACE_ROOT)/include/makeinclude/platform_linux.GNU <br>
INSTALL_PREFIX=$(ACE_ROOT)/build <br>
<br>

공유라이브러리 빌드를 위한 설정을 하고 make로 빌드를 하고 빌드과 완료되면 make install을 통해서 빌드 결과물을 $PWD/build 폴더에서 확인할 수 있다.
```console
$export LD_LIBRARY_PATH=$ACE_ROOT/lib:$LD_LIBRARY_PATH
$make
$make install
```

$PWD/build 폴더에서 ace 라이브러리를 얻을 수 있다.