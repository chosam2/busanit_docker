FROM ubuntu:16.04
MAINTAINER Hyungwook Yu - hwyu@nobreak.co.kr
RUN apt-get update && apt-get install -y \
    cowsay  \
    fortunes \
    && rm -rf /var/lib/apt/lists/*

CMD /usr/games/fortune -a | /usr/games/cowsay