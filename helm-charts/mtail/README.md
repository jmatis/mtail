this is an initial release of mtail helm chart
it has a lot of hardcoded stuff and you have to provide your own docker container built for example with following dockerfile:

```
ARG debian_ver=11
FROM debian:${debian_ver}-slim
RUN apt update && apt upgrade -y && apt install iputils-ping iputils-tracepath curl procps -y
WORKDIR /
ADD https://github.com/google/mtail/releases/download/v3.0.0-rc50/mtail_3.0.0-rc50_Linux_x86_64.tar.gz ./
RUN tar -xzf *.tar.gz -C /usr/bin/ & rm -f /*.tar.gz
EXPOSE 3903
ENTRYPOINT ["/usr/bin/mtail"]
```
