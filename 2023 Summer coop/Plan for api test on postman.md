apiary.apib
	Attribute 
		TenantID
		Status
	Body
		Mutation(?)
WidgetsMapper.xml
	Something similar, currently not familliar 
	Def need to use INNER JOIN  to verify TenantID(maybe not?)
schema.graphqls
	Same stuff as type Seller I think
	extend MutationMessage + some other things?
CreatePatiscoG4Sys-table.sql
- Status
- TenantID

Add stuff on WidgetsMapper.java and WidgetsFetcher.java? 
Not sure if i need this for WidgetsMapper.xml

Do i need to change/add stuff in GraphQLProvider.java under RunTimeWiring BuildWiring()?
maybe not type but prolly .dataFetcher()

can fetch if its on or off
how to fetch how MANY on or off

