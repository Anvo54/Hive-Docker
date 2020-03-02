FROM debian
RUN apt update -y && apt upgrade -y
RUN apt-get install -y curl openssh-server ca-certificates
RUN apt install -y postfix
RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN apt-get install gitlab-ce
RUN mkdir -p /etc/gitlab/ssl
RUN chmod 755 /etc/gitlab/ssl
RUN openssl req -x509 -nodes -days 365 -newkey rsa:4096 \
	-subj /C=FI/ST=HEL/L=Helsinki/O=TheComppany/OU=TheCompany/CN=CommonNameCompany/emailAddress=avornane@student.hive.fi \
	-keyout /etc/gitlab/ssl/selfsigned.key -out /etc/gitlab/ssl/selfsigned.crt
RUN echo "external_url \"https://192.168.99.100\"" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['redirect_http_to_https'] = true" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['ssl_certificate'] = \"/etc/gitlab/ssl/selfsigned.crt\"" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['ssl_certificate_key'] = \"/etc/gitlab/ssl/selfsigned.key\"" >> /etc/gitlab/gitlab.rb
RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 2222" >> /etc/gitlab/gitlab.rb
EXPOSE 443 80 22
CMD service ssh start && (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null
