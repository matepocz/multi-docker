FROM node:14-14.0-alpine AS builder
USER node
RUN mkdir -p /home/node/app
WORKDIR '/home/node/app'
RUN npm install
COPY --chown=node:node . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /home/node/app/build /usr/share/nginx/html