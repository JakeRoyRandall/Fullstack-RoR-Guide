## React in Rails

```bundle add react-rails```

```bundle install```

Install Webpacker

```rails webpacker:install```

```rails webpacker:install:react```

```rails generate react:install```

Generate a new React component

```rails g react:component App```

Update the new Component

```cat app/javascript/components/App.js```

Delete PropTypes line
Convert to component React

    import React from "react"
    import PropTypes from "prop-types"
    class HelloWorld extends React.Component {
      render () {
        return (
          <h1>Hello World</h1>
        );
      }
    }

    export default App

Create a Homepage and add the Route to Rails

```rails g controller Pages```

inside of config/routes.rb

    Rails.application.routes.draw do
      root to: "pages#index"
    end

Add homepage, and React Component
inside of app/views/pages/index.html.erb

```app/views/pages/index.html.erb```
