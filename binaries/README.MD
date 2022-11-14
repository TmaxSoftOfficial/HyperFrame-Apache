# 빌드 환경

- CentOS Stream release 8
- Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz x86_64 bit

# 파일 내역

binaries 폴더에 등록된 apache2.4_build.tar.gz에는 아래의 Build 파일 포함

- apr-1.7.0
- apr-util-1.6.1
- pcre-8.45
- openssl-1.1.1s

압축파일의 빌드된 경로는 아래를 참고

    $ tar -xzvf apache2.4_Linux_x86_64bit_build.tar.gz
    $ cd ${APACHE_HOME}

    # Apache2.4를 설치하면 bin, build, cgi-bin, conf, error, htdocs, icons, include, lib, logs, man, manual, modules 폴더가 기본적으로 설치되나, Apache2.4 폴더 아래에 src 폴더를 별도로 생성하여 필요한 라이브러리 위치시킴
    $ cd ${APCHE_HOME}/src
    $ ls -al
    drwxrwxr-x  8 hfapache hfapache  117 11월 14 14:33 .
    drwxrwxr-x 16 hfapache hfapache  186 11월 14 14:45 ..
    drwxr-xr-x 28 hfapache hfapache 4096 11월 14 14:49 apr-1.7.0
    drwxr-xr-x 21 hfapache hfapache 4096 11월 14 14:51 apr-util-1.6.1
    drwxrwxr-x  6 hfapache hfapache   60 11월 14 14:52 build
    drwxr-xr-x 13 hfapache hfapache 4096 11월 14 14:43 httpd-2.4.48
    drwxrwxr-x 19 hfapache hfapache 4096 11월 14 14:40 openssl-1.1.1s
    drwxr-xr-x  9 hfapache hfapache 8192 11월 14 14:36 pcre-8.45


    # openssl, pcre, apr, apr-util 등 빌드한 파일은 아래의 경로로 위치
    $ cd ${APACHE_HOME}/src/build
    $ ls -al
    drwxrwxr-x 6 hfapache hfapache  60 11월 14 14:52 .
    drwxrwxr-x 8 hfapache hfapache 117 11월 14 14:33 ..
    drwxr-xr-x 6 hfapache hfapache  58 11월 14 14:49 apr
    drwxr-xr-x 5 hfapache hfapache  43 11월 14 14:52 apr-util
    drwxrwxr-x 7 hfapache hfapache  67 11월 14 14:40 openssl
    drwxrwxr-x 6 hfapache hfapache  56 11월 14 14:36 pcre

# 빌드 파일 실행방법

- 등록된 빌드 바이너리의 Prefix는 /home/hfapache/apache2.4.48_openssl1.1.1s로 빌드

- 빌드된 Prefix가 아닌, 다른 Prefix에서 사용 시 사용자 환경에서 [재빌드 과정](https://github.com/TmaxSoftOfficial/HyperFrameOE-Apache#%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%8B%A4%ED%96%89) 수행 필요

# 변경 이력

- 2022년 11월 14일
  - openssl-1.1.1l → openssl-1.1.1s
  - add mpms modules
