---
description: 'API response filtering , sort and search'
---

# Filter , Sort and Search

As your API start to grows ,  you may want to implement filters at the **URL level** to restricts the data returned. Filter can be append as a query parameter named for the field to be filtered on, the value should  be the value you need to filter for.

### Filtering

`GET /tickets?state=open&priority=high`

Retrieving only tickets that are open and high priority

### Sorting

`GET /tickets?sort=createdDateTime`

Retrieving tickets and sort them according to created date

### Searching

`GET /tickets?q={"type" : "error"}`

Retrieve tickets that are of error type



