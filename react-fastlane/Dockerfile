FROM deredy/react-native

RUN apt-get update -y && \
  apt-get install -y --no-install-recommends software-properties-common build-essential && \
  apt-add-repository ppa:brightbox/ruby-ng && \
  apt-get update && \
  apt-get install -y  --no-install-recommends ruby2.4 ruby-dev ruby2.4-dev && \
  gem install fastlane

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
