FROM ruby:3.0.0

RUN apt-get update -qq && apt-get install -y nodejs sudo

RUN gem install rails

RUN rails new testing_project
WORKDIR /testing_project

# install yarn, required for webpacker
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN sudo apt-get update && sudo apt-get install yarn

RUN rails webpacker:install

RUN bundle install

EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]