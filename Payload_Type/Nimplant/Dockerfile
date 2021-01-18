FROM nimlang/nim
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update -y 
RUN apt-get install build-essential -y 
RUN apt-get install gcc-mingw-w64 -y 
RUN nimble install winim nimcrypto sysrandom ws -y 

RUN apt-get install software-properties-common apt-utils make build-essential libssl-dev zlib1g-dev libbz2-dev \
    libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
    xz-utils tk-dev libffi-dev liblzma-dev -y

RUN apt-get update
RUN wget https://www.python.org/ftp/python/3.8.6/Python-3.8.6.tgz
RUN tar xvf Python-3.8.6.tgz
RUN Python-3.8.6/configure --with-ensurepip=install
RUN make -j8
RUN make altinstall
RUN python3.8 -m pip install aio_pika

ENTRYPOINT ["/Mythic/mythic/payload_service.sh"]