# Órbita: Vendas

A API de vendas do Órbita permite visualizar os dados das vendas.

## Listar vendas

**Description:** Liste as vendas que você efetuou

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/orbita/v1/sales</h6>
	</div>
</div>

```shell
curl GET https://example.com/orbita/v1/sales?start_date=2020-01-01&end_date=2020-01-07 \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta JSON:

```json
{
  "pages": 57,
  "items_per_page": 25,
  "page": 1,
  "total_items": 1402,
  "items": [
    {
      "id": 123321,
      "created_at": "2020-08-09T02:54:38Z",
      "paid_at": "2020-08-09T02:54:41Z",
      "discount_amount": 0,
      "is_recover": false,
      "is_infinite_funnel": false,
      "gross_gain": 480.09,
      "net_gain": 480.09,
      "affiliate_gain": 0,
      "fee_value": -18.91,
      "others_fees_values": 0,
      "total_value": 499,
      "total_interest_value": 499,
      "refund_value": 0,
      "payment_method": "Mastercard",
      "client": {
        "id": 123321,
        "name": "Nome do Cliente",
        "email": "emaildocliente@dominio.com",
        "document": "X99999999999",
        "foreign_document": null,
        "cellphone": "11999999999",
        "country": "BR",
        "state": "SP",
        "city": "São Paulo",
        "neighborhood": "11999999999",
        "zipcode": "18000000",
        "street": "Rua Endereço do Cliente",
        "addr_number": "1997",
        "addr_complement": "complemento do endereço",
        "language": "PT"
      },
      "producer": {
        "name": "Nome do Produtor"
      },
      "affiliate": {
        "name": "Nome do Afiliado"
      },
      "main_content": {
        "id": 99999999,
        "name": "Nome do Conteúdo",
        "sku": "SKU_Conteudo"
      },
      "status": {
        "name": "Paga"
      },
      "utm_source": "utm_source",
      "utm_campaign": "utm_campaign",
      "utm_medium": "utm_medium",
      "utm_content": "utm_content",
      "tracker": "trk",
      "tracker2": "trk2",
      "tracker3": "tr3"
    }
  ]
}
```

| Atributo                  | Tipo de dado       | Descrição                                    |
| ------------------------- | ------------------ | -------------------------------------------- |
| `id`                      | integer            | Identificador da venda                       |
| `created_at`              | string - date-time | Data de criação da venda                     |
| `paid_at`                 | string - date-time | Data de pagamento da venda                   |
| `discount_amount`         | number - float     | Valor do desconto                            |
| `is_recover`              | boolean            | Se foi uma venda recuperada                  |
| `is_infinite_funnel`      | boolean            | Se foi uma venda por funil infinito          |
| `gross_gain`              | number - float     | Ganho bruto da venda                         |
| `net_gain`                | number - float     | Ganho líquido da venda                       |
| `affiliate_gain`          | number - float     | Ganho líquido do afiliado                    |
| `fee_value`               | number - float     | Taxa da Eduzz sobre a venda                  |
| `others_fees_values`      | number - float     | Outras valores                               |
| `total_value`             | number - float     | Valor total da venda                         |
| `total_interest_value`    | number - float     | Valor total da venda com juros               |
| `refund_value`            | number - float     | Valor de reembolso                           |
| `payment_method`          | string             | Descrição do método de pagamento             |
| `client.id`               | integer            | Identificador do cliente                     |
| `client.name`             | string             | Nome do cliente                              |
| `client.email`            | string             | E-mail do cliente                            |
| `client.document`         | string             | Documento do cliente                         |
| `client.foreign_document` | string             | Documento Estrangeiro do cliente             |
| `client.cellphone`        | string             | Celular do cliente                           |
| `client.country`          | string             | País do cliente                              |
| `client.state`            | string             | Estado do cliente                            |
| `client.city`             | string             | Cidade do cliente                            |
| `client.neighborhood`     | string             | Bairro do cliente                            |
| `client.zipcode`          | string             | CEP do cliente                               |
| `client.street`           | string             | Rua do cliente                               |
| `client.addr_number`      | string             | Número do endereço do cliente                |
| `client.addr_complement`  | string             | Complemento do endereço do cliente           |
| `client.language`         | string             | Idioma do cliente                            |
| `producer.name`           | string             | Nome do Produtor                             |
| `affiliate.name`          | string             | Nome do Afiliado                             |
| `main_content.id`         | integer            | Identificador do principal conteúdo da venda |
| `main_content.name`       | string             | Nome do principal conteúdo da venda          |
| `main_content.sku`        | string             | SKU do princiupal conteúdo da venda          |
| `status.name`             | string             | Descrição do status da venda                 |
| `utm_source`              | string             | UTM Source da venda                          |
| `utm_campaign`            | string             | UTM Campaign da venda                        |
| `utm_medium`              | string             | UTM Medium da venda                          |
| `utm_content`             | string             | UTM Content                                  |
| `tracker`                 | string             | Tracker da venda                             |
| `tracker2`                | string             | Tracker 2 da venda                           |
| `tracker3`                | string             | Tracker 3 da venda                           |

**Parâmetros**

| Nome       | Tipo do Parâmetro | Descrição                                                                                                                      | Obrigatório | Tipo de dado  |
| ---------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------ | ----------- | ------------- |
| start_date | query             | Data inicial para listar as vendas                                                                                             | Sim         | string - date |
| end_date   | query             | Data final para listar as vendas                                                                                               | Sim         | string - date |
| date_type  | query             | Tipo de data da venda - "creation" (criação) ou "payment" (pagamento)                                                          | Não         |
| status     | query             | Status da Venda (open, paid, canceled, waiting_refund, refunded, duplicated, expired, recovering, waiting_payment, negociated) | Não         | integer       |
| page       | query             | Número da página referente a paginação                                                                                         | Não         | integer       |
| per_page   | query             | Registros por página (max 25)                                                                                                  | Não         | integer       |

**Respostas**

| Código | Descrição |
| ------ | --------- |
| 200    | Sucesso   |

## Retornar uma venda

**Description:** Retorna uma venda que você efetuou

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/orbita/v1/sales/{id}</h6>
	</div>
</div>

```shell
curl GET https://example.com/orbita/v1/sales/123321 \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta JSON:

```json
{
  "id": 123321,
  "created_at": "2020-08-09T02:54:38Z",
  "paid_at": "2020-08-09T02:54:41Z",
  "discount_amount": 0,
  "is_recover": false,
  "is_infinite_funnel": false,
  "gross_gain": 480.09,
  "net_gain": 480.09,
  "affiliate_gain": 0,
  "fee_value": -18.91,
  "others_fees_values": 0,
  "total_value": 499,
  "total_interest_value": 499,
  "refund_value": 0,
  "payment_method": "Mastercard",
  "client": {
    "id": 123321,
    "name": "Nome do Cliente",
    "email": "emaildocliente@dominio.com",
    "document": "X99999999999",
    "foreign_document": null,
    "cellphone": "11999999999",
    "country": "BR",
    "state": "SP",
    "city": "São Paulo",
    "neighborhood": "11999999999",
    "zipcode": "18000000",
    "street": "Rua Endereço do Cliente",
    "addr_number": "1997",
    "addr_complement": "complemento do endereço",
    "language": "PT"
  },
  "producer": {
    "name": "Nome do Produtor"
  },
  "affiliate": {
    "name": "Nome do Afiliado"
  },
  "main_content": {
    "id": 99999999,
    "name": "Nome do Conteúdo",
    "sku": "SKU_Conteudo"
  },
  "status": {
    "name": "Paga"
  },
  "utm_source": "utm_source",
  "utm_campaign": "utm_campaign",
  "utm_medium": "utm_medium",
  "utm_content": "utm_content",
  "tracker": "trk",
  "tracker2": "trk2",
  "tracker3": "tr3",
  "items": [
    {
      "description": "Descrição do Item da Venda",
      "type": "Infoproduto",
      "sku": "SKU_Item",
      "is_bump": false,
      "quantity": 1,
      "value": 79.2,
      "coupon_key": null,
      "discount": 0,
      "gross_gain": 0,
      "net_gain": 0,
      "partner_gain": 0,
      "total_value": 79.2,
      "total_interest_value": 79.2,
      "fee_value": 0,
      "anticipation_value": 0,
      "others_fees_values": 0
    }
  ]
}
```

| Atributo                     | Tipo de dado       | Descrição                                    |
| ---------------------------- | ------------------ | -------------------------------------------- |
| `id`                         | integer            | Identificador da venda                       |
| `created_at`                 | string - date-time | Data de criação da venda                     |
| `paid_at`                    | string - date-time | Data de pagamento da venda                   |
| `discount_amount`            | number - float     | Valor do desconto                            |
| `is_recover`                 | boolean            | Se foi uma venda recuperada                  |
| `is_infinite_funnel`         | boolean            | Se foi uma venda por funil infinito          |
| `gross_gain`                 | number - float     | Ganho bruto da venda                         |
| `net_gain`                   | number - float     | Ganho líquido da venda                       |
| `affiliate_gain`             | number - float     | Ganho líquido do afiliado                    |
| `fee_value`                  | number - float     | Taxa da Eduzz sobre a venda                  |
| `others_fees_values`         | number - float     | Outras valores                               |
| `total_value`                | number - float     | Valor total da venda                         |
| `total_interest_value`       | number - float     | Valor total da venda com juros               |
| `refund_value`               | number - float     | Valor de reembolso                           |
| `payment_method`             | string             | Descrição do método de pagamento             |
| `client.id`                  | integer            | Identificador do cliente                     |
| `client.name`                | string             | Nome do cliente                              |
| `client.email`               | string             | E-mail do cliente                            |
| `client.document`            | string             | Documento do cliente                         |
| `client.foreign_document`    | string             | Documento Estrangeiro do cliente             |
| `client.cellphone`           | string             | Celular do cliente                           |
| `client.country`             | string             | País do cliente                              |
| `client.state`               | string             | Estado do cliente                            |
| `client.city`                | string             | Cidade do cliente                            |
| `client.neighborhood`        | string             | Bairro do cliente                            |
| `client.zipcode`             | string             | CEP do cliente                               |
| `client.street`              | string             | Rua do cliente                               |
| `client.addr_number`         | string             | Número do endereço do cliente                |
| `client.addr_complement`     | string             | Complemento do endereço do cliente           |
| `client.language`            | string             | Idioma do cliente                            |
| `producer.name`              | string             | Nome do Produtor                             |
| `affiliate.name`             | string             | Nome do Afiliado                             |
| `main_content.id`            | integer            | Identificador do principal conteúdo da venda |
| `main_content.name`          | string             | Nome do principal conteúdo da venda          |
| `main_content.sku`           | string             | SKU do princiupal conteúdo da venda          |
| `status.name`                | string             | Descrição do status da venda                 |
| `utm_source`                 | string             | UTM Source da venda                          |
| `utm_campaign`               | string             | UTM Campaign da venda                        |
| `utm_medium`                 | string             | UTM Medium da venda                          |
| `utm_content`                | string             | UTM Content                                  |
| `tracker`                    | string             | Tracker da venda                             |
| `tracker2`                   | string             | Tracker 2 da venda                           |
| `tracker3`                   | string             | Tracker 3 da venda                           |
| `items.description`          | string             | Descrição do item                            |
| `items.type`                 | string             | Tipo do item                                 |
| `items.sku`                  | string             | SKU do item                                  |
| `items.is_bump`              | boolean            | Se foi o item de Order Bump                  |
| `items.quantity`             | integer            | Quantidade do item                           |
| `items.value`                | number - float     | Valor unitário do item                       |
| `items.description`          | string             | Descrição do item                            |
| `items.coupon_key`           | string             | Código de cupom de desconto do item          |
| `items.discount`             | number - float     | Desconto do item                             |
| `items.gross_gain`           | number - float     | Ganho bruto do item                          |
| `items.net_gain`             | number - float     | Ganho líquido do item                        |
| `items.partner_gain`         | number - float     | Ganho do parceiro no item                    |
| `items.total_value`          | number - float     | Valor total do item                          |
| `items.total_interest_value` | number - float     | Valor total do item com juros                |
| `items.fee_value`            | number - float     | Valor da taxa sobre o item                   |
| `items.anticipation_value`   | number - float     | Valor de antecipação do item                 |
| `items.others_fees_values`   | number - float     | Outras taxas sobre o item                    |

**Parâmetros**

| Nome | Tipo do Parâmetro | Descrição              | Obrigatório | Tipo de dado |
| ---- | ----------------- | ---------------------- | ----------- | ------------ |
| id   | path              | Identificador da venda | Sim         | integer      |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |
