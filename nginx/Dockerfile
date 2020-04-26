FROM nginx:alpine
COPY ./nginx.conf /etc/nginx/nginx.conf
COPY ./default.conf /etc/nginx/conf.d/default.conf
RUN chown -R nginx:nginx /var/cache/nginx

ENV HEALTHCHECK_PORT=3000
USER nginx
EXPOSE 3000
