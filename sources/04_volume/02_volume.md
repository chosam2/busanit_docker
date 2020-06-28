# Volume 예제

## 3. --volumes-from 옵션 사용

### 문제

- 볼륨 이름 : vf-vol1
- 컨테이너1 : vf-vol1을 사용하는 vf-web1 컨테이너 생성
- 연결경로 : `/usr/local/apache2/htdocs/`
- 컨테이너2 : `--volumes-from` 옵션을 사용해 vf-web1 컨테이너와 볼륨 공유하는 컨테이너 생성

### 풀이

```bash
docker volume create vf-vol1
```

```bash
docker run -d --name vf-web1 -v vf-vol1:/usr/local/apache2/htdocs/ httpd
```

```bash
docker run -d --name vf-web1 --volumes-from vf-web1 httpd
```