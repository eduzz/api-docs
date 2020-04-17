# Jobzz: Serviço #

A API de serviços que permite gerenciar conteúdos.

## Propriedades do serviço ##

| Atributo | Tipo de dado | Descrição
| --------- | ---- | ----------------------------------------------|
`id` | number - integer | Identificador do serviço
`key` | string | Chave do serviço
`user_id` | number - integer | Identificador do prestador do serviço
`work_type` | string | Tipo do serviço (online, presential)
`moderation` | number - integer | Status da moderação do serviço
`type` | string | Tipo de pagamento do serviço (normal, signature)
`signature` | string | Código do contrato de assinatura
`cnt_cod` | number - integer | Código do serviço
`category_id` | number - integer | Identificador da categoria do serviço. Veja [Serviço - Propriedades das categorias](#servico-propriedade-das-categorias)
`sub_category_id` | number - integer | Identificador da subcategoria do serviço. Veja [Serviço - Propriedades das subcategorias](#servico-propriedade-das-subcategorias)
`title` | string | Título do serviço
`description` | string | Descrição do serviço
`visible` | number - integer | Campo informando se o serviço está visível na vitrine
`active` | number - integer | Campo informando se o serviço está disponível para venda
`value` | number - float | Valor do serviço
`value_type` | string | Tipo de cobrança
`deadline` | number - integer | Prazo de entrega do serviço
`deadline_type` | string | Tipo do prazo de entrega (meses, anos)
`automatic_start` | number - integer | Configuração para início automático do serviço
`images` | array | Imagens do serviço
`locations` | array | Locais onde seu serviço será prestado caso seja presencial
`certifications` | array | Certificações que o prestador possui
`negotiate` | number - integer | Campo informando se o serviço está aberto à negociações
`value_to_be_discussed` | boolean | Configuração de valor incial aberto a negociação
`created` | string - date-time | Data de criação do serviço
`modified` | string - date-time | Data da última modificação do serviço
`deleted` | string - date-time | Data em que o serviço foi deletado

## Serviço - Propriedade das categorias ##

`id` |  number - integer | Identificador da categoria
`key` |  string | Chave da categoria
`name` |  string | Nome da categoria
`created` |  string - date-time | Data de criação da categoria
`modified` |  string - date-time | Data da última modificação da categoria
`deleted` |  string - date-time | Data de exclusão da categoria

## Serviço - Propriedade das subcategorias ##

`id` |  number - integer | Identificador da subcategoria
`key` |  string | Chave da subcategoria
`category_id` |  number - integer | Identificador da categoria
`name` |  string | Nome da subcategoria
`created` |  string - date-time | Data de criação da subcategoria
`modified` |  string - date-time | Data da última modificação da subcategoria
`deleted` |  string - date-time | Data de exclusão da subcategoria

## Listar meus serviços

**Description:** Lista os servicos criados por mim

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/jobzz/v1/service</h6>
	</div>
</div>

```shell
curl GET https://example.com/jobzz/v1/service?page=1&per_page=2
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta JSON:

```json
{
    "pages": 1,
    "items_per_page": 2,
    "page": 1,
    "total_items": 2,
    "items": [
        {
          "id": 123,
          "key": "7c85574b",
          "user_id": 13,
          "work_type": "online",
          "moderation": 1,
          "type": "normal",
          "signature": null,
          "cnt_cod": 334747,
          "category_id": 1,
          "sub_category_id": 1,
          "title": "Example",
          "description": "This is an example of description",
          "visible": 0,
          "active": 1,
          "value": 1000.45,
          "value_type": "fixed",
          "deadline": 10,
          "deadline_type": "month",
          "automatic_start": 0,
          "images": [
              "/uploads/images/40/5f/488aa90009b99a2eeebdebe7432b.png"
          ],
          "locations": null,
          "certifications": null,
          "negotiate": 1,
          "value_to_be_discussed": false,
          "config": "{}",
          "created": "2020-04-02 11:05:31",
          "modified": "2020-04-02 11:18:45",
          "deleted": null
        },
        {
          "id": 1234,
          "key": "7c85574b",
          "user_id": 12,
          "work_type": "online",
          "moderation": 1,
          "type": "normal",
          "signature": null,
          "cnt_cod": 334747,
          "category_id": 1,
          "sub_category_id": 1,
          "title": "Example",
          "description": "This is an example of description",
          "visible": 0,
          "active": 1,
          "value": 1000.45,
          "value_type": "fixed",
          "deadline": 10,
          "deadline_type": "month",
          "automatic_start": 0,
          "images": [
              "/uploads/images/40/5f/488aa90009b99a2eeebdebe7432b.png"
          ],
          "locations": null,
          "certifications": null,
          "negotiate": 1,
          "value_to_be_discussed": false,
          "config": "{}",
          "created": "2020-04-02 11:05:31",
          "modified": "2020-04-02 11:18:45",
          "deleted": null
        }
    ]
}
```

**Parâmetros**

| Nome | Tipo do Parâmetro | Descrição | Obrigatório | Tipo de dado |
| ---- | ---------- | ----------- | -------- | ---- |
| page | query | Número da página referente a paginação | Não | integer |
| per_page | query | Items por página | Não | integer |
| moderation | query | Status da moderação do serviço | Não | integer |

**Respostas**

| Código | Descrição |
| ---- | ----------- |
| 200 | Sucesso |
| 404 | Dado não encontrado |


## Detalhes do serviço

**Description:** Exibe informações de um serviço específico através do seu identificador

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/jobzz/v1/service/{id}</h6>
	</div>
</div>

```shell
curl GET https://example.com/jobzz/v1/service/a66a65a7?page=1&per_page=2
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta JSON:

```json
{
    "id": 4863,
    "key": "a66a65a7",
    "user_id": 18115,
    "work_type": "online",
    "moderation": 3,
    "type": "normal",
    "signature": null,
    "cnt_cod": 305800,
    "category_id": 8,
    "sub_category_id": 0,
    "title": "Example",
    "description": "This is an example of description",
    "visible": 0,
    "active": 1,
    "value": 11.11,
    "value_type": "fixed",
    "deadline": 999,
    "deadline_type": "day",
    "automatic_start": 1,
    "images": [
        "/uploads/images/cd/5a/bd6c6655ea0e72472383911d70ec.png"
    ],
    "locations": [],
    "certifications": [],
    "negotiate": 1,
    "value_to_be_discussed": false,
    "config": null,
    "created": "2020-01-16 11:30:31",
    "modified": "2020-01-24 09:37:54",
    "deleted": null
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

## Criar serviço

**Description:** Cria um novo serviço na plataforma

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/jobzz/v1/service</h6>
	</div>
</div>

```shell
curl GET https://example.com/jobzz/v1/service/a66a65a7?page=1&per_page=2
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta JSON:

```json
{
  "id": 16260,
  "key": "e9e8ac97",
  "user_id": 18115,
  "work_type": "online",
  "moderation": 1,
  "type": "normal",
  "signature": null,
  "cnt_cod": null,
  "category_id": 1,
  "sub_category_id": 1,
  "group_id": 1,
  "title": "Example",
  "description": "This is an example of description",
  "visible": false,
  "active": true,
  "value": 1000.45,
  "value_type": null,
  "deadline": 10,
  "deadline_type": "month",
  "automatic_start": 0,
  "images": [
      "/uploads/images/4c/03/634bf06856d195c4e799e2719759.png"
  ],
  "locations": null,
  "certifications": null,
  "negotiate": 1,
  "value_to_be_discussed": false,
  "config": "{}",
  "created": "2020-01-16 11:30:31",
  "modified": "2020-01-24 09:37:54",
  "deleted": null
}
```

**Parâmetros**

| Nome | Tipo do Parâmetro | Descrição | Obrigatório | Tipo de dado |
| ---- | ---------- | ----------- | -------- | ---- |
| work_type | query | Tipo do serviço | Sim | string |
| type | query | Tipo de cobrança | Não | string |
| category | query | Categoria do serviço | Não | integer |
| sub_category_id | query | Subcategoria do serviço | Não | integer |
| title | query | Título do serviço | Sim | string |
| description | query | Descrição do serviço | Sim | string |
| visible | query | Visibilidade na vitrine da plataforma | Não | boolean |
| active | query | Disponibilidade de venda | Não | boolean |
| value | query | Valor do serviço | Sim | number - float |
| deadline | query | Prazo de entrega | Sim | number - integer |
| deadline_type | query | Tipo de prazo de entrega | Sim | string |
| images | query | Imagens do serviço | Sim | array |
| location | query | Locais onde seu serviço será prestado caso presencial | Não | array |
| location.*.country | query | País onde seu serviço será prestado caso presencial | Não | string |
| location.*.state | query | Estado onde seu serviço será prestado caso presencial | Não | string |
| location.*.cities | query | Cidades onde seu serviço será prestado caso presencial | Não | array |
| location.*.cities | query | Cidade onde seu serviço será prestado caso presencial | Não | string |
| negotiation | query | Disponibilidade de negociação | Não | boolean |
| automatic_start | query | Início imediatamente após a compra | Não | boolean |
| value_to_be_discussed | query | Valor inicial do serviço a ser discutido | Sim | boolean |

**Respostas**

| Código | Descrição |
| ---- | ----------- |
| 200 | Sucesso |
| 404 | Dado não encontrado |

## Editar serviço

**Description:** Edita um serviço na plataforma através do seu identificador

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">PUT</i>
		<h6>/jobzz/v1/service/e9e8ac97</h6>
	</div>
</div>

```shell
curl GET https://example.com/jobzz/v1/service/a66a65a7?page=1&per_page=2
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta JSON:

```json
{
  "id": 16260,
  "key": "e9e8ac97",
  "user_id": 18115,
  "work_type": "online",
  "moderation": 1,
  "type": "normal",
  "signature": null,
  "cnt_cod": 342827,
  "category_id": 1,
  "sub_category_id": 1,
  "title": "Example",
  "description": "This is an example of description",
  "visible": 0,
  "active": 1,
  "value": 10,
  "value_type": "fixed",
  "deadline": 4,
  "deadline_type": "day",
  "automatic_start": 0,
  "images": [
      "/uploads/images/a5/f0/62356680585b9d4d802a666a9d9e.png"
  ],
  "locations": null,
  "certifications": null,
  "negotiate": 1,
  "value_to_be_discussed": false,
  "config": "{}",
  "created": "2020-04-16 14:34:42",
  "modified": "2020-04-16 14:34:44",
  "deleted": null
}
```

**Parâmetros**

| Nome | Tipo do Parâmetro | Descrição | Obrigatório | Tipo de dado |
| ---- | ---------- | ----------- | -------- | ---- |
| work_type | query | Tipo do serviço | Sim | string |
| type | query | Tipo de cobrança | Não | string |
| category | query | Categoria do serviço | Não | integer |
| sub_category_id | query | Subcategoria do serviço | Não | integer |
| title | query | Título do serviço | Sim | string |
| description | query | Descrição do serviço | Sim | string |
| visible | query | Visibilidade na vitrine da plataforma | Não | boolean |
| active | query | Disponibilidade de venda | Não | boolean |
| value | query | Valor do serviço | Sim | number - float |
| deadline | query | Prazo de entrega | Sim | number - integer |
| deadline_type | query | Tipo de prazo de entrega | Sim | string |
| images | query | Imagens do serviço | Sim | array |
| location | query | Locais onde seu serviço será prestado caso presencial | Não | array |
| location.*.country | query | País onde seu serviço será prestado caso presencial | Não | string |
| location.*.state | query | Estado onde seu serviço será prestado caso presencial | Não | string |
| location.*.cities | query | Cidades onde seu serviço será prestado caso presencial | Não | array |
| location.*.cities | query | Cidade onde seu serviço será prestado caso presencial | Não | string |
| negotiation | query | Disponibilidade de negociação | Não | boolean |
| automatic_start | query | Início imediatamente após a compra | Não | boolean |
| value_to_be_discussed | query | Valor inicial do serviço a ser discutido | Sim | boolean |

**Respostas**

| Código | Descrição |
| ---- | ----------- |
| 200 | Sucesso |
| 404 | Dado não encontrado |

## Excluir serviço

**Description:** Exclui um serviço da plataforma através do seu identificador

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">DELETE</i>
		<h6>/jobzz/v1/service/e9e8ac97</h6>
	</div>
</div>

```shell
curl GET https://example.com/jobzz/v1/service/a66a65a7?page=1&per_page=2
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

**Parâmetros**

| Nome | Tipo do Parâmetro | Descrição | Obrigatório | Tipo de dado |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | Identificador do serviço | Sim | string |

**Respostas**

| Código | Descrição |
| ---- | ----------- |
| 204 | Sucesso |
| 404 | Dado não encontrado |

## Listar categorias

**Description:** Lista categorias da plataforma

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/jobzz/v1/category</h6>
	</div>
</div>

```shell
curl GET https://example.com/jobzz/v1/category
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta JSON:

```json
[
  {
      "id": 5,
      "key": "bc8f7202",
      "name": "Design e Animação",
      "created": "2019-03-15 14:09:34",
      "modified": "2020-04-06 15:29:46",
      "deleted": null
  },
  {
      "id": 1,
      "key": "f286baaf",
      "name": "Finanças",
      "created": "2019-03-15 14:09:34",
      "modified": "2019-03-15 14:09:34",
      "deleted": null
  },
  {
      "id": 6,
      "key": "bf0df829",
      "name": "Marketing Digital e Vendas",
      "created": "2019-03-15 14:09:35",
      "modified": "2020-04-06 15:30:17",
      "deleted": null
  },
  {
      "id": 207,
      "key": "eb6d21f6",
      "name": "Negócios",
      "created": "2019-08-12 10:56:58",
      "modified": "2020-04-09 14:50:28",
      "deleted": null
  },
  {
      "id": 2,
      "key": "38d94de6",
      "name": "Saúde e Beleza",
      "created": "2019-03-15 14:09:34",
      "modified": "2020-04-06 15:29:08",
      "deleted": null
  },
  {
      "id": 7,
      "key": "9a256e48",
      "name": "Sites e Tecnologia",
      "created": "2019-03-15 14:09:35",
      "modified": "2020-04-06 15:30:57",
      "deleted": null
  }
]
```

**Respostas**

| Código | Descrição |
| ---- | ----------- |
| 200 | Sucesso |
| 404 | Dado não encontrado |

## Listar subcategorias

**Description:** Lista subcategorias da plataforma

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/jobzz/v1/sub_category</h6>
	</div>
</div>

```shell
curl GET https://example.com/jobzz/v1/sub_category
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta JSON:

```json
[
  {
      "id": 106,
      "key": "b84c0f5b",
      "category_id": 5,
      "name": "Fotografia e Edição de Imagens",
      "created": "2020-04-14 12:08:19",
      "modified": "2020-04-14 12:08:19",
      "deleted": null
  },
  {
      "id": 82,
      "key": "ade7dbef",
      "category_id": 5,
      "name": "AudioBook",
      "created": "2020-04-14 09:52:55",
      "modified": "2020-04-14 10:02:15",
      "deleted": null
  },
  {
      "id": 81,
      "key": "65367aac",
      "category_id": 5,
      "name": "Identidade Visual",
      "created": "2020-04-14 09:52:55",
      "modified": "2020-04-14 10:02:15",
      "deleted": null
  },
  {
      "id": 80,
      "key": "3e7c9a5b",
      "category_id": 5,
      "name": "Artes para Rede Social",
      "created": "2020-04-14 09:52:55",
      "modified": "2020-04-14 10:02:15",
      "deleted": null
  },
  {
      "id": 65,
      "key": "8f300630",
      "category_id": 5,
      "name": "Locução e Produção de Áudio",
      "created": "2019-10-22 14:58:52",
      "modified": "2020-04-16 09:00:37",
      "deleted": null
  },
  {
      "id": 51,
      "key": "60a84235",
      "category_id": 5,
      "name": "Cartão de Visita",
      "created": "2019-06-26 17:10:08",
      "modified": "2019-06-26 17:10:08",
      "deleted": null
  },
  {
      "id": 14,
      "key": "a2147feb",
      "category_id": 5,
      "name": "Criação de Logo",
      "created": "2019-03-15 14:09:37",
      "modified": "2020-04-06 15:32:56",
      "deleted": null
  },
  {
      "id": 8,
      "key": "9ac68854",
      "category_id": 5,
      "name": "Produção e Edição de Vídeo",
      "created": "2019-03-15 14:09:36",
      "modified": "2020-04-16 09:00:37",
      "deleted": null
  }
]
```

**Parâmetros**

| Nome | Tipo do Parâmetro | Descrição | Obrigatório | Tipo de dado |
| ---- | ---------- | ----------- | -------- | ---- |
| category_id | path | Identificador da categoria | Sim | number - integer |

**Respostas**

| Código | Descrição |
| ---- | ----------- |
| 200 | Sucesso |
| 404 | Dado não encontrado |
