#FROM node:10
FROM node:14

#ENV VERSION=v2.0.0

#RUN echo "deb http://archive.debian.org/debian/ stretch main contrib non-free" > /etc/apt/sources.list

RUN apt-get update
RUN apt-get install -y --no-install-recommends gettext-base xsel mc
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN npm i -g serve

#RUN  git clone -b 'v4.1.0' --single-branch https://github.com/ibi-group/datatools-ui.git /opt/datatools-ui
#RUN  git clone https://github.com/ibi-group/datatools-ui.git /opt/datatools-ui

RUN mkdir -p /opt/datatools-ui
COPY . /opt/datatools-ui

WORKDIR /opt/datatools-ui

#ADD ./config/*.yml /config/

RUN yarn

#COPY /config/settings.yml /opt/datatools-ui/configurations/default/settings.yml

EXPOSE 9966

RUN cat /etc/os-release

CMD envsubst < /config/env.yml > /opt/datatools-ui/configurations/default/env.yml && \
    $(npm bin)/mastarm build --env production && serve -p 9966

