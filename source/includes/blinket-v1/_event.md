# Blinket: Eventos #

A API de eventos do Blinket permite visualizar os dados do evento.

## Propriedades do evento ##

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
`tickets` | array | Dados dos tickets do evento. Veja [Evento - Propriedades dos tickets](#evento-propriedades-dos-tickets)

### Evento - Propriedades dos tickets ###

| Atributo | Tipo de dado | Descrição
| --------- | ---- | ----------------------------------------------|
`id` | string | Identificador do ticket
`name` | string | Nome do ticket
`is_paid` | boolean | Se o ticket é pago ou gratuito
`show_on_sale_page` | boolean | Se o ticket está visível na página de vendas
`lots` | array | Dados dos lotes. Veja [Evento - Propriedades dos lotes](#evento-propriedades-dos-lotes)

### Evento - Propriedades dos lotes ###

| Atributo | Tipo de dado | Descrição
| --------- | ---- | ----------------------------------------------|
`id` | string | Identificador do lote
`content_id` | integer | Código do conteúdo Eduzz
`start_sale_date` | string - date-time | Data de início das vendas do lote (formato: UTC)
`end_sale_date` | string - date-time | Data de fim das vendas do lote (formato: UTC)
`total_stock` | integer | Estoque total do lote
`value` | number - float | Preço unitário do lote

## Listar eventos

**Description:** Liste os eventos que você organizou

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

> Exemplo de resposta JSON:

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

## Retornar um evento

**Description:** Obtenha os dados de um evento seu através do identificador

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

> Exemplo de resposta JSON:

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

**Parâmetros**

| Nome | Tipo do Parâmetro | Descrição | Obrigatório | Tipo de dado |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Identficador do evento | Sim | string |

**Respostas**

| Código | Descrição |
| ---- | ----------- |
| 200 | Sucesso |
| 404 | Dado não encontrado |

## Propriedades do participante ##

| Atributo | Tipo de dado | Descrição
| --------- | ---- | ----------------------------------------------|
`id` | string | Identificador do participante
`status` | string | Status do participante (paid, refunded, locked, presence_confirmed, confirmed)
`name` | string | Nome do participante
`email` | string | Email do participante
`invite_key` | string | Código do convite do participante
`tags` | array | Marcadores do participante. Veja [Participantes - Marcadores propriedades](#participantes-marcadores-propriedades)

### Participantes - Propriedades dos marcadores ###

| Atributo | Tipo de dado | Descrição
| --------- | ---- | ----------------------------------------------|
`id` | string | Identificador do marcador
`title` | string | Título do marcador
`color` | string | Cor do marcador (formato HEX HTML)


## Listar participantes de um evento

**Description:** Listar os participantes de um evento através do identificador do evento

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

> Exemplo de resposta JSON:

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


**Parâmetros**

| Nome | Tipo do parâmetro | Descrição | Obrigatório | Tipo de dado |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Identificador do evento | Sim | string |
| page | query | Número da página referente a paginação | Não | integer |
| ticket_id | query | Identificador de um ticket do evento | Não | string |
| status | query | Status do participante que deseja buscar | Não | string |
| invite_key | query | Código do convite do participante que deseja buscar | Não | string |
| name | query | Nome do Participante | Não | string |
| email | query | Email do Participante | Não | string |

**Respostas**

| Código | Descrição |
| ---- | ----------- |
| 200 | Sucesso |
| 404 | Dado não encontrado |

## Obter um participante

**Description:** Obter um participante através do identificador do evento e identificador do participante

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

> Exemplo de resposta JSON:

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

**Parâmetros**

| Nome | Tipo do parâmetro | Descrição | Obrigatório | Tipo de dado |
| ---- | ---------- | ----------- | -------- | ---- |
| eventId | path | Identificador do evento | Sim | string |
| participantId | path | Identificador do participante | Sim | string |

**Respostas**

| Code | Description |
| ---- | ----------- |
| 200 | Sucesso |
| 404 | Dado não encontrado |
