## 예제1 : exec 방식

FROM alpine
ENTRYPOINT ["echo", "$PATH"]

## 예제2 : shell 방식

FROM alpine
ENTRYPOINT echo $PATH

## 예제3 : exec방식에서 변수처리

FROM alpine
ENTRYPOINT ["/bin/sh", "-c", "echo $PATH"]