# 도커 명령

## 이미지 다운로드

### (1) docker search 
docker search 명령을 사용하여 이미지를 검색할 수 있다. TERM에 키워드를 지정하면 저장소 이름, 허브의 ID, 설명 등에 포함된 글자 기준으로 결과를 나타낸다. `docker search` 사용법은 다음과 같다.

```bash
[devops@docker ~]$ docker search --help

Usage:	docker search [OPTIONS] TERM
...
```

### (2) docker pull 명령
`docker pull` 명령은 이미지를 다운로드할 때 사용한다. docker pull 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker pull --help

Usage:	docker pull [OPTIONS] NAME[:TAG|@DIGEST]
...
```

## 3) 이미지 관리

이미지를 다운로드했다면 확인하거나 사용하지 않으면 삭제할 수 있다.

### (1) docker images
docker images 명령으로 이미지 목록을 나열한다. 이 명령은 docker image ls 명령과 동일하지만 편의상 docker images를 좀 더 사용한다. docker images 사용법은 다음과 같다.

```bash
[devops@docker ~]$ docker images --help

Usage:	docker images [OPTIONS] [REPOSITORY[:TAG]]
...
```

### (2) docker rmi
docker rmi 명령을 사용하여 이미지를 삭제할 수 있다. docker rmi 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker rmi --help

Usage:	docker rmi [OPTIONS] IMAGE [IMAGE...]
...
```

### (3) docker inspect
docker inspect 명령은 이미지뿐만 아니라 도커 오브젝트의 정보를 자세히 확인할 때 사용한다. docker inspect의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker inspect --help

Usage:	docker inspect [OPTIONS] NAME|ID [NAME|ID...]
...
```

### (4) docker save / load
docker save 명령은 호스트에 저장된 이미지를 아카이브 파일로 복사하는 명령이며, docker load 명령은 아카이브 파일을 불러오는 명령이다. docker save 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker save --help

Usage:	docker save [OPTIONS] IMAGE [IMAGE...]
...
```
docker save 명령은 -o 옵션을 사용하여 생성되는 파일의 경로를 지정해야한다.

docker load 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker load --help

Usage:	docker load [OPTIONS]
...
```