# README

To Build an Instagram

1- copy gem 'devise' to gem file , bundle install

2-rails generate devise:install

3- Copy config.action_mailer.default_url_options = { host: 'localhost', port: 3000 } in to :config/environments/development.rb

4- rails g devise User

5- rake db:migrate (because of Devise mailer)

6- gem 'bootstrap-sass', '~> 3.3.6'  from git , bundle install

7- Import Bootstrap styles in app/assets/stylesheets/application.scss:
@import "bootstrap-sprockets";
@import "bootstrap";
 and change .css to .scss

 8- Bootstrap JavaScript depends on jQuery. If you're using Rails 5.1+, add the jquery-rails gem to your Gemfile:

gem 'jquery-rails'
$ bundle install
Require Bootstrap Javascripts in app/assets/javascripts/application.js:

//= require jquery
//= require bootstrap-sprockets

9- Using Bootstrap pre built pages

10- rails g model Post

11- rails g model Post description:text

12-rails g controller Posts

13- rake db:migrate

14- rails g controller Posts new index show

15- Routes add :
root 'post#index'
resources :posts
