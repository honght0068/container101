FROM node:latest

#define env variable
ENV APP_PORT=3000 APP_DIR=/fortune

#create APP_DIR, and cd inside
WORKDIR ${APP_DIR}

#copy file to APP_DIR
ADD main.js .
ADD package.json .
ADD public public
ADD views views

#install libraries from package.json
RUN npm install

EXPOSE ${APP_PORT}

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

#how should the image be executed
ENTRYPOINT [ "node", "main.js" ]

#CMD ["1000"]

