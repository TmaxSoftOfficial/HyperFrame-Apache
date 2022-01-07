# HyperFrame-Apache

업로드된 바이너리는 HyperFrame Open Edition 제품 설치를 위한 파일 및 바이너리 폴더에 있는 파일은 아래와 같음 

- 외부 연동 모듈을 포함한 빌드 바이너리 
- WAS와 연동이 필요한 mod_jk.so 파일
- 설치파일 (아래 내용 참고)

## 설치 파일

### Apache

* Version : httpd-2.4.48
* Note : https://httpd.apache.org/download.cgi

### Apr Library

* Version : apr-1.7.0
* Note : https://apr.apache.org/download.cgi

### Apr Util Library

* Version : apr-util-1.6.1
* Note : https://apr.apache.org/download.cgi

### PCRE

* Version : pcre-8.45
* Note : https://ftp.pcre.org/pub/pcre/

### OpenSSL

* Version : openssl-1.1.1l
* Note : https://www.openssl.org/source/

## 검증 환경
    
* CentOS Linux release 7.7
* CentOS Linux release 8.4
* Ubuntu 20.04.1 LTS


## 설치 및 실행

### 1) Acache 압축 풀기

    $ cd ${INSTALL_HOME}
    $ tar -zxvf httpd-2.4.48.tar  

### 2) Apr Library, Apr Util Library 압축 풀기

    $ cd ${INSTALL_HOME}
    $ tar -zxvf apr-1.7.0.tar.gz    
    $ tar -zxvf apr-util-1.6.1.tar.gz  
    $ mv apr-1.7.0 ${APACH_HOME}/srclib/apr
    $ mv apr-util-1.6.1 ${APACH_HOME}/srclib/apr-util

### 3) PCRE 압축 풀기 및 설치

    $ cd ${INSTALL_HOME}
    $ cd ${PCRE_HOME}
    $ tar -xzvf pcre-8.45.tar.gz
    $ ./configure --prefix=${PCRE_HOME}
    $ make & make install

### 4) Apache 설치

    $ cd ${INSTALL_HOME}
    $ ./configure --prefix=${NEW_APACHE_HOME} --enable-modules=all --enable-mods-shared=all --enable-ssl --enable-pcre=static --with-pcre=${PCRE_HOME} --with-openssl=${OPENSSL_HOME} --enable-http2
    $ make & make install
    
### 5) OpenSSL 압축 풀기

    $ cd ${INSTALL_HOME}
    $ tar -zxf openssl-1.1.1l.tar.gz
    $ cd ${OPENSSL_HOME}
    $ ./config --prefix=${OPENSSL_HOME}
    $ make & make install 

### 6) Apache 실행

    $ cd ${NEW_APACHE_HOME}/bin
    $ ./httpd -k start
    
### 7) Apache 종료

    $ cd ${NEW_APACHE_HOME}/bin
    $ ./httpd -k stop

## 디렉토리 구조

      Apache
      ├── bin
      ├── build      
      ├── cgi-bin            
      ├── conf            
      ├── error
      ├── htdocs        
      ├── icons
      ├── include
      ├── logs
      ├── man
      ├── manual
      └── modules           

## 버전 확인

    $ cd ${APACHE_HOME}/bin/
    $ ./httpd -v
    Server version: Apache/2.4.48 (Unix)
    Server built:   Aug 24 2021 13:36:55

## 로그 정보

### 1) 로그 경로

* Error.log

      ${APACHE_HOME}/logs/error_log
      
* Access.log

      ${APACHE_HOME}/logs/access_log

### 2) 로그 설정 변경

* Error 로그 경로

      ${APACHE_HOME}/conf/httpd.conf/
      ErrorLog Logs/error_log
      
* Log Level 설정

      ${APACHE_HOME}/conf/httpd.conf/
      # Log Level [ debug / info / notic / warn / error / crit ]
      LogLevel warn
      
## 환경 설정 파일 정보

### 1) 경로
    
    ${APACHE_HOME}/conf/httpd.conf/

### 2) 환경 설정

* Port 변경

      ...
      Listen 80;
      ...

* 동시 접속자 수 제어

      ...
      MaxClients   150;        # Max 256
      ...

## Apache 명령

### 1) Apache 컴파일 정보 확인

    $ cd ${APACHE_HOME}/bin/
    $ ./httpd -V
    Server version: Apache/2.4.48 (Unix)
    Server built:   Aug 24 2021 13:36:55
    Server's Module Magic Number: 20120211:105
    Server loaded:  APR 1.7.0, APR-UTIL 1.6.1
    Compiled using: APR 1.7.0, APR-UTIL 1.6.1
    Architecture:   64-bit
    Server MPM:     event
      threaded:     yes (fixed thread count)
        forked:     yes (variable process count)
    Server compiled with....
     -D APR_HAS_SENDFILE
     -D APR_HAS_MMAP
     -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
     -D APR_USE_PROC_PTHREAD_SERIALIZE
     -D APR_USE_PTHREAD_SERIALIZE
     -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
     -D APR_HAS_OTHER_CHILD
     -D AP_HAVE_RELIABLE_PIPED_LOGS
     -D DYNAMIC_MODULE_LIMIT=256
     -D HTTPD_ROOT="${APACHE_HOME}"
     -D SUEXEC_BIN="${APACHE_HOME}/bin/suexec"
     -D DEFAULT_PIDLOG="logs/httpd.pid"
     -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
     -D DEFAULT_ERRORLOG="logs/error_log"
     -D AP_TYPES_CONFIG_FILE="conf/mime.types"
     -D SERVER_CONFIG_FILE="conf/httpd.conf"
     
### 2) 설정 파일 지정 Apache 실행

    $ cd ${APACHE_HOME}/bin/
    $ ./httpd -f [설정파일]     

### 3) 설정 파일 타당성 체크

    $ cd ${APACHE_HOME}/bin/
    $ ./httpd -t                                           
      
