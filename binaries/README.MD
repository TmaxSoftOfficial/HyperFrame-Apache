# 빌드 환경

- CentOS Linux release 7.7.1908
- Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz x86_64 bit

# 파일 내역

binaries 폴더에 등록된 apache2.4_build.tar.gz에는 아래의 Build 파일 포함

- apr-1.7.0
- apr-util-1.6.1
- pcre-8.45
- openssl-1.1.1k

압축파일의 빌드된 경로는 아래를 참고

    $ tar -xzvf apache2.4_Linux_x86_64bit_build.tar.gz
    $ cd ${APACHE_HOME}
    
    # Apache2.4를 설치하면 bin, build, cgi-bin, conf, error, htdocs, icons, include, lib, logs, man, manual, modules 폴더가 기본적으로 설치되나, Apache2.4 폴더 아래에 src 폴더를 별도로 생성하여 필요한 라이브러리 위치시킴
    $ cd ${APCHE_HOME}/src
    $ ls -al
    drwxr-xr-x.  8 hfapache hfapache  4096 Oct  1 04:53 .
    drwxr-xr-x. 16 hfapache hfapache  4096 Oct  1 05:02 ..
    drwxr-xr-x. 28 hfapache hfapache  4096 Oct  1 04:54 apr-1.7.0
    drwxr-xr-x. 21 hfapache hfapache  4096 Oct  1 04:55 apr-util-1.6.1
    drwxr-xr-x.  6 hfapache hfapache    60 Oct  1 04:58 build
    drwxr-xr-x. 13 hfapache hfapache  4096 Oct  1 05:01 httpd-2.4.48
    drwxrwxr-x. 18 hfapache hfapache  4096 Oct  1 04:55 openssl-1.1.1k
    drwxr-xr-x.  9 hfapache hfapache 12288 Oct  1 04:57 pcre-8.45
     
    # openssl, pcre, apr, apr-util 등 빌드한 파일은 아래의 경로로 위치
    $ cd ${APACHE_HOME}/src/build
    $ ls -al
    drwxr-xr-x. 6 hfapache hfapache   60 Oct  1 04:58 .
    drwxr-xr-x. 8 hfapache hfapache 4096 Oct  1 04:53 ..
    drwxr-xr-x. 6 hfapache hfapache   58 Oct  1 04:54 apr
    drwxr-xr-x. 5 hfapache hfapache   43 Oct  1 04:55 apr-util
    drwxr-xr-x. 7 hfapache hfapache   67 Oct  1 04:56 openssl
    drwxr-xr-x. 6 hfapache hfapache   56 Oct  1 04:58 pcre

# 빌드 파일 실행방법

* 등록된 빌드 바이너리의 Prefix는 /home/hfapache/apache2.4로 빌드

