FROM ruby:3.0.0
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev apt-utils sudo nodejs

# install yarn
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN sudo apt-get update && sudo apt-get install yarn

RUN mkdir /app
# copy gemfile from host to container & update
WORKDIR /app
# COPY Gemfile /app/Gemfile
# COPY Gemfile.lock /app/Gemfile.lock
ADD Gemfile /app/Gemfile
ADD Gemfile.lock /app/Gemfile.lock
RUN bundle install

ADD . /innCloud

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