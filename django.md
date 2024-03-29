# adding an app
*app is folder with set of python files, means component
each app fits a particular purpose
	eg. each of these could be a seperate app
		blog, forum, wiki
	# app anatomy:
		models.py:			data layer (structure of database tables and how queried)
		admin.py:			admin interface
		views.py			control layer (program logic for app, each takes http web
							request and returns a response
		tests.py			tests the app
		migrations/			holds migration files
		
	# to make app:
		navigate to folder > `python manage.py startapp nameOfApp`
		
within settings.py, under installed_apps = (, add nameOfApp with single quotes and trailing comma
# settings needed to change: 
	installed apps (when adding a new Django app), 
	templates (when adding a template for the first time), 
	staticfiles_dirs (when adding static assets for the first time).
	
	may need to change:
		Debug (set to false when not actively developing)
		DATABASES (if changing enginies, such as PostgreSQL, MySQL, etc.
		smaller settings (consult the documentation for this)
		
*models create the data layer of an app and define the database structure, as well as allowing us to query the database
models.py file contains any number of models for the django app
models use class attributes to define fields
conceptualize models as spreadsheets with fields as columns, and records as rows

`Model:
		`Field`
`Record  	|___|___|___|___|`
`		|___|___|___|___|`
`		|___|___|___|___|`
`		|___|___|___|___|`
`		|___|___|___|___|``

Inventory:
Reqs for app:
	store items wth title, description, and amount in stock
	allow admins to create, edit, or delte items
	allow users to see a list of items in stock, with details

# create the app "Inventory"
	`python manage.py startapp Inventory`

# edit models.py
`
from django.db import models
`
	# model called Item being made
`class Item(models.Model):
	title = models.CharField(max_length=200)
	description = models.TextField()
	amount = models.IntegerField()`
	
				Fields
		  [	|valueforTitle  |___|___|___|
`One Record|	|valueforAmount |___|___|___|`
`		  [	|valueforInteger|___|___|___|`
`			|_______________|___|___|___|`
`			|_______________|___|___|___|`
		
	#called inventory_item
model field types:
	numeric data:				example
		IntegerField			-1, 0, 1, 20
		DecimalField			0.5, 3.14
	Textual data:
		CharField				"Product Name" # needs max length attribute
		TextField				"To elaborate on my point..." # no input required
		EmailField				george@email.com
		URLField				any.url
	File data
		FileField				user_uploaded.docx
		ImageField				best_avatar.jpg
	Data
		BooleanField			True, False
		DateTimeField			datetime(1960, 1, 1, 8, 0, 0)
	
	# CharField with several attributes defined
		`models.CharField(max_length=10, null=True, blank=True)`
			
		Field Attribute Options:
			*max_length: defines max length
			*null: field can be stored without data if true
			*blank: allow for empty string if true
			*default: gives default attribute for field
			*choices: used to limit values to set of choices (T shirt order with choices
			of size
# Migrations
	generate scripts to change the database structure through time as code is updated
	When model is created, corresponding database table does not exist yet
		This is why we need an initial migration
			initial migration creates this table
		Migrations are needed when:
			Adding a model
			Adding a field to a model
			Removing a field
			When changing the attributes of a field
	# commands:
		`python manage.py makemigrations`
			generates migration files for later use
			uses current model fields and current database tables
				reads current models file and inspects current database state
				determines from this what changes need to be made
				makes database structure match models file
				
		`python manage.py migrate`
			runs all migrations that have not yet run
			`migrate --list` shows migrations and history
		*unapplied migration: migration that has been created but not yet run
			common source of errors during development
	# continuing with inventory example...
	`python manage.py makemigrations`
		generates migrations file for "item" model in Inventory App
	`python manage.py migrate --list`
		shows all migrations (including those made by Django when initializing)
		`[ ]` indicates that the following notated migration has not yet run
		`[x]` indicates that the following notated migration has run
	`python manage.py migrate`
		runs all unrun migrations
# Admin
	Registers models/apps
	allows signing in as site admin for administration
	#example admin.py
	`from django.ontrib import admin
	
	from .models import Item
	
	admin.site.register(Item)
	
	`
	`python manage.py createsuperuser`
		creates superuser with username email and password
	#login to the server as admin by:
		making sure `python manage.py runserver` is going
		making sure you have the admin credentials
		visiting localhost:8000/admin
		logging in there
	# admin interface
		site administration is here
		app appears as heading, models appear underneath, can manage these from here
	# adding an Item (model) to the Inventory (app)
		click Items (under Inventory)
			gets to list display page
		Top right, click add Item
		Fill in information according to what fields you have configured
	# to customize admin interface
		to admin.py, add class:
			`class ItemAdmin(admin.ModelAdmin): # new class called "ItemAdmin" inherits from the class admin, using that class's method "Model Admin"
				list_display = ['title', 'amount'] # display title and amount in list
			admin.site.register(Item, ItemAdmin) # added "ItemAdmin" here to register`
# querying data with Django ORM
	`python manage.py shell`
		opens python shell with Django initialized
	`from inventory.models import Item
	Item.objects.all()
	# returns list with items (no titles)
	items = Item.objects.all()
	item = items[0] #first item in array, item with index 0
	item.title
	#returns title of item
	item.description
	#returns description of item
	item.amount
	#returns amount associated with item
	item.id
	#returns id, which, in Django, starts at 1 for each model record
	`
	`
	item.objects.get(id=1)
	#shows item object
	item.objects.get(id=1).title
	#returns title
	item.objects.get(amount=10)
	#returns error saying that more than one is being called
	#.get is supposed to grab one, whereas .all grabs all
	`
	`
	item.objects.filter(amount=0)
	#shows items with 0
	item.objects.filter(amount=0)[0].title
	#shows item with index 0
	item.objects.exclude(amount=0)
	#excludes items that are out of stock
# using url patterns, views, templates
	Order of operations:
		URL patterns -- views -- templates
	eg: twosaints/urls.py -- announcements/views.py -- twosaints/templates
	# url patterns
		# regular expressions
			defines search patterns for strings
		# URL patterns example
			`from django.confs.urls import url
			from inventory import views
			
			urlpatterns = [
				url(r'^$', views.index, name='index'), # expression to match, view to call if matched, name used in templates
				url(r'^info/$', views.info, name="info'), # used if above doesn't match
															# more lines mean more things to match if above doesn't match
															#if no patterns match, we get a 404 error page
			]
			`
		# configuring URL patterns
			`from inventory import views
			urlpatterns = [
				url(r'^$', views.index, name='index),
				url(r'^item/(?P<id>\d+)/', views.item_detail, name='item_detail'), # uses 'named group,' specifies that digits in this area will be called "id"
				url(r'^admin/', include(admin.site.urls))
				`
			within views.py:
				`
				from django.shorcuts import render
				from django.http import HttpsResponse
				
				def index(request):
					return HttpResponse('<p>In index view</p>') #outputs this html (AND ONLY THIS) in browser once request is served
				#look up render function 
				#eg of render:
					#return render(request, 'inventory/index.html', {
					#	'items': items,
					#})
				def item_detail(request, id): #works off of line 212
					return HttpResponse('<p>In item_detail view with id {0}</p>'.format(id)) # parses the argument id (specified with named group), and passes it into view as a parameter
					
# implementing views

	in views.py
	`# make sure importing render
	from django.http import Http404
	# HttpResponse can be removed
	
	from inventory.models import Item #import the item model from the inventory app. needed to query the database
	
	# index view to show all items that are in stock
	def index(request):
		items = Item.objects.exclude(amount=0)
		return render(request, 'inventory/index.html',{
			'items': items, # 'items' string is the name of the variable to be used inside the template, where the items on the other side of the colon references line 241		
			}) #curly braces are dictionary called template's context, the keys to which will be used as variable names inside the template
	
	def item_detail(request, id):
		try:
			item = Item.objects.get(id=id)
		except Item.DoesNotExist:
			raise Http(404)('this item does not exist')
		return render(request, 'inventory/item_detail.html', {
			'item': item,})
	`
	html files go in projectrootdjango/projectrootdjango/templates/nameofApp/index.html
	configure templates by going into settings.py > find TEMPLATES variable > add under 'DIRS'
	
# template syntax
	{{ variable }}
	{% tag %}
	{{ variable|filter }}
		eg:
		`<h3>{{ item.title }}</h3>
		<!-- this makes the title of variable item an h3 within the page (see line 248)-->
	
<ul>
{% for announcement in announcements %}
<li><a href="{% url 'announcement_detail' announcement.id %}">{{ announcement.date }} -- {{ announcement.title }}</a><li>
{% endfor %}
</ul>
`
#this creates a list where announcements are looped, creating a listed item each time

#template inheritance
Django implements a base template that every template might use (meta tags, global css or javascript, structural elements (navbar))
	base.html:
		<html>
			<head>	
			</head>
			<body>
				<!-- stuff to be filled in by django comes here-->
				{% block content %}
				{% endblock content %}
			</body>
		</html>
	inventory/index.html
	{% extends "base.html" %}
		
			{% block content %}
				<h3>Items in stock</h3>
				<!-- more content -->
			{% endblock content %}
	
		





NEED TO LOOK UP/STUDY:
TEMPLATES, CONFIGURING VIEWS
				
