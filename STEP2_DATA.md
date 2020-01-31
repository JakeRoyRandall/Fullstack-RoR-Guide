### Create Data Models & Data

#### Notes for this guide
*T: indicates use of terminal*

*A: indicates use of Atom (or other IDE)*

*Words in all caps (e.g. PROJECTNAME) indicate something to be replaced*


#### Create your database

T: ```db:create```

#### Create your resources

Before creating your data models, it is wise to think through all the data in your application and how it relates to one another. Sketching out your application's data structure in uml is a great exercise.

T: ```rails g resource MODELNAME KEY1:VALUE KEY2:VALUE...```

*g stands for generate. "rails generate resource MODELNAME" is equivalent*

Generating a resource will create and/or modify several files
* Model
* Routes
* Views
*

Once you are done generating your resources & models run

T: ```rails db:migrate```

This is a good point to set up the specs for our models.

T: ```rails g rspec:model MODELNAME```

This command will generate a spec file at spec/models/MODELNAME_spec.rb. Generate rpec models for all the data models.


#### Create development data
Navigate to
