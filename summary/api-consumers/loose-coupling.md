# Loose Coupling

API consumers \(clients\) **MUST** **operate independently** from the REST API implementations. The consumers \(clients\) **must not function by assuming or relying** on the knowledge of the API implementation.

By detaching your clients from the API internals, your client will be more extensible whenever there are modification to the semantics of the API response.

