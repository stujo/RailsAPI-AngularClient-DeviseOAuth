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
      - database: ``` skeleton-rails-api_development ```
      - database: ```skeleton-rails-api_test```
      - database: ```skeleton-rails-api_production```
      - username: ```skeleton-rails-api```
      - password: ```<%= ENV['SKELETON-RAILS-API_DATABASE_PASSWORD'] %>```
    - In /config/initializers/secret_token.rb rename:
      ```SkeletonRailsApi::Application.config.secret_token = 'SOME SECRET TOKEN'```
  - Make sure your Gemfile contains the OAuth gem of choice i.e:
      ```
      gem 'omniauth-github'
      gem 'omniauth-facebook'
      gem 'omniauth-google-oauth2'
      ```
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

## Angular Client
  This was also left as bare bones as possible and only includes the necessary code/scripts to work with Device/OAuth/RailsAPI. I have included JQuery, however that is technically not necessary.
### Setup
- Renaming
  - In index HTML
    - ```<html lang='en' ng-app='yourAppName'>``` yourAppName can be changed to...your apps name
    - ```<body ng-controller='mainCtrl'></body>``` mainCtrl can be changed but not necessary
    - ```<button ng-click="authenticate('google')">``` 'google' should be replaced with the OAuth provider of your choice
  - In /js/controllers.js
    - ```angular.module('yourAppName', ['ng-token-auth']);``` yourAppName should match the app name you set in the HTML tag of index.html
    - ```var yourApp``` on line one, line 3, and line 9 can be changed to whatever you like.
    - ```$auth.authenticate('google')``` Google should be replaced with the OAuth Provider of choice - see https://github.com/lynndylanhurley/ng-token-auth#api
    - Put in the address of your API's server on line 5 ```apiUrl: 'http://localhost:3000'```
- Pray to the Devise, Ruby & JavaScripts Gods
- 
### Runnig the servers
From your rails api directory use ```rails s``` <br>
From your Angular root directory in terminal you can use ```python -m SimpleHTTPServer 8888``` to launch a server
### Other disclamers
You will have needed to configured your OAuth Provider (google, fb, twitter) to have the right redirect...i.e. to your local host in development <br>
In your rails API, when you move to development you **MUST** change ```origins '*'
        resource '*'``` in your /config/application.rb to be the address of your Client otherwise anyone can hit your API <br>
Any questions for the rails-api devise/oauth go to: https://github.com/lynndylanhurley/devise_token_auth <br>
Any questions for the Angular devise/oauth go to: https://github.com/lynndylanhurley/ng-token-auth <br>
**I take absolutely no responsibility for this working well or terribly in your application. You should have a general understanding of what this code is doing and use the resources linked above to understand the two clients.**
