# Pagination

To handle the potential grow of your APIs,  we recommend you to design your API in a manner that supports pagination. 

Let’s say your call is to get the users for a particular system, and the result could be a massive response with hundreds of thousands of pages. Pagination will address this by limiting the number of results per page and allowing you to traverse to a particular page.

Typically, there are two ways of implementing Pagination.

### Offset-Based Pagination Example

 `GET /users?offset=3&limit=25`

The API retrieve users from the 3rd page \(offset\) with maximum of 25 records.

`GET /users?offset=2&records=50`

The API retrieve users from the 2nd page \(offset\) with maximum of 50 records

This pattern is most suitable for non-chronological data.  For consideration,  if  the results list from a offset-based pagination has changed between calls to the API, the indices would shift and cause an item to be either returned twice or skipped and never returned.

### Cursor-Based Pagination Example

Cursor-based **should always be used where possible**. A cursor refers to a random string of characters which marks a specific list of items. You can think of this string like  a bookmark on a book's page where you left off . This string  is usually called **`next`** or **`next_cursor`**

`GET /followers/ids.json?screen_name=user01`

```text
{
    "ids": [
        385752029,
        602890434,
        ...
        333181469,
        333165023
    ],
    "next_cursor": 1374004777531007833,
    "next_cursor_str": "1374004777531007833",
    "previous_cursor": 0,
    "previous_cursor_str": "0"
}
```

`GET /followers/ids.json?screen_name=user01&cursor=1374004777531007833`

```text
{
    "ids": [
        333156387,
        333155835,
        ...
        101141469,
        92896225
    ],
    "next_cursor": 1323935095007282836,
    "next_cursor_str": "1323935095007282836",
    "previous_cursor": -1374003371900410561,
    "previous_cursor_str": "-1374003371900410561"
}
```

Notice that we now have a **`next_cursor`** as well as a **`previous_cursor`**. This means that you can now traverse back and forth the records.  Make a call on the URL \(shown below\) will allow you to view the first set of records.

`GET /followers/ids.json?screen_name=user01&cursor=1374003371900410561`

The cursor will always point to the same part of the list, but will be invalidated if an item is removed. Therefore, cursors should not be stored and assumed to be usable in the future.

By returning a “cursor”, the API guarantees that it will return the exactly the next entry in the list, regardless of what changes happen to the collection between API calls. 

