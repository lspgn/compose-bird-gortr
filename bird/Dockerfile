FROM library/ubuntu as builder

RUN apt-get update && apt-get install -y autoconf build-essential git flex bison libncurses-dev libreadline-dev libssh-dev

RUN git clone --branch v2.0.2 https://github.com/BIRD/bird.git
COPY build.sh ./
RUN cd bird && ../build.sh

FROM library/ubuntu

RUN apt-get update && apt-get install -y adduser lsb-base ucf libc6>=2.27 libreadline7>=0.6.0 libssh-gcrypt-4>=0.8.0 libtinfo5 libssh-4 libssh2-1

COPY --from=builder /bird/bird /usr/local/sbin/bird
COPY --from=builder /bird/birdc /usr/local/sbin/birdc
COPY --from=builder /bird/birdcl /usr/local/sbin/birdcl

ENTRYPOINT [ "bird" ]