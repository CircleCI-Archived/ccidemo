FROM ruby:2.4.1

ENV LANG C.UTF-8
ENV GOLANG_VERSION 1.8.3
ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH

RUN apt-get update && apt-get install -y --no-install-recommends \
		git \
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
	pip install docutils

RUN wget -O go.tar.gz https://storage.googleapis.com/golang/go1.8.3.linux-amd64.tar.gz && \
		tar -C /usr/local -xzf go.tar.gz && \
		rm go.tar.gz

RUN go get github.com/jstemmer/go-junit-report

CMD ["htmlproofer","--help"]

EXPOSE 1313
