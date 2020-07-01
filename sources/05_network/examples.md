# 네트워크 연습문제

## 문제 1
bridge 드라이버를 사용하는 `my-networks` 네트워크를 생성
이때, 네트워크 대역은 `123.123.123.0/24`, gateway `123.123.123.1`로 설정
```
docker network create -d bridge --subnet 123.123.123.0/24 --gateway 123.123.123.1 my-networks
```

## 문제 2
centos 이미지를 사용하는 myos1 컨테이너를 생성
이때, my-networks 네트워크 사용
```
docker run -itd --name myos1 --network my-networks centos
```
## 문제 3
httpd 이미지를 사용하는 myweb1 컨테이너를 생성
이때, my-networks 네트워크 사용
```
docker run -itd --name myweb1 --network my-networks httpd
```
## 문제 4
myos1, myweb1 컨테이너간의 통신 확인
1. ip 주소로 확인
```
docker exec myos1 ping 123.123.123.3
```
2. container 이름으로 확인
```
docker exec myos1 ping myweb1
```