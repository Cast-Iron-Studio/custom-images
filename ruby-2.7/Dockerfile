FROM ruby:2.7

RUN apt-get update -qq && apt-get install -y apt-utils sudo nodejs

# install rails and bundle
RUN gem install rails bundler

WORKDIR /cis

# copy repo into container
COPY . .

# install yarn & link folder
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN sudo apt-get update && sudo apt-get install yarn

# install fae
RUN rails g fae:install

# update gems
RUN bundle install

CMD ["rails", "server", "-b", "0.0.0.0"]
