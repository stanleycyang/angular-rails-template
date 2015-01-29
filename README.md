##Rails side:

###Remove Turbolinks:

Remove from Gemfile:

	-- gem turbolinks
	
Convert app/views/application.html.erb:

	<%= stylesheet_link_tag    "application"%>
	<%= javascript_include_tag "application"%>
	
Remove from app/assets/javascripts/application.js:

	//= require turbolinks
	
###Remove JBuilder

from Gemfile

	gem 'jbuilder', '~> 1.2'

###Add ActiveModelSerializers & AngularJS-Rails gems:

	gem 'active_model_serializers'
	gem 'angularjs-rails'
	gem 'bcrypt'

###Setup Active Model Serializers to work with Angular

Add a file called active_model_serializers.rb in config/initializers with this code:

	ActiveSupport.on_load(:active_model_serializers) do
	  # Disable for all serializers (except ArraySerializer)
	  ActiveModel::Serializer.root = false
	
	  # Disable for ArraySerializer
	  ActiveModel::ArraySerializer.root = false
	end


6. Generate a serializer, edit it.

rails g serializer your-model-name
Add attributes that should be part of the json.

Angular Side

###Add angular javascript

Include in your application.js:

	//= require angular
	//= require angular-resource
	
###Setup a view with an Angular app


	rails g controller home index

Then set your root to:

	root 'home#index'

Go into application and add ng-app to the <html> tag

	<html ng-app>

Go into views/home/index.html.erb

	{{3 + 4}}

If it returns 7, congratulations!! You have successful set up angularJS and rails together

	