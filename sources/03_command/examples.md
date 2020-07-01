# 0630 연습문제

## 문제 1

- centos 이미지를 사용해서 c1 컨테이너 생성
```
docker run -itd --name c1 centos
```
- c1 컨테이너에 접속해서 `/tmp/index.html` 파일 생성
`index.html`에 `Hello World` 내용 입력
```
docker exec -it c1 /bin/bash
```

```
echo 'Hello World' > /tmp/index.html
```

```
exit
```

## 문제 2

- c1 컨테이너의 /tmp/index.html 파일을 호스트의 /home/devops/index.html로 복사

```
docker cp c1:/tmp/index.html /home/devops/index.html
```

## 문제 3

- httpd 이미지를 사용해서 h1 컨테이너 생성
```
docker run -d --name h1 httpd
```
- 호스트의 /home/devops/index.html 파일을 h1 컨테이너의 index.html 파일로 복사(경로 : `/usr/local/apache2/htdocs/index.html`)
```
docker cp /home/devops/index.html h1:/usr/local/apache2/htdocs/index.html
```

## 문제 4

- h1 컨테이너의 ip 정보를 조회해서 `curl x.x.x.x` 수행
```
docker inspect h1 | grep -i ipa
```

```
curl 172.17.0.x
```

## 문제 5

- c1, h1 컨테이너의 파일 변동사항을 조회
```
docker diff c1
```
```
docker diff h1
```


# 0701 연습문제

## 문제 1

- 명령어 한 줄로 모든 컨테이너를 삭제 (실제환경에서 권장x)

```
docker rm -f $(docker ps -qa)
```

## 문제 2
- centos 이미지를 사용해 c1 컨테이너를 생성

```
docker run -itd --name c1 centos
```

## 문제 3
- httpd 이미지를 사용해 h1 컨테이너를 생성

```
docker run -d --name h1 httpd
```

## 문제 4

- h1 컨테이너의 아이이피 주소를 확인

```
docker inspect h1 | grep -i ipa
```

## 문제 5
- exec 명령을 사용해 c1 컨테이너에서 h1 컨테이너 아이피로 ping 명령을 실행

> ex) ping -c3 123.123.123.123

```
docker exec c1 ping -c3 123.123.123.123
```

6. h1 컨테이너에 접속해서 index.html파일을 수정

> ex) echo "Hello World" > index.html

```
docker exec -it h1 /bin/bash
echo "Hello World" > /usr/local/apache2/htdocs/index.html
```

7. h1 컨테이너의 아이피로 curl 명령을 통해 잘 적용되었는지 확인

```
curl 123.123.123.123
```