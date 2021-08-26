# HyperFrameOE-Apache

업로드된 바이너리는 HyperFrame Open Edition 제품 설치를 위한 파일이며, 첨부한 바이너리중 apache2.4.48_centos7.tar.gz와 apache2.4.48_ubuntu.tar.gz 파일은 make 및 make install까지 끝낸 바이너리로 외부 모듈들을 포함하고 있음

# 사전에 필요한 설치파일

- httpd-2.4.48.tar.gz 파일 필요  
- apr-1.7.0.tar.gz  
- apr-util-1.6.1.tar.gz
- pcre-8.42.tar.gz 

# 설치방법

- 다음의 jar 파일들의 압축 해제

      $ tar -zxvf apr-1.7.0.tar.gz    
      $ tzr -xzvf apr-util-1.6.1.tar.gz  
      $ tar -xzvf httpd-2.4.41.tar  

- 압축을 푼 apr 및 apr-util 라이브러리를 ${APACHE_HOME}/srclib의 라이브러리로 이동

      $ mv apr-1.7.0 ${APACHE_HOME}/srclib/apr
      $ mv apr-util-1.6.1 ${APACHE_HOME}/srclib/apr-util

- pcre 설치

      $ cd ${PCRE_HOME}
      $ tar -xzvf pcre-8.42.tar.gz
      $ ./configure --prefix=${PCRE_HOME}
      $ make
      $ make install

-  Apache 2.4.48 설치 및 실행

       $ cd ${APACHE_HOME}
       $ ./configure --prefix=${NEW_APACHE_HOME} --with-pcre=${PCRE_HOME}
       $ make
       $ make install

- 설치 후 기동

# 기동/종료

      - 기동:  httpd -k start
      - 종료:  httpd -k stop

# 버전 확인

      ${NEW_APACHE_HOME}/bin에서 ./httpd -v 명령어로 확인 가능

# 로그 경로

      ${NEW_APACHE_HOME}/logs 폴더에서 access 로그와 error 로그 확인 가능

# 버전 이력

HyperFrameOE-Apache 2.4.48
