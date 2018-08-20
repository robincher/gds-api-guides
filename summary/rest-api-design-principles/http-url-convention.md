# HTTP URL Convention

When forming a REST endpoint URL, think of the following :

1.  ****URL represent a resource, and it should be named as a nouns , not a verb.
2. Provide version number in the API URL.
3. Give plural nouns to identify the resource only for consistency 

Below are a few examples of good and bad url convention of the API resource URL. Specifically, a good API resource end point should be identified by a **nouns** in **plural** form and  consist of a **version number**

**Good Examples**

| GET : api/v1/promotions |
| :--- |
| GET : api/v1/promotions/{promotionId} |
| GET : api/v1/promotions/?querystring=value |
| POST : api/v1/promotions |
| PUT : api/v1/promotions/{promotionId} |
| DELETE : api/v1/promotions |

**Bad Examples**

| **Non-Plural Noun:** api/v1/promotion |
| :--- |
| **Using Verb** : api/v1/getMyPromotion |
| **No Versioning:** api/promotions |

  
When things get a little fuzzy and you need to design APIS that do not typically fit into any CRUD operations , there are a number of approaches you can take.

**Option 1 : Restructure the action to appear like a field of a resource.** 

This works if the action doesn't take parameters. For example an activate action could be mapped to a **boolean activated field** and updated via a PATCH to the resource

```text
PATCH /users/123
{
    "activate": true     // activate user 123 account
}
```

**Option 2 : Treat it like a sub-resource with RESTful principles.**

For example, GitHub's API lets you **star** a gist with **PUT /gists/:id/star** and **unstar** with **DELETE /gists/:id/sta**

**Good Examples**

| api/v1/promotions/{promotionId}/expire |
| :--- |
|  api/v1/users/{userId}/unlock |
| api/v1/users/{userId}/lock |

**Option 3 : You should not need to go deeper than resource/identifier/resource.**  

Sometimes you really have no way to map the action to a sensible RESTful structure. For example, a multi-resource search doesn't really make sense to be applied to a specific resource's endpoint. In this case, **/search** would be more appropriate. Consider developing a generic search or filter that can retrieve results based on filtering parameters. For more information, you may refer to [Ghost API Filter mechanism ](https://api.ghost.org/docs/filter)

**Good Examples**

| api/v1/promotions/search |
| :--- |
| api/v1/promotions/query |
| api/v1/promotions/fields |

  
**Bad Example**

| api/v1/promotions/{promotionID}/users/{promotion.user.id} |
| :--- |




