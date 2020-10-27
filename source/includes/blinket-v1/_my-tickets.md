# Blinket: Meus Tickets

A API Blinket Meus Tickets permite visualizar dados de tickets de eventos dos quais você participou.

## Meus tickets - propriedades do evento

| Atributo             | Tipo de dado       | Descrição                                                     |
| -------------------- | ------------------ | ------------------------------------------------------------- |
| `id`                 | string             | Identificador do evento                                       |
| `type`               | string             | Tipo do evento (online, presential)                           |
| `title`              | string             | Título do evento                                              |
| `description`        | string             | Descrição do evento                                           |
| `start_date`         | string - date-time | Data de início do evento (formato: UTC)                       |
| `end_date`           | string - date-time | Data de fim do evento (formato: UTC)                          |
| `sale_url`           | string             | URL da página de vendas do evento                             |
| `event_img_url`      | string             | URL da imagem do evento                                       |
| `stream_url`         | string             | URL de transmissão do evento (Somente evento Online)          |
| `unassigned`         | string             | Ingressos sem atribuição, que é necessário confirmar os dados |
| `is_gift`            | string             | Se o ticket é presente                                        |
| `address.place`      | string             | Local onde será realizado o evento                            |
| `address.country`    | string             | País onde será realizado o evento                             |
| `address.state`      | string             | Estado onde será realizado o evento                           |
| `address.city`       | string             | Cidade onde será realizado o evento                           |
| `address.district`   | string             | Bairro onde será realizado o evento                           |
| `address.street`     | string             | Rua onde será realizado o evento                              |
| `address.complement` | string             | Complemento onde será realizado o evento                      |
| `address.number`     | string             | Número onde será realizado o evento                           |
| `address.zip`        | string             | CEP onde será realizado o evento                              |
| `address.reference`  | string             | Referência onde será realizado o evento                       |

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
curl GET https://api-eduzz.com/blinket/v1/my-tickets/event?page=1&title=test&type=presential \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
  "pages": 1,
  "items_per_page": 25,
  "page": 1,
  "total_items": 25,
  "items": [
    {
      "event_id": "907785d6-7d12-4d42-b746-912993a4e267",
      "type": "presential",
      "title": "Imersão Especialista em Marketing Digital 2021 - São Paulo",
      "description": "O mundo est&aacute; cada vez mais digitalizado. Com mais de 1 bilh&atilde;o de usu&aacute;rios, a m&iacute;dia digital est&aacute; criando um impacto significativo em nossas vidas diariamente. \n\nPensando nisso, n&oacute;s criamos um ambiente totalmente controlado para que voc&ecirc; fique totalmente imerso durante 2 dias com os melhores especialistas em marketing digital e ao fim dessa jornada voc&ecirc; seja capaz de trabalhar totalmente focado no markting digital. ",
      "start_date": "2021-01-15 08:00:00",
      "end_date": "2021-01-17 17:00:00",
      "sale_url": "https://evento.blinket.com.br/imersao-especialista-em-marketing-digital-2020-sp",
      "event_img_src": "https://cdn.eduzzcdn.com/myeduzz/upload/cd/b8/cdb81ed2ff214024a185acdf348e015a",
      "stream_url": null,
      "unassigned": 0,
      "is_gift": 0,
      "address": {
        "place": "Anfiteatro Camargo Guarnieri, University of São Paulo",
        "street": "Rua do Anfiteatro",
        "number": "109",
        "complement": "Anfiteatro Vermelho",
        "reference": "Próximo à Raia Olímpica da USP",
        "district": "Butantã",
        "state": "SP",
        "zip": "05508-060",
        "city": "São Paulo",
        "country": "Brazil"
      }
    },
    {
      "event_id": "8d66dd17-2715-467e-8ffb-b1abedc4808e",
      "type": "presential",
      "title": "Feira de Carreiras",
      "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus quis lorem nec ante tincidunt porttitor. Nulla et condimentum nunc. Sed vitae magna orci. Quisque gravida leo id nisi commodo vestibulum. Vivamus id ligula eget risus blandit vestibulum non nec metus. Maecenas condimentum a justo eget accumsan. Nulla in pretium tortor.",
      "start_date": "2019-04-26 07:00:00",
      "end_date": "2019-04-28 18:00:00",
      "sale_url": "https://evento.blinket.com.br/feira_de_carreiras",
      "event_img_src": "https://cdn.eduzzcdn.com/myeduzz/upload/87/48/8748ed441da04d30ac4a0f9e63ad7807",
      "stream_url": null,
      "unassigned": 0,
      "is_gift": 1,
      "address": {
        "place": "Impacta Certificação e Treinamento",
        "street": "Avenida Paulista",
        "number": "1009",
        "complement": null,
        "reference": null,
        "district": "Bela Vista",
        "state": "SP",
        "zip": "01311-100",
        "city": "São Paulo",
        "country": "Brasil"
      }
    }
  ]
}
```

**Parâmetros**

| Nome  | Tipo do Parâmetro | Descrição                              | Obrigatório | Tipo de dado              |
| ----- | ----------------- | -------------------------------------- | ----------- | ------------------------- |
| page  | query             | Número da página referente a paginação | Não         | integer                   |
| title | query             | Título do evento que deseja buscar     | Não         | string                    |
| type  | query             | Tipo do evento que deseja buscar       | Não         | enum (online, presential) |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus Tickets - propriedades do convite

| Atributo               | Tipo de dado | Descrição                                                                                 |
| ---------------------- | ------------ | ----------------------------------------------------------------------------------------- |
| `id`                   | string       | Identificador do convite                                                                  |
| `subscribed`           | string       | Data que o participante foi adicionado a lista de presença                                |
| `eduzz_owner_id`       | string       | Id do usuário (no Orbita) do participante que utilizará este ingresso                     |
| `eduzz_first_owner_id` | string       | Código do lote (Também é o mesmo código do conteúdo na Eduzz)                             |
| `name`                 | string       | Nome do participante                                                                      |
| `email`                | string       | Email do participante                                                                     |
| `document`             | string       | CPF do participante que utilizará este ingresso                                           |
| `phone_number`         | string       | Celular do participante que utilizará este ingresso                                       |
| `invoice_id`           | integer      | Número da fatura Eduzz                                                                    |
| `invite_key`           | string       | Código do convite do participante                                                         |
| `eduzz_content_id`     | integer      | Código do conteúdo da eduzz                                                               |
| `status`               | string       | Status do convite do participante (paid, refunded, locked, presence_confirmed, confirmed) |
| `invite_url`           | string       | URL de confirmação de presença.                                                           |
| `ticket_name`          | string       | Nome do ticket do convite                                                                 |
| `ticket_is_paid`       | boolean      | Se o ticket do convite é pago ou gratuíto                                                 |
| `ticket_show_on_page`  | boolean      | Se o ticket é exibido na página de vendas.                                                |
| `unassigned`           | string       | Ingressos sem atribuição, que é necessário confirmar os dados                             |
| `is_gift`              | string       | Se o ticket é presente                                                                    |

## Listar convites de um evento que participei

**Description:** Lista os convites de um evento que participei

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/blinket/v1/my-tickets/event/{event_id}</h6>
	</div>
</div>
```shell
curl GET https://api-eduzz.com/blinket/v1/my-tickets/event/9039jah2-7c1d-4f7a-83e9-e3b9e2f3992j?page=1 \
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
      "id": "90583706-1edb-4cf0-9f38-0fc6ab2c1993",
      "subscribed": "2020-04-16 22:05:46",
      "eduzz_owner_id": 35821795,
      "eduzz_first_owner_id": 35821795,
      "name": "QA Blinket QA Blinket Oficina Viva Produções Eireli ME Oficina Viva Produções Eireli ME",
      "email": "qa-blinket@eduzz.com",
      "document": "29097666082",
      "phone_number": "15999999999",
      "invoice_id": 7797295,
      "invite_key": "326055-100",
      "eduzz_content_id": 326055,
      "status": "presence_confirmed",
      "invite_url": "https://edz.la/blk-nQABC",
      "ticket_name": "Acesso",
      "ticket_is_paid": false,
      "ticket_show_on_page": true,
      "event_id": "901b0b08-5554-4163-beb0-bde5de5ee564",
      "payment_detail": {
        "invoice_id": 7797295,
        "create_date": "2020-04-16 22:05:44",
        "amount": 0,
        "sale_installments": 0,
        "payment_method_name": "Desconhecido",
        "payment_method_id": 11
      }
    },
    {
      "id": "901ef06e-b552-4f7c-845f-b3ee8e52a0f0",
      "subscribed": "2020-03-19 10:46:12",
      "eduzz_owner_id": 44305830,
      "eduzz_first_owner_id": 35821795,
      "name": "Milton Tawamba",
      "email": "milton.tawamba@eduzz.com",
      "document": "00685462030",
      "phone_number": "54991634780",
      "invoice_id": 7161997,
      "invite_key": "326055-1",
      "eduzz_content_id": 326055,
      "status": "presence_confirmed",
      "invite_url": "https://edz.la/blk-B8lQX",
      "ticket_name": "Acesso",
      "ticket_is_paid": false,
      "ticket_show_on_page": true,
      "event_id": "901b0b08-5554-4163-beb0-bde5de5ee564",
      "payment_detail": {
        "invoice_id": 7161997,
        "create_date": "2020-03-19 10:46:11",
        "amount": 0,
        "sale_installments": 0,
        "payment_method_name": "Desconhecido",
        "payment_method_id": 11
      }
    }
  ]
}
```

**Parâmetros**

| Nome     | Tipo do parâmetro | Descrição                                 | Obrigatório | Tipo de dado |
| -------- | ----------------- | ----------------------------------------- | ----------- | ------------ |
| event_id | path              | Identificador de um evento que participei | Sim         | string       |
| page     | query             | Número da página referente a paginação.   | Não         | integer      |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus tickets - formulário de ajuda

**Description:** Permite ao participante enviar uma mensagem de suporte ao produtor do evento ou a eduzz

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinket/v1/my-tickets/helpsend-mytickets</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/my-tickets/helpsend-mytickets \
    -H "Accept: application/json" \
    -H "Authorization: Bearer my_token" \
    --form 'event_id=8fe8b52c-850c-4d2a-9042-7938237b567a' \
    --form 'message=Teste de mensagem' \
    --form 'subject=Críticas ou sugestões' \
    --form 'subject_opt=producer'
```

> JSON response example:

```json
{
  "success": true
}
```

**Parâmetros**

| Nome        | Tipo do parâmetro | Descrição                                                                                                                                                                   | Obrigatório | Tipo de dado           |
| ----------- | ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------------- |
| event_id    | body              | Identificador do evento                                                                                                                                                     | Sim         | string                 |
| subject_opt | body              | Dúvidas sobre o evento que devem ser direcionadas direto para o produtor, deixe como "producer". Caso se trate de dúvidas referentes ao pagamento e a eduzz, deixe "eduzz". | Sim         | enum (eduzz, producer) |
| subject     | body              | Título/Categoria do problema, sugestões: "Problema com a compra", "Tenho dúvidas sobre o evento", "Críticas ou Sugestões", "Outros"                                         | Sim         | string                 |
| message     | body              | Conteúdo da mensagem.                                                                                                                                                       | Sim         | string, max:1000       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus tickets - Reenvio de tickets

**Description:** Permite ao proprietário do ticket Reenviar o ingresso por email para quem ele transferiu

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinket/v1/my-tickets/send-ticket-again</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/my-tickets/send-ticket-again \
    -H "Accept: application/json" \
    -H "Authorization: Bearer my_token" \
    --form 'email=clienteumjobzz+0805@gmail.com' \
    --form 'event_id=8fe8b52c-850c-4d2a-9042-7938237b567a'
```

> JSON response example:

```json
{
  "success": true
}
```

**Parâmetros**

| Nome     | Tipo do parâmetro | Descrição                                                  | Obrigatório | Tipo de dado |
| -------- | ----------------- | ---------------------------------------------------------- | ----------- | ------------ |
| event_id | body              | Identificador do evento                                    | Sim         | string       |
| email    | body              | Email do usuário que gostaria de enviar novamente o ticket | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus tickets - Confirmar dados do ingresso

**Description:** Permite ao detentor do ticket confirmar os dados do ingresso. No sistema é a ação do botão "Este ticket é meu."

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinket/v1/my-tickets/set-as-mine</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/my-tickets/set-as-mine \
    -H "Accept: application/json" \
    -H "Authorization: Bearer my_token" \
    --form 'id=8e4a5432-1781-4f5a-8d3d-31dd01868aef'
```

> JSON response example:

```json
{
  "success": true,
  "data": {
    "eduzz_owner_id": 60235725,
    "eduzz_content_id": 250242,
    "subscribed": "2019-07-30 12:01:52",
    "document": "30496865021",
    "document_type": "cpf",
    "email": "clienteumjobzz+20122019_2@gmail.com",
    "event_id": "8e2dba65-214c-48a4-99f8-380ba645329c",
    "invoice_id": 4995433,
    "eduzz_first_owner_id": 35821795,
    "id": "8e4a5432-1781-4f5a-8d3d-31dd01868aef",
    "invite_key": "250242-5",
    "name": "Teste User Blinket",
    "phone_number": "11999999999",
    "status": "presence_confirmed"
  }
}
```

**Parâmetros**

| Nome | Tipo do parâmetro | Descrição               | Obrigatório | Tipo de dado |
| ---- | ----------------- | ----------------------- | ----------- | ------------ |
| id   | body              | Identificador do evento | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus tickets - Transferir ticket para outra pessoa

**Description:** Permite ao proprietário do ticket Transferir para outra pessoa

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinket/v1/my-tickets/transfer-ticket</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/my-tickets/transfer-ticket \
    -H "Accept: application/json" \
    -H "Authorization: Bearer my_token" \
    --form 'id=8e4a5432-1781-4f5a-8d3d-31dd01868aef' \
    --form 'document=30496865021' \
    --form 'document_type=cpf' \
    --form 'email=clienteumjobzz+20122019_2@gmail.com' \
    --form 'name=Teste User Blinket' \
    --form 'phone=11999999999'
```

> JSON response example:

```json
{
  "success": true,
  "data": {
    "eduzz_owner_id": 60235725,
    "eduzz_content_id": 250242,
    "subscribed": "2019-07-30 12:01:52",
    "document": "30496865021",
    "document_type": "cpf",
    "email": "clienteumjobzz+20122019_2@gmail.com",
    "event_id": "8e2dba65-214c-48a4-99f8-380ba645329c",
    "invoice_id": 4995433,
    "eduzz_first_owner_id": 35821795,
    "id": "8e4a5432-1781-4f5a-8d3d-31dd01868aef",
    "invite_key": "250242-5",
    "name": "Teste User Blinket",
    "phone_number": "11999999999",
    "status": "presence_confirmed"
  }
}
```

**Parâmetros**

| Nome          | Tipo do parâmetro | Descrição                                                    | Obrigatório | Tipo de dado         |
| ------------- | ----------------- | ------------------------------------------------------------ | ----------- | -------------------- |
| id            | body              | Identificador do evento                                      | Sim         | string               |
| name          | body              | Nome completo da pessoa que receberá o ticket                | Sim         | string, max:100      |
| document      | body              | Documento da pessoa que receberá o ticket. CPF ou passaporte | Sim         | string, max:20       |
| document_type | body              | Tipo do documento da pessoa que receberá o ticket            | Sim         | enum (cpf, passport) |
| phone         | body              | Celular da pessoa que receberá o ticket                      | Sim         | string               |
| email         | body              | E-mail da pessoa que receberá o ticket                       | Sim         | string               |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |
