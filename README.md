# RailsAPI-AngularClient-DeviseOAuth

## Rails-API
  Basic Rails API install with a Postgresql database. 
  Only the necessary gems/code have been added to make Device/OAuth2 work, everything else is untouched.
<hr>
#### Setup:
  - You'll want to replace the name of this project (SkeletonRailsApi) with the name of your project and DB.
  - Renaming is not neccesary to get this going, you'll want to rename if you use this skeleton for a project
    - In /config/application.rb - Rename ```module SkeletonRailsApi``` to your app name
    - In /config/database.yml rename the following, replace skeleton-rails-api with your app name
      - database: skeleton-rails-api_development
      - database: skeleton-rails-api_test
      - database: skeleton-rails-api_production
      - username: skeleton-rails-api
      - password: <%= ENV['SKELETON-RAILS-API_DATABASE_PASSWORD'] %>
    - In /config/initializers/secret_token.rb rename:
      SkeletonRailsApi::Application.config.secret_token = '......YOUR SECRET TOKEN,'
  - Run the following:
    - Bundle install
    - rails g devise_token_auth:install User auth
      - Sets up model and migrations, db fields for User model
      - Sets up a route called auth
      - Other magic config
    - rake db:create
    - rake db:migrate
  - .ENV
    - Create a .env file in your root directory
    - add your keys for the OAuth provider of choice:
    - See "OmniAuth provider settings” in https://github.com/lynndylanhurley/devise_token_auth
    - Set the ENV variable names for the auth provider you’re using in config/initializers/omniauth.rb
  - Pray to the gods of Devise, Ruby, and JavaScripts
