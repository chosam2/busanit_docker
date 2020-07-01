# 도커 설치

## 0) 편의상 추가적으로 설치할 패키지

```bash
sudo yum -y install epel-release bash-completion bridge-utils
```

## 1) 사전 패키지 설치
아래의 패키지들은 도커 패키지 저장소에 연결하거나 도커를 사용하면서 필요한 패키지들이다.

```bash
sudo yum install -y yum-utils \
     device-mapper-persistent-data \
     lvm2
```

## 2) yum 저장소 설정
yum-config-manager로 docker-ce 패키지 저장소에 연결한다.

```bash
sudo yum-config-manager \
     --add-repo \
     https://download.docker.com/linux/centos/docker-ce.repo
```

## 3) docker-ce 설치
docker-ce 패키지를 설치한다.

```bash
sudo yum install -y docker-ce docker-ce-cli containerd.io
```

## 4) 서비스 실행 및 활성화
패키지가 설치되었으면 서비스를 실행한다.

```bash
sudo systemctl start docker
```

서비스가 부팅 이후에도 동작하도록 활성화한다.

```bash
sudo systemctl enable docker
Created symlink from /etc/systemd/system/multi-user.target.wants/docker.service to /usr/lib/systemd/system/docker.service.
```

## 5) docker 그룹 지정
devops 사용자가 sudo 명령을 사용하지 않더라도 docker 명령을 사용할 수 있게 설정해야 한다.

```bash
sudo usermod -aG docker $USER
```

이 설정을 하고 난 뒤에는 로그아웃 했다가 로그인을 해야한다.

```
exit
```

> docker 그룹에 사용자를 추가하는 작업은 신원이 확실한 사용자가 아니면 권장하지 않는다. 컨테이너를 다루는 권한은 기본적으로 커널을 다루기 때문이다.

## 6) 도커버전 확인
docker를 설치하고 설정이 끝났으면 docker version 명령으로 버전 및 정보를 확인한다.

```bash
docker version
```

## 7) hello world 컨테이너 실행
프로그래밍을 처음 배울 때와 비슷하게 hello-world 컨테이너를 실행해본다.

```bash
docker run hello-world
```