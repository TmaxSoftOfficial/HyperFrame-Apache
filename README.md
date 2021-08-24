# HyperFrameOE-Apache

업로드된 바이너리는 HyperFrame Open Edition 제품 설치를 위한 파일임

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

# 디렉토리 구조

${pwd}                                                                       
|- release-image                                             # image folder                                                    
|   |- Dockerfile                                            # Dockerfile versions (v20.3, v20.4, etc.)
|- usage                                                     # usage folder                                                    
|   |- conf                                                  # Configuration folders
|   |   |- catalina.policy                                   # Configuration file for Tomcat's security policy permissions
|   |   |- catalina.properties                               # Contains shared definitions such as servers, shared loaders, and JARs that are searched when the server starts
|   |   |- context.xml                                       # Loaded when running the application
|   |   |- jaspic-providers.xml                              # Used for jaspic-providers.xml
|   |   |- jaspic-providers.xsd                              # XSD file for jaspic-providers.xml
|   |   |- logging.properties                                # Defines logging properties of Tomcat instance.
|   |   |- server.xml                                        # Contains important information such as IP address and virtual host and context path
|   |   |- tomcat-users.xml                                  # Used for authentication and approval according to role-based definitions
|   |   |- tomcat-users.xsd                                  # XSD file for tomcat-users.xml
|   |   |- web.xml                                           # Define the default values ​​for all applications when the Tomcat instance is started                            
|   |- webapps                                               # Web applications that are basically provided by Tomcat binary files.
|   |   |   |- ROOT                                          # Directories in webapps directory
|   |   |   |- docs                                          # Directories in webapps directory
|   |   |   |- examples                                      # Directories in webapps directory
|   |   |   |- host-namager                                  # Directories in webapps directory
|   |   |   |- manager                                       # Directories in webapps directory
|- README.md    
|- apache-tomcat-latest.tar.gz

# 버전 확인

- ${NEW_APACHE_HOME}/bin에서 ./httpd -v 명령어로 확인 가능

# 로그 경로

- ${NEW_APACHE_HOME}/logs 폴더에서 access 로그와 error 로그 확인 가능

# 버전 이력

HyperFrameOE-Apache 2.4.48
