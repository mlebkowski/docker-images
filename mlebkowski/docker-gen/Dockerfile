FROM jwilder/docker-gen

RUN apk --no-cache add curl
ADD restart-container /bin/restart-container
RUN chmod +x /bin/restart-container

ENV DOCKER_ENGINE_VERSION=1.39
