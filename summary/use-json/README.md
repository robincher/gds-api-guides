# Use JSON

When designing new web-based digital services, the **recommended message type is JSON \(Javascript Object Notation\),** which follow ****the **** [RFC-7159](https://tools.ietf.org/html/rfc7159) standard. JSON is simple, extensible and human readable. Additionally, data represented in JSON format can be easily parsed by any modern web browser, where most of the application are built upon. 

Only consider other message content type when there are requirements to 

* interface with legacy systems that only support a particular format , i.e XML or Cobol.
* design services that strongly tied to a schema, where protocol buffers and XML are better options

We recommend that you should:

* use consistent grammar case for object keys - choose **camelCase** if possible. Look at [Restful API Design Principles](../rest-api-design-principles/) section for more information.

```text
{
    "userName" : "User 1",
    "userAge" : "10",
    "accountStatus" : "Active",
    "isAdmin" : false
}
```

* create response as a JSON object rather than an array, as an array will limit a JSON objective capability to extend in the future. For example, adding metadata.

