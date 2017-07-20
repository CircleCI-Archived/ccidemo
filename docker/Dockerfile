FROM ruby:2.4.1-alpine

LABEL maintainer="ricardo@feliciano.tech"

ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH

RUN apk add --update --no-cache --virtual build-dependencies

RUN apk add --update --no-cache \
		bash \
		build-base \
		ca-certificates \
		git \
		go \
		libcurl \
		libxml2-dev \
		libxslt-dev \
		openssh \
		py-pip \
		rsync \
		wget && \
	gem install \
		asciidoctor \
		html-proofer \
		nokogiri \
		--no-document && \
	pip install --upgrade pip && \
	pip install docutils && \
	apk del build-dependencies && \
	rm /var/cache/apk/*

CMD ["htmlproofer","--help"]

EXPOSE 1313
