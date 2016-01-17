# SF-Test-Data-Generator
TestDataGenerator is a class which allows you to dynamically create and delete custom and standard objects in salesforce for testing purposes.

To run generation use method g() which generates amount of records you need and returns the list of sObjects or gi() which generates and inserts sObjets.
Both g() and gi() methods has following parameters:

- **Integer amount** - specifies amount of objects to create. It takes aprox. 15-20 seconds to create 500 custom objects with 8 required fields and one reference.
- **sObject obj** - it's an object, which instances will be created. Also you can specify any field to fill manually: for example new Account(Name='MyAccount').
- **Set<String> notRequiredFieldsToFill** - optional field, in which you can specify any field which is not required and will be autofilled.

Also there's a convenient d() - delete - method, which has simillar to g()/gi() syntax:
- **sObject obj** - specifies and object, instance of which will be deleted. You can specify the field on which a query will search objects to delete, otherwise **all objects will be deleted**. For example: d(new Account(Name='My%')) - deletes all Accounts, which names start with My (it uses LIKE SOQL operator; for number fields = is used); d(new Account()) - deletes all Accounts.
- **String query** - optional field, in which you can specify exact WHERE statement.

Finally, a static createPortalUser() method does exactly what it suppose to do.
