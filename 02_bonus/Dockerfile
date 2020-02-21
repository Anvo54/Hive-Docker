FROM debian
RUN apt update && apt install -y \
	build-essential \
	vim \
	git \
	lldb
RUN mkdir /opt/app
WORKDIR /opt/app
RUN echo 'int main()\n{\n\treturn(0)\n}' > test.c
CMD bash
