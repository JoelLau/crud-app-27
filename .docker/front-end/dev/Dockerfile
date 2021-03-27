# Builder (Node) Image
FROM node:15-alpine3.10

RUN apk update && apk add --no-cache make git

WORKDIR /usr/src/app

# install
RUN rm -rf node_modules dist
RUN npm install

# build
EXPOSE 4200
RUN npm install -g @angular/cli
CMD ["ng","serve","--host", "0.0.0.0", "--disable-host-check"]