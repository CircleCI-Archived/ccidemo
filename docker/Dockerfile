FROM ruby:2.4.1

ENV GOLANG_VERSION 1.8.3
ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH

RUN apt-get update && apt-get install -y --no-install-recommends \
		git \
		golang \
		libxml2-dev \
		libxslt-dev \
		openssh-client \
		python-pip \
		rsync \
		wget && \
	gem install \
		asciidoctor \
		html-proofer \
		nokogiri \
		--no-document && \
	pip install --upgrade pip && \
	pip install docutils && \

CMD ["htmlproofer","--help"]

EXPOSE 1313
