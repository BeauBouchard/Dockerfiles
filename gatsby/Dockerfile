FROM mhart/alpine-node:12.12.0

EXPOSE 8000

RUN apk update && \
    apk add --update --repository http://dl-3.alpinelinux.org/alpine/edge/testing vips-tools vips-dev fftw-dev gcc g++ make libc6-compat && \
    apk add git && \
    apk add python && \
    rm -rf /var/cache/apk/*

# Creating working directory
RUN mkdir -p /usr/src/app

# Copy files to working directory
COPY . /usr/src/app/

# Change working directory
WORKDIR /usr/src/app

# Create Distribution
RUN npm install --global gatsby --no-optional gatsby@1.9 


VOLUME /usr/src/app

COPY ./fluffer.sh /

RUN chmod +x /fluffer.sh

ENTRYPOINT ["/fluffer.sh"]




