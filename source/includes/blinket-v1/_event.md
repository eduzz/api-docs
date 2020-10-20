# Blinket: Meus Eventos

## Meus Eventos

A API de eventos do Blinket permite visualizar os dados dos eventos que o produtor criou.

### Propriedades do evento

| Atributo     | Tipo de dado       | Descrição                                                                                               |
| ------------ | ------------------ | ------------------------------------------------------------------------------------------------------- |
| `id`         | string             | Código UUID do evento                                                                                   |
| `type`       | string             | Tipo do evento (online, presential)                                                                     |
| `title`      | string             | Título do evento.                                                                                       |
| `Descrição`  | string             | Descrição do evento                                                                                     |
| `sale_url`   | string             | URL da página de vendas do evento                                                                       |
| `stream_url` | string             | URL de transmissão do evento (Somente evento Online)                                                    |
| `start_date` | string - date-time | Data de início do evento (formato: UTC)                                                                 |
| `end_date`   | string - date-time | Data de fim do evento (formato: UTC)                                                                    |
| `place`      | string             | Local onde será realizado o evento                                                                      |
| `country`    | string             | País onde será realizado o evento                                                                       |
| `state`      | string             | Estado onde será realizado o evento                                                                     |
| `city`       | string             | Cidade onde será realizado o evento                                                                     |
| `district`   | string             | Bairro onde será realizado o evento                                                                     |
| `street`     | string             | Rua onde será realizado o evento                                                                        |
| `complement` | string             | Complemento onde será realizado o evento                                                                |
| `number`     | string             | Número onde será realizado o evento                                                                     |
| `zip`        | string             | CEP onde será realizado o evento                                                                        |
| `reference`  | string             | Referência onde será realizado o evento                                                                 |
| `tickets`    | array              | Dados dos tickets do evento. Veja [Evento - Propriedades dos tickets](#evento-propriedades-dos-tickets) |

### Propriedades dos tickets

A entidade ticket está abaixo de eventos, e acima de lotes. Um ticket pode possuir um ou mais lotes.

| Atributo            | Tipo de dado | Descrição                                                                               |
| ------------------- | ------------ | --------------------------------------------------------------------------------------- |
| `id`                | string       | Código UUID do ticket                                                                   |
| `name`              | string       | Nome do ticket                                                                          |
| `is_paid`           | boolean      | Se o ticket é pago ou gratuito                                                          |
| `show_on_sale_page` | boolean      | Se o ticket está visível na página de vendas                                            |
| `lots`              | array        | Dados dos lotes. Veja [Evento - Propriedades dos lotes](#evento-propriedades-dos-lotes) |

### Propriedades dos lotes

A entidade lote está abaixo de tickets. Um lote pertence a apenas um ticket, que está abaixo de um determinado evento.

| Atributo          | Tipo de dado       | Descrição                                        |
| ----------------- | ------------------ | ------------------------------------------------ |
| `id`              | string             | Código UUID do lote                              |
| `content_id`      | integer            | Código do conteúdo Eduzz                         |
| `start_sale_date` | string - date-time | Data de início das vendas do lote (formato: UTC) |
| `end_sale_date`   | string - date-time | Data de fim das vendas do lote (formato: UTC)    |
| `total_stock`     | integer            | Estoque total do lote                            |
| `value`           | number - float     | Preço unitário do lote                           |

## Meus Eventos: Listar eventos

**Descrição:** Liste os eventos que você organizou

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
      "Descrição": "Example 1 Descrição",
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
      "Descrição": "Example 2 Descrição",
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

| Nome  | Tipo do Parâmetro | Descrição                                             | Obrigatório | Tipo de dado |
| ----- | ----------------- | ----------------------------------------------------- | ----------- | ------------ |
| page  | query             | Número da página referente a paginação                | Não         | integer      |
| title | query             | Título do evento que deseja buscar                    | Não         | string       |
| type  | query             | Tipo do evento que deseja buscar (online, presential) | Não         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus Eventos: Detalhes de um evento

**Descrição:** Obtém os detalhes de um evento através de seu Código UUID

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/blinket/v1/event/{Código UUID do evento}</h6>
	</div>
</div>

```shell
curl GET https://example.com/blinket/v1/event/{id} \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta JSON:

```json
{
  "id": "903uaj99-dbe6-442e-b4f6-47e34cf0m957",
  "type": "presential",
  "title": "Example",
  "Descrição": "This is a example Descrição",
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

| Nome | Tipo do Parâmetro | Descrição             | Obrigatório | Tipo de dado |
| ---- | ----------------- | --------------------- | ----------- | ------------ |
| id   | path              | Código UUID do evento | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |
