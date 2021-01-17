FROM ruby:3.0.0
RUN apt-get update -qq && apt-get install -y apt-utils sudo nodejs

# install yarn
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN sudo apt-get update && sudo apt-get install yarn

# RUN gem install rails -q # do we need this? OG docker rails install doesn't have it

# copy gemfile from host to container & update
COPY . /innCloud
WORKDIR /innCloud
RUN bundle install


# # Add a script to be executed every time the container starts.
# COPY entrypoint.sh /usr/bin/
# RUN chmod +x /usr/bin/entrypoint.sh
# ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

# # Start the main process.
CMD ["rails", "server", "-b", "0.0.0.0"]

# COPY ./app/Gemfile /webapp/Gemfile
# COPY ./app/Gemfile.lock /webapp/Gemfile.lock

# RUN bundle install
# COPY . /myapp

# # Add a script to be executed every time the container starts.
# COPY entrypoint.sh /usr/bin/
# RUN chmod +x /usr/bin/entrypoint.sh
# ENTRYPOINT ["entrypoint.sh"]
# EXPOSE 3000

# # Start the main process.
# CMD ["rails", "server", "-b", "0.0.0.0"]