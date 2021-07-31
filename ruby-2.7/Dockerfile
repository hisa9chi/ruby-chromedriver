# base image
FROM ruby:2.7.4

# set environment
ENV CHROME_VERSION 92.0.4515.107-1
ENV CHROME_DRIVER_VERSION 92.0.4515.107

# install chrome
RUN apt-get update && \
    apt-get install -y --no-install-recommends -y --no-install-recommends \
              wget \
              unzip \
              apt-utils \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -  \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list \
    && apt-get update && apt-get install -y --no-install-recommends google-chrome-stable=$CHROME_VERSION \
    && rm -rf /var/lib/apt/lists/*

# install chromedriver
RUN wget -O /tmp/chromedriver.zip http://chromedriver.storage.googleapis.com/$CHROME_DRIVER_VERSION/chromedriver_linux64.zip \
    && unzip /tmp/chromedriver.zip chromedriver -d /usr/bin/ \
    && rm /tmp/chromedriver.zip \
    && chmod ugo+rx /usr/bin/chromedriver \
    && apt-mark hold google-chrome-stable
