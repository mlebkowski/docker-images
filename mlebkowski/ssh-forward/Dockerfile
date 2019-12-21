FROM alpine:3.2

RUN apk add --update openssh-client && rm -rf /var/cache/apk/*

ENV FORWARD_HOST localhost
ENV SSH_HOST localhost
ENV ID_RSA_PATH /root/id_rsa
ENV PORT 3306

CMD mkdir -p /root/.ssh \
    && cp "$ID_RSA_PATH" /root/.ssh/id_rsa \
    && chmod -R a-rwx /root/.ssh \
    && ssh -vv \
        -o StrictHostKeyChecking=no \
        -o ServerAliveInterval=60 \
        -o ServerAliveCountMax=3 \
        -N $SSH_HOST -L *:$PORT:$FORWARD_HOST:$PORT
