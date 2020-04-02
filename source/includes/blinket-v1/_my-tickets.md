# Blinket: My-Tickets #

The Blinket My-Tickets API allows you to view tickets data of events you have participated.

## My-Tickets event properties ##

| Attribute | Type | Description
| --------- | ---- | ----------------------------------------------|
`id` | string | Event id
`type` | string | Event type in (online, presential)
`title` | string | Event title
`description` | string | Event description
`sale_url` | string | Event sale url
`stream_url` | string | Event stream url
`start_date` | string - date-time | Event start date in UTC format
`end_date` | string - date-time | Event start date in UTC format
`place` | string | Address place of event
`country` | string | Address country of event
`state` | string | Address state of event
`city` | string | Address city of event
`district` | string | Address district of event
`street` | string | Address street of event
`complement` | string | Address complement of event
`number` | string | Address number of event
`zip` | string | Address zipcode of event
`reference` | string | Address reference of event

## List events i've participated

**Summary:** List of events you have participated

**Description:** List of events you have participated

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/blinket/v1/my-tickets/event</h6>
	</div>
</div>

```shell
curl GET https://example.com/blinket/v1/my-tickets/event?page=1&title=test&type=online \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
    "pages": 1,
    "items_per_page": 25,
    "page": 1,
    "total_items": 2,
    "items": [
        {
            "id": "9039jah2-7c1d-4f7a-83e9-e3b9e2f3992j",
            "type": "online",
            "title": "Example 1",
            "description": "Example 1 description",
            "sale_url": "https://evento.blinket.com.br/example-1",
            "stream_url": "http://example.ex",
            "start_date": "2020-05-04T21:29:00Z",
            "end_date": "2020-06-19T21:29:00Z",
            "place": null,
            "country": null,
            "state": null,
            "city": null,
            "district": null,
            "street": null,
            "complement": null,
            "number": null,
            "zip": null,
            "reference": null
        },
        {
            "id": "9039bd46-7c1d-4f7a-83e9-e3b9e2f390e1",
            "type": "online",
            "title": "Example 2",
            "description": "Example 2 description",
            "sale_url": "https://evento.blinket.com.br/example-1",
            "stream_url": "http://example.ex",
            "start_date": "2020-05-04T21:29:00Z",
            "end_date": "2020-06-19T21:29:00Z",
            "place": null,
            "country": null,
            "state": null,
            "city": null,
            "district": null,
            "street": null,
            "complement": null,
            "number": null,
            "zip": null,
            "reference": null
        }
    ]
}
```

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

## My-Tickets invite properties ##

| Attribute | Type | Description
| --------- | ---- | ----------------------------------------------|
`id` | string | Invite ID
`name` | string | Participant name
`email` | string | Participant email
`invoice_id` | integer | Eduzz invoice ID
`invite_key` | string | Participant invite key ID
`content_id` | integer | Eduzz content ID
`status` | string | Participant invite status IN (paid, refunded, locked, presence_confirmed, confirmed)
`invite_url` | string | URL of invite confirmation
`ticket_name` | string | Invite ticket name
`ticket_is_paid` | boolean | If invite ticket is paid or not
`ticket_show_on_page` | boolean | If invite ticket is showed up in event sale page

## List invites of event i've participated

**Summary:** List of invites of an event you have participated

**Description:** List of invites of an event you have participated

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/blinket/v1/my-tickets/event/{eventId}</h6>
	</div>
</div>
```shell
curl GET https://example.com/blinket/v1/my-tickets/event/9039jah2-7c1d-4f7a-83e9-e3b9e2f3992j?page=1 \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
    "pages": 1,
    "items_per_page": 25,
    "page": 1,
    "total_items": 1,
    "items": [
        {
            "id": "9039jah2-7c1d-4f7a-83e9-e3b9e2f3992j",
            "name": "Participant example",
            "email": "participant@email.com",
            "invoice_id": 000001,
            "invite_key": "000001-1",
            "content_id": 000001,
            "status": "presence_confirmed",
            "invite_url": "https://example.com",
            "ticket_name": "Ticket Example",
            "ticket_is_paid": false,
            "ticket_show_on_page": true
        }
    ]
}
```

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
