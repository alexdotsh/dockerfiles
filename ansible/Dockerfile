FROM alpine:3.11.5

RUN builddeps=' \
		python3-dev \
		py2-pip \
		musl-dev \
		openssl-dev \
		libffi-dev \
		gcc \
		' \
	&& apk --no-cache --update add \
	        ca-certificates \
	        python3 \
	        $builddeps \
	        && pip3 install --upgrade pip setuptools \
	        && pip3 install \
		    ansible \
		    six \
	&& apk del --purge $builddeps

ENTRYPOINT [ "ansible" ]
