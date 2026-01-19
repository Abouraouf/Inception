FROM debian:latest

#RUN apt update && apt install -y php-fpm
RUN apt update -y && apt upgrade -y &&  apt install php php-fpm -y


CMD ["php-fpm8.4", "-F"]

#what is the "php-fpm8.4", "F" and php-fp