# 빌드 환경

- CentOS Linux release 7.7.1908

# 파일 내역

아래 등록된 *build.tar.gz는 모두 Build 된 상태의 파일

- apache2.4.48_build.tar.gz
- apr-1.7.0_build.tar.gz
- apr-util-1.6.1_build.tar.gz
- pcre-8.45_build.tar.gz
- openssl-1.1.1k_build.tar.gz

# 경로가 fix된 파일 리스트

아래의 파일에는 path가 fix가 되어있으므로 참고 필요 (상세 설정은 생략)

- ${APACHE_HOME}/conf: httpd.conf
- ${APACHE_HOME}/bin: apachectl, apxs, apr-1-config, envvars, envvars-std
- ${APACHE_HOME}/build: apr_rules.mk, config.nice, config_vars.mk
- ${APACHE_HOME}/include  ap_config_auto.h, ap_config_layout.h
- ${APACHE_HOME}/lib: libapr-1.la, libaprutil-1.la
- ${APACHE_HOME}/lib/pkgconfig: apr-1.pc, apr-util-1.pc
