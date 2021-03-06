# AUTOGENERATED FILE
FROM balenalib/generic-aarch64-alpine:3.8-build

ENV NODE_VERSION 10.10.0
ENV YARN_VERSION 1.6.0

# Install dependencies
RUN apk add --no-cache libgcc libstdc++ libuv libcrypto1.0 libssl1.0

RUN for key in \
	6A010C5166006599AA17F08146C2130DFD2497F5 \
	; do \
		gpg --keyserver pgp.mit.edu --recv-keys "$key" || \
		gpg --keyserver keyserver.pgp.com --recv-keys "$key" || \
		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key" ; \
	done \
	&& curl -SLO "http://resin-packages.s3.amazonaws.com/node/v$NODE_VERSION/node-v$NODE_VERSION-linux-alpine-aarch64.tar.gz" \
	&& echo "60106d4934d5af9a122ae3a6a15e1c8e3ca7e832a6c16ef5b21a9addcc340f95  node-v$NODE_VERSION-linux-alpine-aarch64.tar.gz" | sha256sum -c - \
	&& tar -xzf "node-v$NODE_VERSION-linux-alpine-aarch64.tar.gz" -C /usr/local --strip-components=1 \
	&& rm "node-v$NODE_VERSION-linux-alpine-aarch64.tar.gz" \
	&& curl -fSLO --compressed "https://yarnpkg.com/downloads/$YARN_VERSION/yarn-v$YARN_VERSION.tar.gz" \
	&& curl -fSLO --compressed "https://yarnpkg.com/downloads/$YARN_VERSION/yarn-v$YARN_VERSION.tar.gz.asc" \
	&& gpg --batch --verify yarn-v$YARN_VERSION.tar.gz.asc yarn-v$YARN_VERSION.tar.gz \
	&& mkdir -p /opt/yarn \
	&& tar -xzf yarn-v$YARN_VERSION.tar.gz -C /opt/yarn --strip-components=1 \
	&& ln -s /opt/yarn/bin/yarn /usr/local/bin/yarn \
	&& ln -s /opt/yarn/bin/yarn /usr/local/bin/yarnpkg \
	&& rm yarn-v$YARN_VERSION.tar.gz.asc yarn-v$YARN_VERSION.tar.gz \
	&& npm config set unsafe-perm true -g --unsafe-perm \
	&& rm -rf /tmp/*

CMD ["echo","'No CMD command was set in Dockerfile! Details about CMD command could be found in Dockerfile Guide section in our Docs. Here's the link: https://balena.io/docs"]

RUN [ ! -d /.balena ] && mkdir /.balena; echo 'Here are a few details about this Docker image (For more information please visit https://www.balena.io/docs/reference/base-images/base-images/): \nArchitecture: ARM v8 \nOS: Alpine Linux 3.8 \nVariant: build variant \nDevice: Generic AARCH64 \nDevice-type:generic-aarch64 \nDefault variable(s): UDEV=off \nThe following software stack is preinstalled: \nNode.js v10.10.0, Yarn v1.6.0 \nExtra features: \n- Easy way to install packages with `install_packages <package-name>` command \n- Run anywhere with cross-build feature  (for ARM only)' > /.balena/image-info

ONBUILD RUN cat /.balena/image-info