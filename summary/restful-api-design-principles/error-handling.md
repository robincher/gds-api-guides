---
description: Error handling for REST API
---

# Error Handling

Error handling is one  the most important part of any REST API. You must provide sufficient information on why the error occured so as to allow recovery and prevention, while ensuring that the error message are not over-exposing with sensitive information.

Below is an example of showing just enough :

```text
{
 "status": 401,
 "errorCode": 1234,
 "errorMessage": "Authentication Failed",
 "errorDetails": "Error due to invalid token or credentials"
 }
```

Showing too much details :

```text
{
 "status": 401,
 "errorCode": 1234,
 "errorMessage": "Authentication Failed",
 "errorDetails": "TypeError: Bad input string
    at Decipher.Cipher.update (crypto.js:279:27)
    at module.exports.decrypt (/xxxx/yyyyy/jjj/ssss/encryptionService.js:19:28)
    at Object.module.exports.passwordDecryptor (/xxxx/yyyyy/jjj/ssss/encryptionService.js:59:56)
    at Object.<anonymous> (/xxxx/yyyyy/jjj/ssss/test.js:32:33)
    at Module._compile (module.js:456:26)
    at Object.Module._extensions..js (module.js:474:10)
    at Module.load (module.js:356:32)
    at Function.Module._load (module.js:312:12)
    at Function.Module.runMain (module.js:497:10)
    at startup (node.js:119:16)"
 }
```

