FROM ruby:2.7

RUN apt-get update -qq && apt-get install -y apt-utils sudo nodejs

# install rails and bundle
RUN gem install rails bundler

WORKDIR /cis

COPY . .

# copy repo gemfile to container
# COPY Gemfile /cis/Gemfile
# COPY Gemfile.lock /cis/Gemfile.lock

# install yarn & link folder
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN sudo apt-get update && sudo apt-get install yarn

RUN bundle install

EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]

# RUN bundle install
# COPY . /myapp

# # Add a script to be executed every time the container starts.
# COPY entrypoint.sh /usr/bin/
# RUN chmod +x /usr/bin/entrypoint.sh
# ENTRYPOINT ["entrypoint.sh"]
# EXPOSE 3000

# # Start the main process.
# CMD ["rails", "server", "-b", "0.0.0.0"]