FROM debian
RUN apt update -y && apt upgrade -y
RUN apt-get install -y curl openssh-server ca-certificates
RUN apt install -y postfix
RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN apt-get install gitlab-ce
CMD (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null
