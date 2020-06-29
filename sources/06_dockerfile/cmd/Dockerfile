## 예제1 : exec 방식

FROM alpine
CMD ["echo", "$PATH"]

## 예제2 : shell 방식

FROM alpine
CMD echo $PATH

## 예제3 : exec 방식에서 변수처리
FROM alpine
CMD ["/bin/sh", "-c", "echo $PATH"]