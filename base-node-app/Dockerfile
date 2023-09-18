ARG NODE_VERSION=18-alpine # 
FROM node:${NODE_VERSION}
LABEL org.opencontainers.image.version="1.0.0"
LABEL org.opencontainers.image.authors="likuan"
LABEL org.opencontainers.image.url="https://hub.docker.com/r/copymanager/base-node-app"
LABEL org.opencontainers.image.description="web应用的基础镜像"
LABEL org.opencontainers.image.documentation="https://github.com/lik778"
# 安装curl（仅在接受的Node版本是alpine类型时安装）
RUN if [ "$(echo ${NODE_VERSION} | grep -o 'alpine')" = "alpine" ]; then \
      apk add --no-cache curl; \
    fi
RUN curl -f https://get.pnpm.io/v6.16.js | node - add --global pnpm
RUN mkdir /home/app
WORKDIR /home/app
ONBUILD COPY package.json pnpm-lock.yaml ./
ONBUILD RUN pnpm -v && pnpm install --no-frozen-lockfile
ONBUILD COPY . /home/app
ONBUILD RUN pnpm run build \
             && rm -rf node_modules \
             && pnpm prune --prod /

