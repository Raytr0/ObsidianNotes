GraphQLProvider.java:
Seems to be using "schema.graphqls" to display messages and data information regarding the website and the user

WidgetsFetcher.java:
Seems to check for user access permissions to display what types of widgets
also checks for language
Multiple error checks and some potential fallbacks so it doesn't brick all the time
Has a debugging mode as well?
logic nets for exceptions and fallbacks

WidgetsMapper.java:
Seems to check for seller and tenant(buyer?) and displays the catalog accordingly?
not too sure

Catalog.java:
getter and setter methods for catalog information with user info

Seller.java:
Getter and Setter methods for seller

MyService.java:
Managing the display and the updates done to the catalog

MyApplication.java:
Main method, has language aspects, seems to run everything to make the site work

Tenant, Buyer, Seller, User whats the difference?

WidgetsMapper.xml:
mysql command things

logback.xml:
7 day log history