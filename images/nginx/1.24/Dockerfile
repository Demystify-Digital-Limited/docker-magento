FROM nginx:1.24-alpine

ARG APP_ID=1000

RUN addgroup -g "$APP_ID" app \
&& adduser -G app -u "$APP_ID" -h /var/www -s /bin/bash -S app
RUN touch /var/run/nginx.pid
RUN mkdir /sock

ARG TARGETARCH

COPY ./conf/nginx.conf /etc/nginx/
COPY ./conf/default.conf /etc/nginx/conf.d/

RUN mkdir -p /etc/nginx/html /var/www/html \
  && chown -R app:app /etc/nginx /var/www /var/cache/nginx /var/run/nginx.pid /sock

EXPOSE 8443

USER app:app

VOLUME /var/www
VOLUME /etc/nginx

WORKDIR /var/www/html
