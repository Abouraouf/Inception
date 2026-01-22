FROM debian:bullseye

RUN apt update -y && apt upgrade -y && apt install -y nginx openssl

RUN mkdir -p /etc/nginx/ssl

# Note: DOMAIN_NAME must be passed as an ARG during build to work here
ARG DOMAIN_NAME=irabhi.42.fr

RUN openssl req -x509 -nodes -days 1365 -newkey rsa:2048 \
    -keyout /etc/nginx/ssl/server.key \
    -out /etc/nginx/ssl/server.crt \
    -subj "/CN=${DOMAIN_NAME}"

# Ensure Nginx config is in the right place 
COPY conf/default /etc/nginx/sites-available/default
RUN ln -sf /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default

RUN mkdir -p /var/www/html/about
RUN chown -R www-data:www-data /var/www/html/about

# daemon off; keeps the container running in the foreground
CMD ["nginx", "-g", "daemon off;"]