## Setup your React on Rails application & install dependencies

#### Notes for this guide
*T: indicates use of terminal*

*A: indicates use of Atom (or other IDE)*

*Words in all caps (e.g. PROJECTNAME) indicate something to be replaced*

#### Create a new Rails application
In the terminal, navigate to the appropriate directory (e.g. ~/desktop)

T: ```rails new PROJECTNAME -T -d prostgresql```

  **-T** Instructs rails to drop the default testing suite minitest (we will be utilizing rspec)

  **-d postgresql** Instructs rails to utilize postgresql (not SQLlite which is the default)

T: ```cd PROJECTNAME```

#### rspec & byebug
We will be using rspec testing suite & byebug to provide us testing tools for completing our application.

A: navigate to PROJECTNAME/Gemfile

A: insert the below:

        group :development, :test do
            gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
            gem 'rspec-rails', '~> 3.8' # <--- Added this gem
        end

T: ```bundle install```

T: ```rails generate rspec:install```

#### React
T: ```bundle add webpacker react-rails```

T: ```bundle install```

T: ```rails webpacker:install```

T: ```rails webpacker:install:react```

T: ```rails generate react:install```

T: ```yarn install```


#### CORS

In order to enable fetch, we need CORS. CORS (Cross Origin Resource Scripting) is a security protocol browsers implement that helps protect users from cross-site scripting.

T: ```bundle add rack-cors```

A: Create a file inside the  /app/config/initializers/ directory named cors.rb

A: insert the below:

    Rails.application.config.middleware.insert_before 0, Rack::Cors do
      allow do
        origins '*'  # <- change this to allow requests from any domain while in development. resource '*',
        headers: :any,
        methods: [:get, :post, :put, :patch, :delete, :options, :head]
        end
    end
