# 도커 명령

## 컨테이너 관리

## 1. 컨테이너 접근 및 실행

분리 모드로 실행중인 컨테이너에 접근하거나 컨테이너에 직접 접근하지 않고 명령을 실행하는 방법이 있다. docker attach와 docker exec에 대해서 알아본다.

### (1) docker attach

`docker attach` 명령으로 표준 입력, 표준출력/에러를 포함하는 컨테이너에 연결할 수 있다. docker attach 명령의 사용법은 다음과 같다.

```bash
[devops@docker ~]$ docker attach --help

Usage:  docker attach [OPTIONS] CONTAINER
...
```

다음은 os2 컨테이너에 연결하는 명령이다.
```bash
[devops@docker ~]$ docker attach os2
[root@8e5780ba8d5c /]# 
```

컨테이너 사용을 마쳤으면 `Ctrl + P + Q`를 사용하여 종료하지 않고 빠져나온다.
docker attach 명령으로 쉘 프로그램 외에 어플리케이션을 실행하고 있는 컨테이너에 접근하면 쉘이 나타날 것이라고 생각할 수 있다. 하지만 컨테이너는 기본적으로 쉘 프로그램을 실행하고 있지 않으므로 docker attach 로 접근하지 않는 것이 좋다.

### (2) docker exec
`docker exec` 명려을 사용하여 실행중인 컨테이너에서 명령을 실행할 수 있다. docker exec의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker exec --help

Usae:  docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
...
```

docker exec도 docker run과 같이 `-it` 옵션을 사용할 수 있다.

## 2. 컨테이너 프로세스 및 로그 확인
컨테이너에서 실행중인 프로세스와 로그를 확인할 수있다. docker top과 docker logs 명령에 대해서 알아본다.

### (1) docker top

`docker top` 명령으로 컨테이너에서 실행되는 프로세스의 정보를 확인할 수 있다. docker top 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker top --help

Usage:  docker top CONTAINER [ps OPTIONS]
...
```

> docker top 명령은 리눅스의 ps 옵션을 그대로 사용할 수 있다. 만약 지정하지 않으면 `-ef` 옵션과 동일하다.

### (2) docker logs
docker logs 명령으로 컨테이너의 로그를 확인할 수 있다. docker logs 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker logs --help

Usage:  docker logs [OPTIONS] CONTAINER
...
```

## 3. 컨테이너에 파일 복사 및 확인
호스트에 있는 파일을 컨테이너에 복사하거나 반대로 작업할 수 있다. 또한 컨테이너의 파일시스템 중 어느 것이 변경되었는지 알 수 있는 명령어도 있다.

### (1) docker cp
docker cp 명령을 사용하여 호스트의 파일을 컨테이너로 복사하거나 컨테이너의 파일을 호스트로 복사할 수 있다. docker cp 명령의 사용법은 다음과 같다.

```bash
[devops@docker ~]$ docker cp --help

Usage:  docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|-       
        docker cp [OPTIONS] SRC_PATH|- CONTAINER:DEST_PATH
...
```

### (2) docker diff
docker diff 명령은 컨테이너에서 파일의 변경 상태를 체크한다. docker diff 명령의 사용법은 다음과 같다.
```bash
[devops@docker ~]$ docker diff --help

Usage:  docker diff CONTAINER
...
```

docker diff 명령으로 출력되는 파일의 상태는 다음과 같다.

|파일상태|설명|
|---|---|
|A|파일이 추가됨|
|C|파일이 변경됨|
|D|파일이 삭제됨|