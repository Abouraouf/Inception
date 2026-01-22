FROM debian:bullseye

RUN apt update -y && apt upgrade -y && apt install mariadb-server -y

# Fix: Ensure the directory for the socket file exists and belongs to mysql user
RUN mkdir -p /run/mysqld && chown -R mysql:mysql /run/mysqld

COPY tools/mariadb.sh /tmp/mariadb.sh
# Fix: Be specific about copying the cnf file to the right directory [cite: 1]
COPY conf/50-server.cnf /etc/mysql/mariadb.conf.d/50-server.cnf

RUN chmod +x /tmp/mariadb.sh

# Using the script as the entrypoint is better for initialization
ENTRYPOINT ["/tmp/mariadb.sh"]