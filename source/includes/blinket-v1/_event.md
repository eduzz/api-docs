# Blinket: Event #

The Blinket Event API allows you to view event data.

## Event properties ##

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
`tickets` | array | Tickets data. See [Event - Ticket properties](#event-ticket-properties)

### Event - Ticket properties ###

| Attribute | Type | Description
| --------- | ---- | ----------------------------------------------|
`id` | string | Ticket id
`name` | string | Ticket name
`is_paid` | boolean | If ticket is paid or not
`show_on_sale_page` | boolean | If ticket is showed up in event sale page
`lots` | array | Lot data. See [Event - Ticket lot properties](#event-ticket-lot-properties)

### Event - Ticket lot properties ###

| Attribute | Type | Description
| --------- | ---- | ----------------------------------------------|
`id` | string | Lot id
`content_id` | integer | Eduzz content id
`start_sale_date` | string - date-time | Lot start sale date in UTC format
`end_sale_date` | string - date-time | Lot end sale date in UTC format
`total_stock` | integer | Total stock of this lot
`value` | number - float | "Unit price of this lot"

## List events

**Description:** List your events data you have organized

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/blinket/v1/event</h6>
	</div>
</div>

```shell
curl GET https://example.com/blinket/v1/event?page=1&title=test&type=online \
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

## Retrieve an event

**Description:** Get your event data by event id

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/blinket/v1/event/{id}</h6>
	</div>
</div>

```shell
curl GET https://example.com/blinket/v1/event/903uaj99-dbe6-442e-b4f6-47e34cf0m957 \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
    "id": "903uaj99-dbe6-442e-b4f6-47e34cf0m957",
    "type": "presential",
    "title": "Example",
    "description": "This is a example description",
    "sale_url": "https://evento.blinket.com.br/example",
    "stream_url": null,
    "start_date": "2020-05-04T21:33:00Z",
    "end_date": "2020-06-18T21:30:00Z",
    "place": "An event place",
    "country": "Brazil",
    "state": "SP",
    "city": "Sorocaba",
    "district": "Jardim Magnolia",
    "street": "Av Sorocaba",
    "complement": "Empresa",
    "number": "500",
    "zip": "18044-390",
    "reference": "Eduzz",
    "tickets": [
        {
            "id": "90jah2e99-dd4c-4fed-8ee4-cde55fejajanc",
            "name": "Ticket Example",
            "is_paid": false,
            "show_on_sale_page": true,
            "lots": [
                {
                    "id": "9039be9a-df55-4f96-af8d-73a927987651",
                    "content_id": 000001,
                    "start_sale_date": "2020-05-04T03:00:00Z",
                    "end_sale_date": "2020-06-18T21:30:00Z",
                    "total_stock": 150,
                    "value": 0
                }
            ]
        }
    ]
}
```

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | ID of event. | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | successful operation |
| 404 | Data not found |

## Participant properties ##

| Attribute | Type | Description
| --------- | ---- | ----------------------------------------------|
`id` | string | Participant ID"
`status` | string | Participant status IN (paid, refunded, locked, presence_confirmed, confirmed)
`name` | string | Participant name
`email` | string | Participant email
`invite_key` | string | Participant invite key ID
`tags` | array | Participant marker tags
`tickets` | array | Tickets data. See [Participant - tags properties](#participant-tags-properties)

### Participant - Tags properties ###

| Attribute | Type | Description
| --------- | ---- | ----------------------------------------------|
`id` | string | tag marker ID
`title` | string | tag marker title
`color` | string | tag marker hex color


## List event participants

**Description:** List the participants of your event by event id

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/blinket/v1/event/{id}/participant</h6>
	</div>
</div>

```shell
curl GET https://example.com/blinket/v1/event/903uaj99-dbe6-442e-b4f6-47e34cf0m957/participant \
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
            "id": "902f3c60-271d-hab1-a999-f29021acacd1s",
            "status": "confirmed",
            "name": "Participant example 1",
            "email": "participant1@email.com",
            "invite_key": "000001-1"
        },
        {
            "id": "902f3c60-271d-hab1-a999-f29021acacd2a",
            "status": "confirmed",
            "name": "Participant example 2",
            "email": "participant2@email.com",
            "invite_key": "000001-2"
        }
    ]
}
```


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

## Retrieve an event participant

**Description:** Get your participant data of an event you have produced

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/blinket/v1/event/{eventId}/participant/{participantId}</h6>
	</div>
</div>

```shell
curl GET https://example.com/blinket/v1/event/903uaj99-dbe6-442e-b4f6-47e34cf0m957/participant/902f3c60-271d-hab1-a999-f29021acacd1s \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
    "id": "902f3c60-271d-hab1-a999-f29021acacd1s",
    "status": "confirmed",
    "name": "Participant example 1",
    "email": "participant1@email.com",
    "invite_key": "000001-1",
    "tags": [
        {
            "id": "manually",
            "title": "Adicionado Manualmente",
            "color": "blue"
        }
    ]
}
```

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
