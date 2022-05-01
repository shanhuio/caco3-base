FROM cr.shanhu.io/lib/base
MAINTAINER Shanhu Tech Inc.

ARG NPM_VERSION

RUN apk add --update nodejs npm make git openssh zip
RUN npm install -g "npm@${NPM_VERSION}"
RUN npm install -g typescript less
RUN /bin/sh -c '[[ "$(uname -m)" != amd64 ]] || npm install -g esbuild-linux-64'
RUN /bin/sh -c '[[ "$(uname -m)" != aarch64 ]] || npm install -g esbuild-linux-arm64'

RUN mkdir /usr/local/idle
COPY idle.js /usr/local/idle/idle.js

COPY ssh_known_hosts /etc/ssh/known_hosts

CMD ["/usr/bin/node", "/usr/local/idle/idle.js"]
