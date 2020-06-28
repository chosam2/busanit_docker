# 도커 명령

## 1. 컨테이너 실행

### (1) docker ps
docker ps 명령으로 컨테이너 목록을 확인할 수 있다. docker ps 명령의 사용법은 다음과 같다.

```bash
[devops@docker ~]$ docker ps --help

Usage:	docker ps [OPTIONS]
...
```

### (2) docker create
docker create 명령으로 컨테이너를 생성할 수 있다. docker create 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker create --help

Usage:	docker create [OPTIONS] IMAGE [COMMAND] [ARG...]
...
```

docker create 명령 중 기본적으로 사용하는 옵션은 다음과 같다.

|옵션|설명|
|---|---|
|-i|연결되어있지 않아도 표준입력을 유지|
|-t|가상 터미널 지정|
|--name|컨테이너 이름 지정|

### (3) docker start
docker start 명령은 중지되어 있거나 생성된 컨테이너를 시작할 수 있다. docker start 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker start --help

Usage:	docker start [OPTIONS] CONTAINER [CONTAINER...]
...
```

다음은 docker start 명령 중 유용한 옵션이다.

|옵션|설명|
|---|---|
|-i|컨테이너의 표준입력에 연결|
|-a|컨테이너의 표준출력/에러에 연결|

### (4) docker run
docker run 명령을 사용하여 컨테이너를 바로 실행할 수 있다. 이 명령을 사용하면 create와 start를 사용할 필요가 없다. docker run 명령의 사용법은 다음과 같다.

```bash
[devops@docker ~]$ docker run --help

Usage:	docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
...
```

docker run 명령 중 유용한 옵션이다.

|옵션|설명|
|---|---|
|-i|연결되어있지 않아도 표준입력을 유지|
|-t|가상 터미널 지정|
|-d|컨테이너 실행 시 
|--name|컨테이너 이름 지정|

### (5) docker stats
docker stats 명령으로 컨테이너의 실시간 상태를 확인할 수 있다. docker stats 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker stats --help

Usage:	docker stats [OPTIONS] [CONTAINER...]
...
```

docker stats 명령의 유용한 옵션은 다음과 같다.

|옵션|설명|
|---|---|
|-a|모든 컨테이너 확인|
|--no-stream|스트리밍 출력 하지 않음|


## 2. 컨테이너 중지 및 제거

### (1) docker stop
docker stop 명령을 사용하여 실행중인 컨테이너를 중지할 수 있다. docker stop 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker stop --help

Usage:	docker stop [OPTIONS] CONTAINER [CONTAINER...]
...
```

### (2) docker restart
docker restart 명령으로 컨테이너를 재시작할 수 있다. docker restart 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker restart --help

Usage:	docker restart [OPTIONS] CONTAINER [CONTAINER...]
...
```

### (3) docker rm
docker rm 명령으로 컨테이너를 삭제할 수 있다. docker rm 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker rm --help

Usage:	docker rm [OPTIONS] CONTAINER [CONTAINER...]
...
```

## 3. 컨테이너 실행시 유용한 설정 옵션

- `-e` : 환경변수
- `--cpus` : cpu 사용량 제한
- `--memory` : 메모리 사용량 제한