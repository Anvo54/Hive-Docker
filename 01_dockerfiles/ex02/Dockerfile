FROM ruby
RUN apt update -y && apt upgrade -y && apt install nodejs -y
RUN mkdir /opt/app
	ONBUILD WORKDIR  /opt/app
	ONBUILD RUN echo "source 'https://rubygems.org'\ngem 'rails', '~>5'" > /opt/app/Gemfile \
			&& touch /opt/app/Gemfile.lock \
			&& bundle install \
			&& curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg |  apt-key add - \
			&& echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list \
			&& apt update && apt install yarn \
			&& gem install rails \
			&& cd .. \
			&& rails new app \
			&& cd app \
			&& rake db:migrate
