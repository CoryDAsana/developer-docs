<hr class="full-line">
<section>

# SCIM


Asana supports SCIM 2.0 operations at `https://app.asana.com/api/1.0/scim`. Okta provides [documentation](https://developer.okta.com/docs/concepts/scim/) for understanding SCIM.

Only [Service Accounts](https://asana.com/guide/help/premium/service-accounts) in [Enterprise Domains](https://asana.com/enterprise) can access SCIM endpoints.

<hr>

## Service provider configuration endpoints

|HTTP method|API endpoint|Asana behavior|
|---------|--------|--------------|
|GET|/ServiceProviderConfig|Read-only meta information.|
|GET|/ResourceTypes|Read-only meta information.|
|GET|/Schemas|Read-only meta information.|

<hr>

## User endpoints

> Examples

```json
Request: GET https://app.asana.com/api/1.0/scim/Users?filter=userName eq "johnsmith@example.com"

Response: 200 OK

{
    "Resources": [
        {
            "id": "1",
            "name": {
                "familyName": "John",
                "givenName": "Smith",
                "formatted": "John Smith"
            },
            "userName": "johnsmith@example.com",
            "emails": [
                {
                    "value": "johnsmith@example.com",
                    "primary": true,
                    "type": "work"
                }
            ],
            "active": true,
            "schemas": [
                "urn:ietf:params:scim:schemas:core:2.0:User",
                "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
            ],
            "title": "Software Engineer",
            "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
                "department": "R&D"
            }
        }
    ],
    "totalResults": 1,
    "schemas": [
        "urn:ietf:params:scim:api:messages:2.0:ListResponse"
    ]
}
```

```json
Request: POST https://app.asana.com/api/1.0/scim/Users

{
    "schemas": [
        "urn:ietf:params:scim:schemas:core:2.0:User",
        "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
    ],
    "userName": "johnsmith@example.com",
    "name": {
        "formatted": "John Smith"
    },
    "emails": [
        {
            "primary": true,
            "value": "johnsmith@example.com"
        }
    ],
    "active": true,
    "title": "Software Engineer",
    "preferredLanguage": "en",
    "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
        "department": "R&D"
    }
}

Response: 201 Created

{
    "id": "1",
    "name": {
        "familyName": "John",
        "givenName": "Smith",
        "formatted": "John Smith"
    },
    "userName": "johnsmith@example.com",
    "emails": [
        {
            "value": "johnsmith@example.com",
            "primary": true,
            "type": "work"
        }
    ],
    "active": true,
    "schemas": [
        "urn:ietf:params:scim:schemas:core:2.0:User",
        "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
    ],
    "title": "Software Engineer",
    "preferredLanguage": "en",
    "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
        "department": "R&D"
    }
}
```

```json
Request: PATCH https://app.asana.com/api/1.0/scim/Users/1

{
    "schemas": [
        "urn:ietf:params:scim:api:messages:2.0:PatchOp"
    ],
    "Operations": [
        {
            "op": "replace",
            "value": {
                "title": "Senior Software Engineer"
            }
        }
    ]
}

Response: 200 OK

{
    "id": "1",
    "name": {
        "familyName": "John",
        "givenName": "Smith",
        "formatted": "John Smith"
    },
    "userName": "johnsmith@example.com",
    "emails": [
        {
            "primary": true,
            "value": "johnsmith@example.com",
            "type": "work"
        }
    ],
    "active": true,
    "preferredLanguage": "en",
    "title": "Senior Software Engineer",
    "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
        "department": "R&D"
    },
    "schemas": [
        "urn:ietf:params:scim:schemas:core:2.0:User",
        "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
    ]
}

```

|HTTP method|API endpoint|Asana behavior|
|---|--------|--------------|
|GET|/Users|Return full list of users in the domain.  Does not return Asana guest users. <br>The accepted query parameters are:<br> 1. filter for `userName`.|
|GET|/Users/:id|Return specific user in the domain.  Does not return Asana guest users.|
|POST|/Users|Create a new user if the User does not exist.|
|PUT|/Users/:id|Update / remove attributes for a User. Deprovision user (zombify) in Asana if `active=false`.|
|PATCH|/Users/:id|Add / update attributes for a user. Deprovision user (zombify) in Asana if `active=false`.|
|DELETE|/Users/:id|Deprovision user (zombify) in Asana.|


Accepted attributes:

|Attribute|Type|Info|
|---------|----|----|
|userName|string|Unique identifier for the user, typically used by the user to directly authenticate to the service provider. Each user MUST include a non-empty `userName` value, and it must be an email address. _Required_.|
|name|complex|The user's name.|
|name.givenName|string|Unsupported for `PATCH` request, use `name.formatted`.|
|name.familyName|string|Unsupported for `PATCH` request, use `name.formatted`.|
|name.formatted|string|The full name of the user.|
|emails|multi-valued complex|Email addresses for the user.|
|emails.value|string|Email address for the user.|
|email.primary|string|Whether this email address is the preferred email address for this user. `true` may only appear once for this attribute.|
|active|boolean|Indicates whether the user's account is active in Asana.|
|title|string|The user's title, such as "Vice President".|
|preferredLanguage|string|The user's preferred language. Used for selecting the localized User interface.|
|"urn:ietf:params:scim:<br>schemas:extension:enterprise:<br>2.0:User"|complex|The Enterprise User Schema Extension attribute.|
|"urn:ietf:params:scim:<br>schemas:extension:enterprise:<br>2.0:User.department"|string|The department the user belongs to.|

<hr>

## Group endpoints

> Examples

```json
Request: GET https://app.asanac.om/api/1.0/scim/Groups?filter=displayName eq "Marketing"

Response: 200 OK

{
    "Resources": [
        {
            "id": "1",
            "displayName": "Marketing",
            "schemas": [
                "urn:ietf:params:scim:schemas:core:2.0:Group"
            ],
            "meta": {
                "resourceType": "Group"
            }
        }
    ],
    "totalResults": 1,
    "schemas": [
        "urn:ietf:params:scim:api:messages:2.0:ListResponse"
    ]
}
```

```json
Request: POST https://app.asana.com/api/1.0/scim/Groups

{
    "schemas": [
        "urn:ietf:params:scim:schemas:core:2.0:Group"
    ],
    "displayName": "Marketing",
    "members": [
        {"value": "1"},
        {"value": "2"}
    ]
}

Response: 201 Created

{
    "id": 1,
    "displayName": "Marketing",
    "members": [
        {"value": "1"},
        {"value": "2"}
    ],
    "schemas": [
        "urn:ietf:params:scim:schemas:core:2.0:Group"
    ],
    "meta": {
        "resourceType": "Group"
    }
}
```

```json
Request: PATCH https://app.asana.com/api/1.0/scim/Groups/1

{
    "schemas": [
        "urn:ietf:params:scim:api:messages:2.0:PatchOp"
    ],
    "Operations": [
        {
            "op": "add",
            "path": "members",
            "value": [
                {
                    "value": "3"
                }
            ]
        }
    ]
}

Response: 204 No Content
```

SCIM Groups are equivalent to Asana [teams](/docs/teams).

|HTTP method|API endpoint|Asana behavior|
|---------|------|--------------|
|GET|/Groups|Return full list of team in the domain, including private team. <br>The accepted query parameters are:<br> 1. filter for `displayName`.|
|GET|/Groups/:id|Return a specific team in the domain. |
|POST|/Groups|Create a new team.|
|PUT|/Groups/:id|Replace the team's attributes.|
|PATCH|/Groups/:id|Update the team's attributes.|


Accepted attributes:

|Attribute|Type|Info|
|---------|----|----|
|displayName|string|Unique identifier for the team. _Required_.|
|members|multi-valued complex|The members of the team.|
|members.value|string|The team member's user ID.|

</section>
