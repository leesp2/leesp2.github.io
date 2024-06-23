---
title: linux에서 openssl 빌드를 통해 라이브러리 얻는 방법
description: >-
  linux에서 openssl 빌드를 통해 라이브러리 얻는 방법
author: leesp2
date: 2024-06-16 15:45:00 +0900
categories: [opensource, openssl]
tags: [opensource, openssl]
---

## linux centos7 기준 openssl 최신 버전 빌드해서 라이브러리 얻는 방법

[opensssl 다운로드 경로](https://www.openssl.org/source/index.html)<br>
해당 위치에서 openssl 최신 버전 링크 주소를 복사해서 wget을 통해서 로컬에 다운로드한다.<br>
<br>
openssl 다운로드
```console
$wget https://www.openssl.org/source/openssl-3.3.1.tar.gz
```

압축해제 및 경로로 이동
```console
$tar xvf openssl-3.3.1.tar.gz
$cd openssl-3.3.1
```

배포 폴더 생성 및 배포 설정, prefix를 통해서 서버 전체가 아닌 라이브러리를 쓰기 위해서 빌드 위치에 파일이 나오도록 한다.
```console
$mkdir build
$./config --prefix=$PWD/build
```

openssl 3.0 버전 이상부터는 config 실행시에 다음과 같은 에러가 발생한다.

```console
Can't locate IPC/Cmd.pm in @INC (@INC contains: /engn001/installer/openssl-3.0.7/util/perl /usr/local/lib64/perl5 /usr/local/share/perl5 /usr/lib64/perl5/vendor_perl /usr/share/perl5/vendor_perl /usr/lib64/perl5 /usr/share/perl5 . /engn001/installer/openssl-3.0.7/external/perl/Text-Template-1.56/lib) at /engn001/installer/openssl-3.0.7/util/perl/OpenSSL/config.pm line 19.
BEGIN failed--compilation aborted at /engn001/installer/openssl-3.0.7/util/perl/OpenSSL/config.pm line 19.
Compilation failed in require at /engn001/installer/openssl-3.0.7/Configure line 23.
BEGIN failed--compilation aborted at /engn001/installer/openssl-3.0.7/Configure line 23.
```

IPC-Cmd 사용 불가한 것으로 보여(설치 안되어 있음) yum으로 설치 진행한다.
```console
$yum install perl-IPC-Cmd
```

설치후에 다시 빌드 배포 설정을 하면 빌드할 수 있는 Makefile이 나온다.
```console
$./config --prefix=$PWD/build
```

config를 통해서 os 환경에 맞게 Makefile이 작성이 되기 때문에 make로 빌드를 하고 빌드과 완료되면 make install을 통해서 빌드 결과물을 $PWD/build 폴더에서 확인할 수 있다.
```console
$make   
$make instll
```

$PWD/build/lib64 폴더에서 ssl, crypto 라이브러리를 얻을 수 있다.
![img-description](/assets/img/2024-06-16/1.png)