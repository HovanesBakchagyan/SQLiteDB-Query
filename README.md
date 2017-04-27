# SQLiteDB-Query

#_schema.json
Contains the schema for the database

#package.json
Contains the API version information as well as the table names included in the schema.

#servicedef.json
The service definition for the REST API. Contains all necessary GET, POST, PATCH, PUT, and DELETE functions for querying SQLite database

API Code Uses

getDbResources() - Get resources for this service.
/db   
Implementation Notes
  Return an array of the resources available.
Response Class (Status 200)
  Success

getDbSchemas() - List all Schemas
/db/_schema 
Implementation Notes
  Return a list of the resource identifiers.
Response Class (Status 200)
  Success

 updateDbTables() - Update (patch) one or more tables.
 /db/_schema
Implementation Notes
  Post data should be a single table definition or an array of table definitions.
Response Class (Status 200)
  Tables Updated

createDbTables() - Create one or more tables.
/db/_schema
Implementation Notes
  Post data should be a single table definition or an array of table definitions.
Response Class (Status 200)
  Tables Created
 
replaceDbTables() - Update (replace) one or more tables.
/db/_schema
Implementation Notes
  Post data should be a single table definition or an array of table definitions.
Response Class (Status 200)
  Tables Updated

 deleteDbTable() - Delete (aka drop) the given table.
 /db/_schema/{table_name}
Implementation Notes
  Careful, this drops the database table and all of its contents.
Response Class (Status 200)
  Success
 
 describeDbTable() - Retrieve table definition for the given table.
  /db/_schema/{table_name}  
Implementation Notes
  This describes the table, its fields and relations to other tables.
Response Class (Status 200)
  Table Schema

updateDbTable() - Update (patch) a table with the given properties.
 /db/_schema/{table_name}  
Implementation Notes
  Post data should be an array of field properties.
Response Class (Status 200)
  Success

 createDbTable() - Create a table with the given properties and fields.
 /db/_schema/{table_name}
Implementation Notes
  Post data should be an array of field properties.
Response Class (Status 200)
  Success

replaceDbTable() - Update (replace) a table with the given properties.
 /db/_schema/{table_name}
Implementation Notes
  Post data should be an array of field properties.
Response Class (Status 200)
  Success

 /db/_schema/{table_name}/_field
    deleteDbFields() - Delete (aka drop) the given fields.
Implementation Notes
  Careful, this drops the table column and all of its contents.
Response Class (Status 200)
  Success

 describeDbFields() - Retrieve table field definitions for the given table.
 /db/_schema/{table_name}/_field
Implementation Notes
  This describes the table's fields.
Response Class (Status 200)
  Table Fields Schema

updateDbFields() - Update (patch) table fields with the given properties.
 /db/_schema/{table_name}/_field
Implementation Notes
  Post data should be an array of field properties.
Response Class (Status 200)
  Success

createDbFields() - Create table fields.
 /db/_schema/{table_name}/_field
Implementation Notes
  Post data should be an array of fields and their properties.
Response Class (Status 200)
  Success

 /db/_schema/{table_name}/_field
    replaceDbFields() - Update (replace) table fields with the given properties.
Implementation Notes
  Post data should be an array of fields and their properties.
Response Class (Status 200)
  Success

deleteDbRelationships() - Delete the given table relationships.
 /db/_schema/{table_name}/_related
Implementation Notes
    Removes the relationships between tables.
Response Class (Status 200)
    Success
 
describeDbRelationships() - Retrieve relationships definition for the given table.
/db/_schema/{table_name}/_related      
Implementation Notes
     This describes the table relationships to other tables.
Response Class (Status 200)
    Relationships Schema
    
updateDbRelationships() - Update (patch) a table with the given properties.    
/db/_schema/{table_name}/_related
Implementation Notes
    Post data should be an array of relationship properties.
Response Class (Status 200)
    Success

createDbRelationships() - Create table relationships with the given properties.
/db/_schema/{table_name}/_related     
Implementation Notes
    Post data should be an array of relationship properties.
Response Class (Status 200)
    Success



replaceDbRelationships() - Update (replace) table relationships with the given properties.	
/db/_schema/{table_name}/_related    
Implementation Notes
    Post data should be an array of relationship properties.
Response Class (Status 200)
    Success

 

deleteDbField() - Remove the given field from the given table.	
/db/_schema/{table_name}/_field/{field_name}       
Implementation Notes
    Careful, this drops the database table field/column and all of its contents.
Response Class (Status 200)
    Success

describeDbField() - Retrieve the definition of the given field for the given table.
/db/_schema/{table_name}/_field/{field_name}    
Implementation Notes
    This describes the field and its properties.
Response Class (Status 200)
    Field Schema


updateDbField() - Update one field by identifier.
/db/_schema/{table_name}/_field/{field_name}     
Implementation Notes
    Post data should be an array of field properties for the given field.
Response Class (Status 200)
    Success

replaceDbField() - Update one field by identifier.	
/db/_schema/{table_name}/_field/{field_name}       
Implementation Notes
    Post data should be an array of field properties for the given field.
Response Class (Status 200)
    Success

deleteDbRelationship() - Remove the given relationship from the given table.
/db/_schema/{table_name}/_related/{relationship_name}      
Implementation Notes
    Removes the relationship between the tables given.
Response Class (Status 200)
    Success	

describeDbRelationship() - Retrieve the definition of the given relationship for the given table.
/db/_schema/{table_name}/_related/{relationship_name}
Implementation Notes
    This describes the relationship and its properties.
Response Class (Status 200)
    Relationship Schema
	
updateDbRelationship() - Update one relationship by identifier.
patch /db/_schema/{table_name}/_related/{relationship_name}    
Implementation Notes
    Post data should be an array of properties for the given relationship.
Response Class (Status 200)
    Success

	
replaceDbRelationship() - Update one relationship by identifier.
/db/_schema/{table_name}/_related/{relationship_name}       
Implementation Notes
    Post data should be an array of properties for the given relationship.
Response Class (Status 200)
    Success


describeDbField() - Retrieve the definition of the given field for the given table. DEPRECATED
/db/_schema/{table_name}/{field_name}        
Implementation Notes
    This describes the field and its properties.
Response Class (Status 200)
    Field Schema


updateDbField() - Update one field by identifier. DEPRECATED	
/db/_schema/{table_name}/{field_name
Implementation Notes
    Post data should be an array of field properties for the given field.
Response Class (Status 200)
    Success



	
replaceDbField() - Update one field by identifier. DEPRECATED
/db/_schema/{table_name}/{field_name}       
Implementation Notes
    Post data should be an array of field properties for the given field.
Response Class (Status 200)
    Success

getDbTables() - List all Tables
/db/_table        
Implementation Notes
    Return a list of the resource identifiers.
Response Class (Status 200)
    Success

	
deleteDbRecords() - Delete one or more records.
/db/_table/{table_name}        
Implementation Notes
    Set the ids parameter to a list of record identifying (primary key) values to delete specific records.
    Alternatively, to delete records by a large list of ids, pass the ids in the body.
    By default, only the id property of the record is returned on success, use fields to return more info. Set the filter parameter to a SQL WHERE clause to delete specific records, otherwise set force to true to clear the table.
    Alternatively, to delete by a complicated filter or to use parameter replacement, pass the filter with or without params as the body.
    By default, only the id property of the record is returned on success, use fields to return more info. Set the body to an array of records, minimally including the identifying fields, to delete specific records.
    By default, only the id property of the record is returned on success, use fields to return more info.
Response Class (Status 200)
    Records



getDbRecords() - Retrieve one or more records.	
/db/_table/{table_name}      
Implementation Notes
    Set the filter parameter to a SQL WHERE clause (optional native filter accepted in some scenarios) to limit records returned    or leave it blank to return all records up to the maximum limit.
    Set the limit parameter with or without a filter to return a specific amount of records.
    Use the offset parameter along with the limit parameter to page through sets of records.
    Set the order parameter to SQL ORDER_BY clause containing field and optional direction ( [ASC|DESC]) to order the returned records.
    Alternatively, to send the filter with or without params as posted data, use the getRecordsByPost() POST request and post a filter with or without params.
    Pass the identifying field values as a comma-separated list in the ids parameter.
    Use the id_field and id_type parameters to override or specify detail for identifying fields where applicable.
    Alternatively, to send the ids as posted data, use the getRecordsByPost() POST request.
    Use the fields parameter to limit properties returned for each record. By default, all fields are returned for all records.
Response Class (Status 200)
    Records
	
updateDbRecords() - Update (patch) one or more records.
/db/_table/{table_name}       
Implementation Notes
    Post data should be an array of records containing at least the identifying fields for each record.
    Posted body should be a single record with name-value pairs to update wrapped in a record tag.
    Ids can be included via URL parameter or included in the posted body.
    Filter can be included via URL parameter or included in the posted body.
    By default, only the id property of the record is returned on success. Use fields parameter to return more info.
Response Class (Status 200)
    Records
	
createDbRecords() - Create one or more records.
/db/_table/{table_name}
Implementation Notes
Posted data should be an array of records wrapped in a record element.
  By default, only the id property of the record is returned on success. Use fields parameter to return more info.
Response Class (Status 200)
  Records

	
replaceDbRecords() - Update (replace) one or more records.
/db/_table/{table_name}
Implementation Notes
    Post data should be an array of records wrapped in a resource tag.
    If ids or filter is used, posted body should be a single record with name-value pairs to update, wrapped in a resource tag.
    Ids can be included via URL parameter or included in the posted body.
    Filter can be included via URL parameter or included in the posted body.
    By default, only the id property of the record is returned on success. Use fields parameter to return more info.
Response Class (Status 200)
  Records

	
deleteDbRecord() - Delete one record by identifier.delete 
/db/_table/{table_name}/{id}
Implementation Notes
    Use the fields parameter to return more deleted properties. By default, the id is returned.
Response Class (Status 200)
    Record

	
 getDbRecord() - Retrieve one record by identifier.
 /db/_table/{table_name}/{id}
 Implementation Notes
    Use the fields parameter to limit properties that are returned. By default, all fields are returned.
Response Class (Status 200)
    Record

updateDbRecord() - Update (patch) one record by identifier.   
patch /db/_table/{table_name}/{id}     
Implementation Notes
    Post data should be an array of fields for a single record.
    Use the fields parameter to return more properties. By default, the id is returned.
Response Class (Status 200)
    Record

	
replaceDbRecord() - Replace the content of one record by identifier.
put /db/_table/{table_name}/{id}
Implementation Notes
  Post data should be an array of fields for a single record.
Use the fields parameter to return more properties. By default, the id is returned.
  Response Class (Status 200)
    Record

