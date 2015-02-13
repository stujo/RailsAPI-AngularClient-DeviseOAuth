# RailsAPI-AngularClient-DeviseOAuth

## rough-ass notes, seriously don't even.
Open rails-api in sublime
Do a search of all the files for the word ‘skeleton'
     replace SkeletonRailsApi/skeleton-rails-api with the name of your app
Bundle Install
rails g devise_token_auth:install User auth
rake db:create
rake db:migrate

create a .env file and add your keys for the api of choice
See "OmniAuth provider settings” in https://github.com/lynndylanhurley/devise_token_auth
     set the ENV variable names for the auth provider you’re using in config/initializers/omniauth.rb
