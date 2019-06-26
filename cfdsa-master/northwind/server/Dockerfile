# base image
FROM node:latest

#define env variable
ENV DB_HOST=nwdb DB_PORT=3306 \
    DB_USER=root DB_PASSWORD=changeit \
    APP_PORT=3000 APP_DIR=/dataApp

#create APP_DIR, and cd inside
WORKDIR ${APP_DIR}

#copy file to APP_DIR
ADD main.js .
ADD package.json .
ADD public public
ADD views views
ADD config config

#install libraries from package.json
RUN npm install

EXPOSE ${APP_PORT}

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

#how should the image be executed
ENTRYPOINT [ "node", "main.js" ]