FROM node:24.4.1-alpine3.22

#Install and update system dependencies
RUN apt update -y && apt install -y supervisor npm
RUN npm install express ejs

#Prepare and setup the working directory
WORKDIR /app
COPY vsnippet .

#Copy configs
COPY config/supervisord.conf /etc/supervisord.conf

EXPOSE 1337

ENTRYPOINT [ "/usr/bin/supervisord", "-c", "/etc/supervisord.conf" ]
