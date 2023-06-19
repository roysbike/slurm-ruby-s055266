FROM ruby:2.6.4

# Install Node.js
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs

ARG SECRET_KEY_BASE=$SECRET_KEY_BASE
ARG RAILS_ENV=$RAILS_ENV
ARG RAILS_LOG_TO_STOUT=$RAILS_LOG_TO_STDOUT
ARG DB_HOST=$DB_HOST
ARG DB_PORT=$DB_PORT
ARG DB_NAME=$DB_NAME
ARG DB_USER=$DB_USER
ARG DB_PASSWORD=$DB_PASSWORD

COPY ./xpaste_practicum /app
WORKDIR /app
#RUN bundle clean --force
RUN bundle config build.nokogiri --use-system-libraries
RUN bundle install --clean --no-cache --without development

ENV SECRET_KEY_BASE=$SECRET_KEY_BASE
ENV RAILS_ENV=$RAILS_ENV
ENV RAILS_LOG_TO_STOUT=$RAILS_LOG_TO_STDOUT
ENV DB_HOST=$DB_HOST
ENV DB_PORT=$DB_PORT
ENV DB_NAME=$DB_NAME
ENV DB_USER=$DB_USER
ENV DB_PASSWORD=$DB_PASSWORD

CMD bundle exec rake db:migrate && bundle exec puma -b unix:///var/run/puma/puma.sock -e $RAILS_ENV config.ru