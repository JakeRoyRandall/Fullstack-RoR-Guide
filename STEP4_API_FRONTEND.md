
A* ensure <%= javascript_pack_tag 'application' %> is included in app/views/layouts/application.html.erb

rails g controller Pages

config/routes.rb

Rails.application.routes.draw do
  root to: 'pages#root'
end

rails g react:component MainApp

app/javascript/components/MainApp.js

    import React from "react"
    import PropTypes from "prop-types"
    class MainApp extends React.Component {
     render () {
       return (
         <h1>React MainApp Component</h1>
       );
     }
    }

    export default MainApp

Place Component on Page

app/views/pages/root.html.erb

 <h1>Single Page App Example</h1>
 <%= react_component('MainApp') %>
