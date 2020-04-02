--- 

title: Blinket API 

language_tabs: 
   - shell 

toc_footers: 
   - <a href='#'>Sign Up for a Developer Key</a> 
   - <a href='https://github.com/lavkumarv'>Documentation Powered by lav</a> 

includes: 
   - errors 

search: true 

--- 

# Introduction 

This is the Blinket public API 

**Version:** 1.0.0 

# Authentication 

|oauth2|*OAuth 2.0*|
|---|---| 

# /EVENT
## ***GET*** 

**Summary:** List your events data you have organized

**Description:** List your events data you have organized

### HTTP Request 
`***GET*** /event` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| page | query | Number of pagination page. | No | integer |
| title | query | Title of event you must search | No | string |
| type | query | Type of event you must search | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | successful operation |
| 404 | Data not found |

# /EVENT/{ID}
## ***GET*** 

**Summary:** Get event data by event id

**Description:** Get your event data by event id

### HTTP Request 
`***GET*** /event/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | ID of event. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | successful operation |
| 404 | Data not found |

# /EVENT/{ID}/PARTICIPANT
## ***GET*** 

**Summary:** List the participants of your event by event id

**Description:** List the participants of your event by event id

### HTTP Request 
`***GET*** /event/{id}/participant` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | ID of event | Yes | string |
| page | query | Number of pagination page. | No | integer |
| ticket_id | query | Id of a ticket of this event | No | string |
| status | query | Status of participant you must search | No | string |
| invite_key | query | Invite key of an participant | No | string |
| name | query | Name of an participant | No | string |
| email | query | Email of an participant | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | successful operation |
| 404 | Data not found |

# /EVENT/{EVENTID}/PARTICIPANT/{PARTICIPANTID}
## ***GET*** 

**Summary:** Get participant data of an event you have produced

**Description:** Get your participant data of an event you have produced

### HTTP Request 
`***GET*** /event/{eventId}/participant/{participantId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| eventId | path | ID of event. | Yes | string |
| participantId | path | ID of participant. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | successful operation |
| 404 | Data not found |

# /MY-TICKETS/EVENT
## ***GET*** 

**Summary:** List of events you have participated

**Description:** List of events you have participated

### HTTP Request 
`***GET*** /my-tickets/event` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| page | query | Number of pagination page. | No | integer |
| title | query | Title of event you must search | No | string |
| type | query | Type of event you must search | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | successful operation |
| 404 | Data not found |

# /MY-TICKETS/EVENT/{EVENTID}
## ***GET*** 

**Summary:** List of invites of an event you have participated

**Description:** List of invites of an event you have participated

### HTTP Request 
`***GET*** /my-tickets/event/{eventId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| eventId | path | Id of an event you have participated | Yes | string |
| page | query | Number of pagination page. | No | integer |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | successful operation |
| 404 | Data not found |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
