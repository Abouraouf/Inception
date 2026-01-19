FROM debian:latest

RUN apt update && apt upgrade && apt install -y \
	nginx

CMD ["nginx", "-g", "daemon off;"]
#what does this commend do ?