FROM node:latest
# DB_USER, DB_PASSWORD
#ENV MYSQL_ROOT_PASSWORD=changeit
ENV APP_DIR=/app APP_PORT=3000
ENV DB_USER=root
ENV DB_PASSWORD=changeit

WORKDIR ${APP_DIR}
#dun add config directory
ADD main.js .
ADD package-lock.json .
ADD package.json .

ADD public public
ADD views views
ADD config config

RUN npm install

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 \
        CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1

EXPOSE ${APP_PORT}

ENTRYPOINT [ "node", "main.js" ]
#nwapp