# README

To Build an Instagram

1- copy gem 'devise' to gem file , bundle install

2-rails generate devise:install

3- Copy config.action_mailer.default_url_options = { host: 'localhost', port: 3000 } in to :config/environments/development.rb

4- rails g devise User

5- rake db:migrate (because of Devise mailer)
