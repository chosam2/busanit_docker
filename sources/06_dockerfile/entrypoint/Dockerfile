# 예제1번

# Docker 이미지 Pull
FROM alpine
# CMD 방식으로 명령 실행
CMD [ "ls", "-l" ]

# 사용법1
# docker build -t cmd:v1 .
# docker run --rm --name cmd_sample cmd:v1
# docker run --rm --name cmd_sample cmd:v1

##################################################

# 예제2번

# Docker 이미지 Pull
FROM ubuntu:16.04

# top 명령 실행
ENTRYPOINT [ "top" ]
CMD [ "-d", "10" ]


# 사용법1
# docker run -it top_sample

# 사용법2
# docker tun -it top_sample -d 2