# BASE
ARG NODE_VERSION=20
FROM node:${NODE_VERSION} AS base-debian
EXPOSE 1337

FROM base-debian

ARG STRAPI_VERSION=latest

RUN yarn global add create-strapi-app

RUN mkdir -p /srv/app && chown 1000:1000 -R /srv/app

WORKDIR /srv/app

VOLUME /srv/app

COPY docker-entrypoint.sh /usr/local/bin/

RUN chmod 777 /usr/local/bin/docker-entrypoint.sh && ln -s /usr/local/bin/docker-entrypoint.sh

ENTRYPOINT ["docker-entrypoint.sh"]

CMD ["create-strapi-app"]
