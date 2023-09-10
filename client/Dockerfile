FROM node:16-alpine as builder
USER node
#WORKDIR /home/node/app
RUN mkdir -p /app
WORKDIR /app
 
COPY --chown=node:node ./package.json ./
RUN npm install
COPY --chown=node:node ./ ./
RUN npm run build 

FROM nginx
EXPOSE 3000
COPY --chown=node:node ./nginx/default.conf /etc/nginx/confi.d/default.conf
COPY --chown=node:node --from=builder /app/build /usr/share/nginx/html
