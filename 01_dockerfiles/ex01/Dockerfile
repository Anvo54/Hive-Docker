FROM debian:latest
RUN apt update -y && apt upgrade -y && useradd teamspeak && su teamspeak && apt install wget -y && apt install bzip2 -y &&\
	wget https://files.teamspeak-services.com/releases/server/3.11.0/teamspeak3-server_linux_amd64-3.11.0.tar.bz2 && \
	tar xjf teamspeak3-server_linux_amd64-3.11.0.tar.bz2 && rm teamspeak3-server_linux_amd64-3.11.0.tar.bz2 && \
	cd teamspeak3-server_linux_amd64 && touch .ts3server_license_accepted
EXPOSE 9987/udp 10011 30033
CMD cd teamspeak3-server_linux_amd64 && \
	./ts3server_startscript.sh start && \
	tail -f /bin/bash
