
# README

To Build an Instagram
[![Gem Version](https://img.shields.io/gem/v/guard.svg?style=flat)](https://rubygems.org/gems/guard) [![Build Status](https://travis-ci.org/guard/guard.svg?branch=master)](https://travis-ci.org/guard/guard) [![Dependency Status](https://gemnasium.com/guard/guard.svg)](https://gemnasium.com/guard/guard) [![Code Climate](https://codeclimate.com/github/guard/guard/badges/gpa.svg)](https://codeclimate.com/github/guard/guard) [![Test Coverage](https://codeclimate.com/github/guard/guard/badges/coverage.svg)](https://codeclimate.com/github/guard/guard) [![Inline docs](http://inch-ci.org/github/guard/guard.svg)](http://inch-ci.org/github/guard/guard)

1- copy gem 'devise' to gem file , bundle install

2-rails generate devise:install

3- Copy config.action_mailer.default_url_options = { host: 'localhost', port: 3000 } in to :config/environments/development.rb

4- rails g devise User

5- rake db:migrate (because of Devise mailer)

6- gem 'bootstrap-sass', '~> 3.3.6'  from git , bundle install

7- Import Bootstrap styles in app/assets/stylesheets/application.scss:
```
@import "bootstrap-sprockets";
@import "bootstrap";

```
 and change .css to .scss

 8- Bootstrap JavaScript depends on jQuery. If you're using Rails 5.1+, add the jquery-rails gem to your Gemfile:

gem 'jquery-rails'
$ bundle install
Require Bootstrap Javascripts in app/assets/javascripts/application.js:

```
//= require jquery
//= require bootstrap-sprockets
```

9- Using Bootstrap pre built pages

10- rails g model Post

11- rails g model Post description:text

12-rails g controller Posts

13- rake db:migrate

14- rails g controller Posts new index show

15- Routes add :
```
root 'post#index'
resources :posts
```
16- add and change navbar (application.html.rb) like these:
```
* add : <%= link_to "instagram", root_url, class:"navbar-brand"%>
* add : <%= link_to "New Post", new_post_path %>
* add :
* <% if current_user%>
* <%else%>
* <%end%>
* add : <%= link_to "Login", new_user_session_path %>
* add : <%= link_to "Register", new_user_registration_path %>
* remove useless link
* to find the path of the links do not forget to see: rails routes
```
17- How to make a form for "posts"
* views>layouts>posts>new.html.erb
```
* New Post ( in <h1>)
* <%= form_for @post do |f| %>
* <%= f.label :description %>
* <%= f.text_area :description %>
* <br>
* <%= f.submit%>
* <% end%>
```
* controllers>post_controller.rb
```
* @post = Post.new
```
18- Ability to sign out:
```
* <% if current_user%>
* <li>
* <%= link_to "Log out", destroy_user_session_path,
* method: :delete, confirm: "Are you sure?" %>
* </li>
* <%else%>
* <%end%>
```
19- gem "paperclip", "~> 5.0.0"
20- rails g paperclip post image  and then rake db:migrate
21- models.post.rb=>
```
has_attached_file :avatar, styles: { medium: "300x300>", thumb: "100x100>" },       default_url: "/images/:style/missing.png"
validates_attachment_content_type :avatar, content_type: /\Aimage\/.*\z/
```
* change all avatar to image and resolution to 500*500

22- view> posts> new.html.erb
```
<h1>New Post</h1>

<%= form_for @post, html: {multipart: true} do |f| %>
<%= f.label :image%>
<%= f.file_field :image%>
<br>
<%= f.label :description %>
<%= f.text_area :description %>
<br>
<%= f.submit%>
<% end%>
```
23-controllers>post_controller.rb

```
  def new
    @post = Post.new
  end

  def index
  end

  def show
  end

  def create
    @post=Post.new(permit_post)
    if @post.save
      flash[:success] = "Success!"
      redirect_to post_path(@post)
    else
      flash[:error] = @post.errors.full_messages
      redirect_to new_post_path
    end
  end
  private
  def permit_post
    params.require(:post).permit(:image, :description)
  end
end
```
24-
