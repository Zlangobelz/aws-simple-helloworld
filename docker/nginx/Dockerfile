FROM nginx:latest

RUN apt-get update

RUN rm /etc/nginx/conf.d/default.conf
COPY ./docker/nginx/conf/site.conf /etc/nginx/conf.d/

COPY ./src/ /var/www

EXPOSE 8000

CMD ["nginx", "-g", "daemon off;"]