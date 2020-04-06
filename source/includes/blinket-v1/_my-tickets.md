# Blinket: Meus Tickets #

A API Blinket Meus Tickets permite visualizar dados de tickets de eventos dos quais você participou.

## Meus tickets - propriedades do evento ##

| Atributo | Tipo de dado | Descrição
| --------- | ---- | ----------------------------------------------|
`id` | string | Identificador do evento
`type` | string | Tipo do evento (online, presential)
`title` | string | Título do evento
`description` | string | Descrição do evento
`sale_url` | string | URL da página de vendas do evento
`stream_url` | string | URL de transmissão do evento (Somente evento Online)
`start_date` | string - date-time | Data de início do evento (formato: UTC)
`end_date` | string - date-time | Data de fim do evento (formato: UTC)
`place` | string | Local onde será realizado o evento
`country` | string | País onde será realizado o evento
`state` | string | Estado onde será realizado o evento
`city` | string | Cidade onde será realizado o evento
`district` | string | Bairro onde será realizado o evento
`street` | string | Rua onde será realizado o evento
`complement` | string | Complemento onde será realizado o evento
`number` | string | Número onde será realizado o evento
`zip` | string | CEP onde será realizado o evento
`reference` | string | Referência onde será realizado o evento

## Listar eventos que participei

**Description:** Lista os eventos no quais participei

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

**Parâmetros**

| Nome | Tipo do Parâmetro | Descrição | Obrigatório | Tipo de dado |
| ---- | ---------- | ----------- | -------- | ---- |
| page | query | Número da página referente a paginação | Não | integer |
| title | query | Título do evento que deseja buscar | Não | string |
| type | query | Tipo do evento que deseja buscar (online, presential) | Não | string |

**Respostas**

| Código | Descrição |
| ---- | ----------- |
| 200 | Sucesso |
| 404 | Dado não encontrado |

## Meus Tickets - propriedades do convite ##

| Atributo | Tipo de dado | Descrição
| --------- | ---- | ----------------------------------------------|
`id` | string | Identificador do convite
`name` | string | Nome do participante
`email` | string | Email do participante
`invoice_id` | integer | Número da fatura Eduzz
`invite_key` | string | Código do convite do participante
`content_id` | integer | Código do conteúdo da eduzz
`status` | string | Status do convite do participante (paid, refunded, locked, presence_confirmed, confirmed)
`invite_url` | string | URL de confirmação de presença.
`ticket_name` | string | Nome do ticket do convite
`ticket_is_paid` | boolean | Se o ticket do convite é pago ou gratuíto
`ticket_show_on_page` | boolean | Se o ticket é exibido na página de vendas.

## Listar convites de um evento que participei

**Description:** Lista os convites de um evento que participei

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

**Parâmetros**

| Nome | Tipo do parâmetro | Descrição | Obrigatório | Tipo de dado |
| ---- | ---------- | ----------- | -------- | ---- |
| eventId | path | Identificador de um evento que participei | Sim | string |
| page | query | Número da página referente a paginação. | Não | integer |

**Respostas**

| Código | Descrição |
| ---- | ----------- |
| 200 | Sucesso |
| 404 | Dado não encontrado |

