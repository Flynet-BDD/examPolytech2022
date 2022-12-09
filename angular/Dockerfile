FROM node:10 AS builder

WORKDIR /usr/src/app

COPY . .

RUN npm install && npm run build

FROM nginx

EXPOSE 80
ENV BACKEND_URL_ENV_VAR=localhost

LABEL maintainer="Theo NOEL"

COPY nginx/ /etc/nginx/
COPY sed.sh /docker-entrypoint.d/sed.sh
RUN chmod +x /docker-entrypoint.d/sed.sh

COPY --from=builder /usr/src/app/dist /usr/share/nginx/html