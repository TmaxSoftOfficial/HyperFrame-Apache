# HyperFrame Apache for Win64 설치방법

## 순서
- 설치 전 확인 사항
- 설치
- 기동 및 종료

## 설치 전 확인사항

### 시스템 요구사항
|제목|설명|
|----------|---------------------|
|버전|2.4.52 (openssl 1.1.1m)|
|Disk공간|최소 50MB 이상, 설치 후 아파치는 10MB의 디스크 공간을 차지하며<br>구성 옵션과 추가한 모듈에 따라 차이가 많이 난다.|
|빌드 시스템|Visual C++ Redistributable for Visual Studio 2015-2022|
|Minimum<br>system required|Windows 7 SP1<br>Windows 8 / 8.1<br>Windows 10<br>Windows 11<br>Windows Server 2022<br>Windows Server 2019<br>Windows Server 2016<br>Windows Server 2008 R2 SP1<br>Windows Server 2012 / R2<br>Windows Vista SP2|
|참고사항|https://www.apachelounge.com/download/|
* Apache Lounge is all about the Apache Web Server provided by the Apache Software Foundation (ASF) HTTPD Server Project



## 설치

### 설치 전 필수 OS utility 설치
- 설치 파일 다운로드
  - https://www.apachelounge.com/download/ 

    ![image](https://user-images.githubusercontent.com/96853118/148351181-bf02e07a-7539-435f-9598-e7d7c7456502.png)

- Visual C++ Redistributable for Visual Studio 2015-2022 설치

  ![image](https://user-images.githubusercontent.com/96853118/148351619-8ca7f972-e3e4-4e8c-b941-7cd8fe469865.png)

  ```
  $ OS 64bit : VC_redist.x64.exe
  $ OS 32bit : VC_redist.x86.exe
  ```

### Apache 설치
- 설치 파일 다운로드 (VC버전에 따라 다운로드)
  - https://www.apachelounge.com/download/
- 설치파일
  ```
  $ OS 64bit :  httpd-2.4.52-win64-VS16.zip 
  $ OS 32bit :  httpd-2.4.52-win32-VS16.zip
  ```
- 설치
  - 압축 파일을 임의의 경로에 압축해제 (ex: D:\hyperframe\apache24
  - 이 경로가 Apache 설치경로임
- Windows 환경 설정
  - 환경 변수 등록 : PATH 에 httpd.exe 가 포함된 경로 등록
  - Windows 시스템 속성 > 환경변수(N)... > 시스템 변수(S) > Path선택 > 편집(I)... > 새로 만들기(N) > 설치경로/bin 입력 > 확인
- Apache 환경 설정 변경
  - ServerRoot, Listen port 등 변경
  - Apache설치경로/conf/httpd.conf 에서 수정
  - Define SRVROOT 경로 변경 : Apache 설치경로로 변경
  - Listen 포트 변경 : 80(기본값) 에서 원하는 값으로 변경
- Apache Windows service 등록
  - cmd 창 열고 Apache설치경로/bin 으로 이동
  - Windows Service 등록명령 수행
    ```
    httpd -k install
    ```
  - Windows 보안경고 발생 시 "액세스 허용(A)" 선택
  - Windows 서비스 목록에서 Apache2.4 서비스 확인



## Apache 기동 및 종료

### Apache 기동
- Windows service를 통한 기동
  - Windows 서비스 목록에서 Apache2.4 선택
  - 상단 메뉴바 또는 좌상단 설명란에서 "서비스 시작" 메뉴 선택
  - 작업관리자 > 세부정보 에서 httpd.exe 프로세스 확인
  - cmd 창에 다음 명령으로 httpd.exe 프로세스 및 PID 확인
    ```
    tasklist | findstr httpd.exe
    ```
  - cmd 창에 다음 명령으로 Apache 포트 LISTEN 및 PID 확인
    ```
    netstat -ano | findstr httpd.exe
    ```
    - PID : tasklist 명령에서 확인한 httpd.exe 의 PID 확인
    - 포트정보 : httpd.conf 의 "Listen" 에 설정한 포트가 LISTEN 상태인지 확인

### Apache 종료
- Windows service를 통한 종료
  - Windows 서비스 목록에서 Apache2.4 선택
  - 상단 메뉴바 또는 좌상단 설명란에서 "서비스 중지" 메뉴 선택
  - 작업관리자 > 세부정보 에서 httpd.exe 프로세스가 제거된 것 확인
  - cmd 창에 다음 명령으로 httpd.exe 프로세스가 제거되었는지 확인
    ```
    tasklist | findstr httpd.exe
    ```
  - cmd 창에 다음 명령으로 Apache 포트 LISTEN 확인
    ```
    netstat -ano | findstr [포트번호]
    ```
    - 포트번호 : httpd.conf 의 "Listen" 에 설정한 포트가 LISTEN 상태인지 확인


## Apache 호출
- Apache설치경로/htdocs 폴더에 index.html 파일 생성
  ```
  <html><body><h1>HyperFrame Apache it Works!</h1></body></html>
  ```
- http://ip:port/index.html 호출

  HyperFrame Apache it Works!
  =============================


## 참고 : Third Party Site

### third party site (https://dlcdn.apache.org//httpd/binaries/win32/)
- https://www.apachehaus.com/
- https://www.apachelounge.com/
- https://bitnami.com/
- https://www.wampserver.com/
- https://www.apachefriends.org/



HyperFrame Apache for Win64
Apache 2.4.52 Win64 & vc_redist_x64
