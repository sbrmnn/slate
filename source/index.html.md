---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ


toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

search: true

code_clipboard: false

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

API documentation for Asteroid.

#  Authentication
## Login

> 200 OK

```json
{
    "token": "eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoyNSwiZXhwaXJlc19hdCI6IjIwMjItMTEtMjQgMTg6NDc6NDIgVVRDIn0.K1Y3HB0ljH-DmIVUBX7ggc3J4WUe6z3b4kHmYexHImY",
    "signInPath": "/pet/ally_test/sign_in",
    "id": 25,
    "name": "Jeremy Mickelson",
    "email": "jeremy@test.com",
    "googleApiKey": null,
    "clientId": "1",
    "primaryRole": "pet",
    "roles": [
        "client"
    ],
    "practiceId": 1,
    "practiceName": "AllyDVM Test Practice",
    "practicePms": "Vetter",
    "practiceSms": null,
    "practiceFeatures": [
        "comm_engine",
        "retention_calendar",
        "online_patient_portal",
        "pet_page_app",
        "loyalty_program",
        "html_editor",
        "caller_id",
        "analytics",
        "two_way_texting",
        "net_promoter_score",
        "writebacks",
        "experimental",
        "telemedicine"
    ],
    "sourceId": 1,
    "timeZone": "America/New_York",
    "enterpriseIds": [
        1123,
        5813,
        5827,
        2134,
        1,
        61
    ],
    "timezone": "America/New_York"
}
```

> 401 Unauthorized

```json
{
    "error": "Invalid email or password."
}
```


Authenticate a user with their email and password and recieve a authentication token
that can be used with other endpoints that retrieve user related data. 

### Headers
`Accept: application/json`

`Content-Type: application/json`

### HTTP Request

`POST https://connect.allydvm.com/users/sign_in`

### Request Parameters

Parameter | Required | Description
--------- | ------- | -----------
user[email] | true | Email address of user.
user[password] | true | Password of user.


## Change Password

> 200 OK

```json
{
    "signInPath": "/pet/ally_test/sign_in",
    "id": 25,
    "name": "Jeremy Mickelson",
    "email": "jeremy@test.com",
    "googleApiKey": null,
    "clientId": "1",
    "primaryRole": "pet",
    "roles": [
        "client"
    ],
    "practiceId": 1,
    "practiceName": "AllyDVM Test Practice",
    "practicePms": "Vetter",
    "practiceSms": null,
    "practiceFeatures": [
        "comm_engine",
        "retention_calendar",
        "online_patient_portal",
        "pet_page_app",
        "loyalty_program",
        "html_editor",
        "caller_id",
        "analytics",
        "two_way_texting",
        "net_promoter_score",
        "writebacks",
        "experimental",
        "telemedicine"
    ],
    "sourceId": 1,
    "timeZone": "America/New_York",
    "enterpriseIds": [
        1123,
        5813,
        5827,
        2134,
        1,
        61
    ]
}
```

> 422 Unprocessable Entity

```json
{
    "errors": {
        "password_confirmation": [
            "can't be blank"
        ],
        "password": [
            "should be different than your current password"
        ],
        "current_password": [
            "can't be blank",
            "is invalid"
        ]
    }
}
```

Change a user's password with their current password, new password, and new passsword confirmation. 

### Headers
`Accept: application/json`

`Content-Type: application/json`

`Authorization: Bearer < TOKEN FROM SIGN IN >` [Get token from here](#login)


### HTTP Request

`PUT https://connect.allydvm.com/users/`

### Request Parameters

Parameter | Required | Description
--------- | ------- | -----------
user[current_password] | true | Current password of user.
user[password] | true | New password for user.
user[password_confirmation] | true | New password confirmation for user.

# User 
## User Info

> 200 Ok

```json
{
    "signInPath": "/pet/ally_test/sign_in",
    "id": 25,
    "name": "Jeremy Mickelson",
    "email": "jeremy@test.com",
    "googleApiKey": null,
    "clientId": "1",
    "primaryRole": "pet",
    "roles": [
        "client"
    ],
    "practiceId": 1,
    "practiceName": "AllyDVM Test Practice",
    "practicePms": "Vetter",
    "practiceSms": null,
    "practiceFeatures": [
        "comm_engine",
        "retention_calendar",
        "online_patient_portal",
        "pet_page_app",
        "loyalty_program",
        "html_editor",
        "caller_id",
        "analytics",
        "two_way_texting",
        "net_promoter_score",
        "writebacks",
        "experimental",
        "telemedicine"
    ],
    "sourceId": 1,
    "timeZone": "America/New_York",
    "enterpriseIds": [
        1123,
        5813,
        5827,
        2134,
        1,
        61
    ]
}
```

Get information about a user. 

### Headers
`Accept: application/json`

`Content-Type: application/json`

`Authorization: Bearer < TOKEN FROM SIGN IN >` [Get token from here](#login)


### HTTP Request

`GET https://connect.allydvm.com/users/current`

### Request Parameters

None


# Terms 

## Accept Terms for API use
> 200 Ok

```json
{
    "success": "success"
}
```

Accept terms and conditions so the user can access a greater number of API endpoints.

### Headers
`Accept: application/json`

`Content-Type: application/json`

`Authorization: Bearer < TOKEN FROM SIGN IN >` [Get token from here](#login)

### HTTP Request

`POST https://connect.allydvm.com/terms`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
terms[accept] | true | Accept terms for user.



# Client

## Get All Clients 

> 200 OK

```json
{
    "sourceId": 1,
    "clientId": "1",
    "practiceId": 1,
    "fingerprint": 1,
    "clientClassId": "cool_clients",
    "firstSyncedAt": "2022-12-01T15:50:30.000Z",
    "lastSyncedAt": "2022-12-01T15:50:30.000Z",
    "createdAt": "2022-12-01T15:50:30.000Z",
    "updatedAt": "2022-12-01T15:50:30.000Z",
    "displayId": "1",
    "firstName": "Jeremy",
    "lastName": "Mickelson",
    "address": "Address",
    "city": "City",
    "state": "CA",
    "postalCode": "12345",
    "email": "jeremy@test.com",
    "homePhone": "9096480002",
    "workPhone": "9096480003",
    "mobilePhone": "8012223333",
    "status": "active",
    "balanceDue": 23871,
    "communicationsDisabled": "enabled",
    "emailVerificationStatus": "verified",
    "emailVerificationResponse": {},
    "emailVerifiedAt": null,
    "emailPrior": null,
    "alertsDisabled": false,
    "emailAlertDisabled": false,
    "smsAlertDisabled": false,
    "badPhysicalAddress": false,
    "fullAddressPrior": "",
    "loyaltyInvoiceProcessingEndedAt": null,
    "loyaltyInvoiceProcessingRemainder": null,
    "loyaltyToggle": false,
    "clientClass": {
        "clientClassId": "cool_clients",
        "sourceId": 1,
        "description": "Cool Clients",
        "communicationsDisabled": "enabled"
    },
    "patients": [
        {
            "sourceId": 1,
            "patientId": "pi",
            "practiceId": 1,
            "name": "Pi",
            "displayId": null,
            "deceasedDate": null,
            "status": "active"
        },
        {
            "sourceId": 1,
            "patientId": "xzy-abc-12345-00001",
            "practiceId": 1,
            "name": "Brownie",
            "displayId": null,
            "deceasedDate": "2022-12-01",
            "status": "active"
        },
        {
            "sourceId": 1,
            "patientId": "12000",
            "practiceId": 1,
            "name": "Oreo",
            "displayId": null,
            "deceasedDate": null,
            "status": "active"
        },
        {
            "sourceId": 1,
            "patientId": "12001",
            "practiceId": 1,
            "name": "Dusty",
            "displayId": null,
            "deceasedDate": null,
            "status": "active"
        },
        {
            "sourceId": 1,
            "patientId": "12002",
            "practiceId": 1,
            "name": "Goldilocks",
            "displayId": null,
            "deceasedDate": null,
            "status": "inactive"
        },
        {
            "sourceId": 1,
            "patientId": "12003",
            "practiceId": 1,
            "name": "Tweets",
            "displayId": null,
            "deceasedDate": null,
            "status": "active"
        },
        {
            "sourceId": 1,
            "patientId": "12004",
            "practiceId": 1,
            "name": "Name",
            "displayId": null,
            "deceasedDate": null,
            "status": "active"
        }
    ],
    "primaryPractice": "AllyDVM Test Practice",
    "petRecordsStatus": "Active"
}
```
This endpoint retrieves all clients.

**Must accept [terms](#terms) before using this endpoint.**

### Headers
`Accept: application/json`

`Content-Type: application/json`

`Authorization: Bearer < TOKEN FROM SIGN IN >` [Get token from here](#login)


### HTTP Request

`GET https://connect.allydvm.com/clients`
