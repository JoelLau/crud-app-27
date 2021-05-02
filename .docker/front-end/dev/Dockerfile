# Builder (Node) Image
FROM node:15-alpine3.10

RUN apk update && apk add --no-cache make git

WORKDIR /usr/src/app

# install
COPY ./front-end .
RUN npm install -g npm
RUN rm -rf node_modules
RUN rm -rf dist
RUN npm install
RUN npm update

# build
EXPOSE 4200
RUN npm install -g @angular/cli
CMD ["ng","serve","--host", "0.0.0.0", "--disable-host-check"]