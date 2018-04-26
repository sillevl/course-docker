# Dockerfile

An image is defined using a Dockerfile

A Dockerfile is human readable text file with a list of steps that describe how to build the image, such as

* configure the system
* copy the application files
* install the required depencies

### Common Dockerfile instructions

* FROM:
* `WORKDIR`: sets de **default working directory** for instructions that follow. If needed, the directory will be created.

### An example of a Dockerfile

Below is an example of a docker file used to setup a Ruby on Rails application.

```text
# The image to start from
FROM ruby:2.3

# Setup a working directory for our app
WORKDIR /app

# Install nodejs and some other required dependencies
RUN apt-get update && apt-get install -y nodejs mysql-client postgresql-client sqlite3 vim --no-install-recommends && rm -rf /var/lib/apt/lists/*

# Setup ENVIRONMENT variables
ENV RAILS_ENV production
ENV RAILS_SERVE_STATIC_FILES true
ENV RAILS_LOG_TO_STDOUT true

# Copy Gemfile
COPY Gemfile /app/
COPY Gemfile.lock /app/

# Install dependencies
RUN bundle install --without development test

# Copy the application files
COPY . .

# Expose port 3000 from the rails server
EXPOSE 3000

# The final command that starts the rails server
CMD ["rails", "server", "-b", "0.0.0.0"]

```



Building images using the dockerfile

{% hint style="info" %}
Hands on !
{% endhint %}



