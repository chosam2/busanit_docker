# Harbor 설치 가이드

## Docker Compose 다운로드 홈페이지

- https://docs.docker.com/compose/install/

## Docker Compose 설치방법

- stable 버전 다운로드

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

- 실행권한 추가

```
sudo chmod +x /usr/local/bin/docker-compose
```

> 심볼링 링크 추가 : 정상적으로 명령이 동작하지 않을 경우 환경변수 설정을 위해서 심볼릭 링크 추가

```
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

- Docker Compose 버전 확인

```
docker-compose --version
```

## Harbor 다운로드 홈페이지

- 공식 홈페이지 : https://goharbor.io/docs/2.0.0/install-config/ 

- github 소스파일 : https://github.com/goharbor/harbor/releases

## Harbor 설치방법

> `wget` 도구가 없을 경우에는 `yum -y install wget` 으로 다운로드

- offline용 tgz 파일 다운로드 **(online용 tgz 파일 받아서 진행해도 상관x)**
```
wget https://github.com/goharbor/harbor/releases/download/v1.10.1/harbor-offline-installer-v1.10.1.tgz
```

- tgz파일 압축해제

```
tar zxf harbor-offline-installer-v1.10.1.tgz 
```

- harbor 디렉토리로 이동

```
cd harbor
```

- harbor.yml 파일 수정

```yml
...
hostname: docker.nobreak.co.kr
# http related confighttp:  # port for http, default is 80. If https enabled, this port will redirect to https port
  port: 80# https related config#https:
# https port for harbor, default is 443
#  port: 443
# The path of cert and key files for nginx
#  certificate: /your/certificate/path
#  private_key: /your/private/key/path
```

- HTTPS 비활성화

```
sudo vi /etc/docker/daemon.json
{
"insecure-registries" : ["192.168.56.101"]
}
```

- 서비스 재시작
```
sudo systemctl restart docker
```

- install.sh 스크립트 실행(sudo 권한으로 실행)

```
sudo ./install.sh
```

- Login 테스트

```
docker login 192.168.56.101
Username: admin
Password: Harbor12345
```