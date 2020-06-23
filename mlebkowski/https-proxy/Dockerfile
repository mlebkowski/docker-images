FROM node:8

VOLUME /data
ENV DATA_PATH /data
ENV FORWARD_HOST host.docker.internal
EXPOSE 443

RUN npm install --save --ignore-scripts 'nassau-https-proxy@~1.0.4'

CMD node_modules/.bin/nassau-https-proxy
