FROM ruby:2.7
RUN apt-get update -qq && apt-get install -y apt-utils sudo nodejs
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN sudo apt-get update && sudo apt-get install yarn
RUN gem install rails -q
RUN rails new innCloud -q