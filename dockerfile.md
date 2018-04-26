# Dockerfile

An image is defined using a Dockerfile

A Dockerfile is human readable text file with a list of steps that describe how to build the image, such as

* configure the system
* copy the application files
* install the required depencies

### Common Dockerfile instructions

The table below lists the most common used instructions for a Dockerfile.

| Instruction | Details |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `FROM` | When creating a Dockerfile it should always specify **on which image it should be based**. This is achieved using the FROM instruction. A common source of images to base your image on is Dockerhub. Specify a specific version using a color `:<version_number>`use the latest image using `:latest` |
| `WORKDIR` | Sets de **default working directory** for instructions that follow. If needed, the directory will be created. |
| `RUN` | Allows the **execution of commands in the shell**. This is for example used to install applications, libraries or other dependencies. Each RUN instruction will execute any commands in a new layer on top of the current image and commit the results |
| `ENV` | Sets an **environmental variable **to a specified value. These **will persist **when a container is run from the resulting image. |
| `COPY <src> <dst>` | C**opies files or directories** from the host file system to the image. Relative paths can be used for both the source as the destination. Relative paths in the destination are relative to the working directory. |
| `EXPOSE <port>/<udp,tcp>` | Indicates that the **container listens on the specified ports** when running. If no protocol is specified, than it **defaults to tcp**. Do note that the EXPOSE instruction does not actually publish the port - this needs to be done when running the container. |
| ` CMD ["executable","arg1","arg2"]` | Specifies the application or **executable process that needs to be run** in the container when started. Only a single CMD instruction can be specified within a Dockerfile. |

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



