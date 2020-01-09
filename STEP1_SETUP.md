## complete full-stack app walkthrough

*T: indicates use of terminal*
*A: idicates use of Atom (or other IDE)*
*All capital letters indicate something to be replaced by the user*

### Create a React App w/ all the fixings
    In the terminal, navigate to the appropriate directory (e.g. ~/desktop)
    T: `rails new PROJECTNAME -T -d prostgresql`
        *-T instructs rails to drop the default testing suite minitest*
        *-d postgresql instructs rails to utilize postgresql and not SQLlite which is the default*
    `cd PROJECTNAME`

    **Rspec & byebug**
    A* navigate to PROJECTNAME/Gemfile
    A* include the below
    A* group :development, :test do
          gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
          gem 'rspec-rails', '~> 3.8' # <--- Added this gem
       end
    T* bundle install

    **CORS**
    **In order to enable fetch, we need CORS. CORS (Cross Origin Resource Scripting) is a security protocol browsers implement that helps protect users from cross-site scripting.
    T* bundle add rack-cors
    A* create file /app/config/initializers/cors.rb
    A* paste below:

    Rails.application.config.middleware.insert_before 0, Rack::Cors do
       allow do
        origins '*'  # <- change this to allow requests from any domain while in development.
        resource '*',
          headers: :any,
          methods: [:get, :post, :put, :patch, :delete, :options, :head]
         end
    end


    **React**
    T* bundle add webpacker react-rails
    T* bundle install
    T* rails webpacker:install
    T* rails webpacker:install:react
    T* rails generate react:install
    T* yarn install

    A* ensure <%= javascript_pack_tag 'application' %> is included in app/views/layouts/application.html.erb

rails g controller Pages

config/routes.rb

Rails.application.routes.draw do
  root to: 'pages#root'
end

rails g react:component MainApp

app/javascript/components/MainApp.js

` import React from "react"
 import PropTypes from "prop-types"
 class MainApp extends React.Component {
   render () {
     return (
       <h1>React MainApp Component</h1>
     );
   }
 }

 export default MainApp`

Place Component on Page

app/views/pages/root.html.erb

: <h1>Single Page App Example</h1>
: <%= react_component('MainApp') %>
