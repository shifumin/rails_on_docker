FROM ruby:2.4.2
ENV LANG C.UTF-8

RUN apt-get update -qq && \
    apt-get install -y build-essential \
                       nodejs \
                       mysql-client \
                       --no-install-recommends

RUN mkdir /rails_app
WORKDIR /rails_app

COPY Gemfile /rails_app/Gemfile
COPY Gemfile.lock /rails_app/Gemfile.lock

RUN bundle install
COPY . /rails_app
