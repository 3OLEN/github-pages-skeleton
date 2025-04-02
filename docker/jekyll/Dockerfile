FROM rubylang/ruby:3.2

RUN apt-get update  \
    && apt-get install -y \
        gcc \
        g++ \
        make \
    && apt-get clean

RUN gem install minima jekyll bundler
