# HTTP Verb \(Standard Methods\)

HTTP verbs, or methods, should be used in compliance with their definitions under the [HTTP/1.1](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) standard. The action taken on the representation will be contextual to the media type being worked on and its current state.

| Method Description | GET | POST | PUT | PATCH | DELETE |
| :--- | :--- | :--- | :--- | :--- | :--- |
| CRUD Operation | Read | Create | Update | Update | Delete |
| /api/v1/promotions | List all promotions | Create a new promotion | Bulk update all promotions\* | Bulk update all promotions specific fields | Delete all Promotions |
| /api/v1/promotions/{id} | Get a single promotion | Error | Update a single promotion based on an identifier if exists, else show error | Update specific fields of a single promotion based on an identifier if exists, else show error | Delete a single Promotion based on an identifier |



**PUT vs PATCH**

As both HTTP **PUT** and **PATCH** are designated operation to update a resource, it is important to understand the differences between both of them before picking one over another.

Look at this statement below:

_When a client needs to replace an existing Resource entirely, they can use **PUT**. When they’re doing a partial update, they can use HTTP **PATCH**._

For example, when updating a single field of a resource, sending the whole resource representation might consume unnecessary bandwidth and introduce additional complexity in the code. In such scenario, the nature of PATCH will make more sense.

Examples below show how you can update a single resource's entity with both PATCH and PUT.

```javascript
PATCH /users/1
{
    "email": "skwee357@gmail.com"// new email address
}
```

{% code-tabs %}
{% code-tabs-item title="Update by PUT" %}
```javascript
PUT /users/1
{    
   "username": "kltan1999",    
   "email": "kltan@gmail.com" // new email address    
   "mobile" : "12345677",    
   "gender" : "female",    
   "race" : "other",    
   "job" : "Software Engineer",    
   "accountStatus" : "active",   
 }
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Another important aspect to consider here is **idempotence; PUT is idempotent; PATCH can be both**. Depending on the semantics of the operation being implemented, we can also choose one or the other based on this characteristic.

Below two examples illustrate both a idempotent and non-idempotent PATCH

**Idempotent PATCH**

```javascript
GET /users/1
{
    "username": "user1",
    "email": "user1@gmail.com"
}
PATCH /users/1
{
    "email": "user123@gmail.com"       // New email address
}

GET /users/1
{
    "username": "user1",
    "email": "user123@gmail.com"       // Email address was changed
}
PATCH /users/1
{
    "email": "user123@gmail.com"       // Same request with new Email
}

GET /users/1
{
    "username": "user1",
    "email": "user123@gmail.com"       // Nothing changed since last GET
}
```

**Non-idempotent PATCH**

Supposed we can call a list of users 

```javascript
GET /users/1[{ "id": 1, "username": "firstuser", "email": "firstuser@example.org" }]
```

We are allow to PATCH /users directly to add a new record 

```javascript
PATCH /users

[{ "operation": "add", "username": "newuser", "email": "newuser@example.org" }]

```

Now we can see the new user when calling GET /users

```javascript
GET /users

[{ "id": 1, "username": "firstuser", "email": "firstuser@example.org" },
 { "id": 2, "username": "newuser", "email": "newuser@example.org" }]
```

Calling the same **PATCH request again** as above ,a new duplicated record will be added. 

```javascript
PUT /users

[{ "op": "add", "username": "newuser", "email": "newuser@example.org" }]

GET /users

[{ "id": 1, "username": "firstuser", "email": "firstuser@example.org" },
 { "id": 2, "username": "newuser", "email": "newuser@example.org" },
 { "id": 3, "username": "newuser", "email": "newuser@example.org" }]
```

In summary , we can use both PUT and PATCH for to update a single field of a resource's entity, but special consideration have to be taken when using PATCH on a top level resource , i.e /users.

