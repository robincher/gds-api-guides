# Versioning

Due to changing business nature and requirements,  it is imperative to provide versioning mechanism on your published API. While updating your API seems to be a simple process,  you must consider how the changes will affect your existing API consumers. The changes to an API **MUST NOT** break existing clients

For simplicity, we **recommend**  API versioning to be done on the URL-level.

  `http://api.example.com/v1/customers/S1213456` 

Not all changes to your API required a new version number. General rule of thumb for versioning are below :

### Types of Changes

**Changes that don’t require a new version**

* New resources
* New HTTP methods on existing resources
* New data format
* New attribute or elements on existing data type

**Changes that require a new version**

* Renaming fields and/or resource paths
* Changing payload structures \(i.e renaming or removing attributes\)
* Changing  HTTP verbs and response codes

