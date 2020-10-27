# Blinket: Meus Ingressos

## Meus Ingressos

Permite visualizar seus ingressos de eventos que você adquiriu ou ganhou de presente.

### Propriedades do evento

| Atributo             | Tipo de dado       | Descrição                                            |
| -------------------- | ------------------ | ---------------------------------------------------- |
| `id`                 | string             | Código UUID do evento                                |
| `type`               | string             | Tipo do evento (online, presential)                  |
| `title`              | string             | Título do evento                                     |
| `Descrição`          | string             | Descrição do evento                                  |
| `start_date`         | string - date-time | Data de início do evento (formato: UTC)              |
| `end_date`           | string - date-time | Data de fim do evento (formato: UTC)                 |
| `sale_url`           | string             | URL da página de vendas do evento                    |
| `event_img_url`      | string             | URL da imagem do evento                              |
| `stream_url`         | string             | URL de transmissão do evento (Somente evento Online) |
| `address.place`      | string             | Local onde será realizado o evento                   |
| `address.country`    | string             | País onde será realizado o evento                    |
| `address.state`      | string             | Estado onde será realizado o evento                  |
| `address.city`       | string             | Cidade onde será realizado o evento                  |
| `address.district`   | string             | Bairro onde será realizado o evento                  |
| `address.street`     | string             | Rua onde será realizado o evento                     |
| `address.complement` | string             | Complemento onde será realizado o evento             |
| `address.number`     | string             | Número onde será realizado o evento                  |
| `address.zip`        | string             | CEP onde será realizado o evento                     |
| `address.reference`  | string             | Referência onde será realizado o evento              |

### Propriedades do Ingresso

| Atributo               | Tipo de dado | Descrição                                                                                  |
| ---------------------- | ------------ | ------------------------------------------------------------------------------------------ |
| `id`                   | string       | Código UUID do ingresso                                                                    |
| `subscribed`           | string       | Data que este ingresso recebeu a primeira atribuição                                       |
| `eduzz_owner_id`       | string       | Id Orbita de usuário do detentor deste ingresso                                            |
| `eduzz_first_owner_id` | string       | ID Orbita de usuário do proprietário original deste ingresso                               |
| `name`                 | string       | Nome do participante que detém a posse deste ingresso                                      |
| `email`                | string       | Email do participante que detém a posse deste ingresso                                     |
| `document`             | string       | CPF do participante (sem pontos) detentor do ticket, ou passaporte caso estrangeiro        |
| `phone_number`         | string       | Número de Celular do participante que utilizará este ingresso                              |
| `invoice_id`           | integer      | Número da fatura na Eduzz                                                                  |
| `invite_key`           | string       | Identificador numérico do ingresso                                                         |
| `eduzz_content_id`     | integer      | Código do conteúdo da eduzz                                                                |
| `status`               | string       | Status do ingresso do participante (paid, refunded, locked, presence_confirmed, confirmed) |
| `invite_url`           | string       | URL para realização do check-in na portaria (resultado da leitura do QR Code)              |
| `ticket_name`          | string       | Nome do Ticket deste ingresso                                                              |
| `ticket_is_paid`       | boolean      | Se o ticket deste ingresso é pago ou gratuíto                                              |
| `ticket_show_on_page`  | boolean      | Se o ticket deste ingresso é exibido na página de vendas.                                  |
| `unassigned`           | string       | Ingressos sem atribuição, que é necessário confirmar os dados                              |
| `is_gift`              | string       | Se o ticket é presente                                                                     |

## Meus Ingressos: Listar eventos que participei

**Descrição:** Lista os eventos dos ingressos que você possua ou ganhou

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
      "Descrição": "O mundo est&aacute; cada vez mais digitalizado. Com mais de 1 bilh&atilde;o de usu&aacute;rios, a m&iacute;dia digital est&aacute; criando um impacto significativo em nossas vidas diariamente. \n\nPensando nisso, n&oacute;s criamos um ambiente totalmente controlado para que voc&ecirc; fique totalmente imerso durante 2 dias com os melhores especialistas em marketing digital e ao fim dessa jornada voc&ecirc; seja capaz de trabalhar totalmente focado no markting digital. ",
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
      "Descrição": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus quis lorem nec ante tincidunt porttitor. Nulla et condimentum nunc. Sed vitae magna orci. Quisque gravida leo id nisi commodo vestibulum. Vivamus id ligula eget risus blandit vestibulum non nec metus. Maecenas condimentum a justo eget accumsan. Nulla in pretium tortor.",
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
|        |

## Meus Ingressos: Listar ingressos de um evento

**Descrição:** Lista os ingressos que possuo de um determinado evento

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

| Nome     | Tipo do parâmetro | Descrição                               | Obrigatório | Tipo de dado |
| -------- | ----------------- | --------------------------------------- | ----------- | ------------ |
| event_id | path              | Código UUID do evento                   | Sim         | string       |
| page     | query             | Número da página referente a paginação. | Não         | integer      |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus Ingressos: Formulário de ajuda

**Descrição:** Permite ao participante enviar uma mensagem de suporte ao produtor do evento ou a eduzz

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
| event_id    | body              | Código UUID do evento                                                                                                                                                       | Sim         | string                 |
| subject_opt | body              | Dúvidas sobre o evento que devem ser direcionadas direto para o produtor, deixe como "producer". Caso se trate de dúvidas referentes ao pagamento e a eduzz, deixe "eduzz". | Sim         | enum (eduzz, producer) |
| subject     | body              | Título/Categoria do problema, sugestões: "Problema com a compra", "Tenho dúvidas sobre o evento", "Críticas ou Sugestões", "Outros"                                         | Sim         | string                 |
| message     | body              | Conteúdo da mensagem.                                                                                                                                                       | Sim         | string, max:1000       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus Ingressos: Reenviar ingresso

**Descrição:** Permite ao proprietário do ticket Reenviar o ingresso por email para quem ele transferiu

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
| event_id | body              | Código UUID do evento                                      | Sim         | string       |
| email    | body              | Email do usuário que gostaria de enviar novamente o ticket | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus Ingressos: Confirmar dados do ingresso

**Descrição:** Permite ao detentor do ingresso confirmar seus dados pessoais que serão atribuídos ao ingresso. No sistema é a ação do botão "Este ticket é meu."

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
    --form 'id={Código UUID do ingresso}'
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
| id   | body              | Código UUID do ingresso | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus Ingressos: Transferir ingresso para outra pessoa

**Descrição:** Permite ao proprietário do ticket transferir sua posse deste ingresso para outra pessoa

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

| Nome          | Tipo do parâmetro | Descrição                                                         | Obrigatório | Tipo de dado         |
| ------------- | ----------------- | ----------------------------------------------------------------- | ----------- | -------------------- |
| id            | body              | Código UUID do ingresso                                           | Sim         | string               |
| name          | body              | Nome completo da pessoa que receberá o ticket                     | Sim         | string, max:100      |
| document      | body              | Nº do CPF da pessoa (sem pontos), ou passaporte caso estrangeiro. | Sim         | string, max: 20      |
| document_type | body              | Tipo do documento da pessoa que receberá o ticket                 | Sim         | enum (cpf, passport) |
| phone         | body              | Celular da pessoa que receberá o ticket                           | Sim         | string               |
| email         | body              | E-mail da pessoa que receberá o ticket                            | Sim         | string               |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus Ingressos: Transferir via link: Geração de Link

**Descrição:** Permite ao proprietário do ingresso transferir a posse deste para outra pessoa, gerando um link único

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinket/v1/my-tickets/create_transfer_link</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/my-tickets/create_transfer_link \
    -H "Accept: application/json" \
    -H "Authorization: Bearer my_token" \
    --form 'id={código uuid do ingresso}' \
```

> JSON response example:

```json
{
  "success": true,
  "data": {
    "link": "https://evento.blinket.com.br/transfer/{token_gerado_aqui}"
  }
}
```

**Parâmetros**

| Nome | Tipo do parâmetro | Descrição               | Obrigatório | Tipo de dado |
| ---- | ----------------- | ----------------------- | ----------- | ------------ |
| id   | body              | Código UUID do ingresso | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus Ingressos: Transferir via link: Remover link gerado

**Descrição:** Permite ao proprietário do ingresso apagar um link de transferência que ele gerou anteriormente

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">DELETE</i>
		<h6>/blinket/v1/my-tickets/delete_links/{invite_key}</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/my-tickets/delete_links/{invite_key do ingresso} \
    -H "Accept: application/json" \
    -H "Authorization: Bearer my_token" \
```

> JSON response example:

```json
{
  "success": true
}
```

**Parâmetros**

| Nome       | Tipo do parâmetro | Descrição              | Obrigatório | Tipo de dado |
| ---------- | ----------------- | ---------------------- | ----------- | ------------ |
| invite_key | path              | invite_key do ingresso | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus Ingressos: Transferir via link: Presenteado confirma os dados

**Descrição:** Participante presenteado confirma seus dados do ingresso que recebeu via link

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinket/v1/public/my-tickets/edit_by_link/{token}</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/public/my-tickets/edit_by_link/81c2f71536ac3168a423f2721d81576f \
    --form 'name=José da Silva Teste' \
    --form 'document=69860481067' \
    --form 'document_type=cpf' \
    --form 'phone=11999999999' \
    --form 'email=usuarioteste@gmail.com' \

````

> JSON response example:

```json
{
  "success": true
}
````

**Parâmetros**

| Nome          | Tipo do parâmetro | Descrição                                                               | Obrigatório | Tipo de dado        |
| ------------- | ----------------- | ----------------------------------------------------------------------- | ----------- | ------------------- |
| token         | path              | Token obtido do link gerado                                             | Sim         | string              |
| name          | body              | Nome completo da pessoa que recebeu o ingresso de presente via link     | Sim         | string              |
| document      | body              | Nº do CPF do participante (sem pontos), ou passaporte caso estrangeiro. | Sim         | string              |
| document_type | body              | Tipo do documento.                                                      | Sim         | enum(cpf, passport) |
| phone         | body              | Número de celular do participante                                       | Sim         | string              |
| email         | body              | E-mail do participante.                                                 | Sim         | string              |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Meus Ingressos: Transferir via link: Validar link

**Descrição:** Deve ser chamado assim que o presenteado acessa o link de presente gerado. Utilizado para validar se o token do link é válido e não está expirado. Caso seja válido, permitir ao presenteado confirmar seus dados enviando-os ao endpoint edit_by_link.

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/blinket/v1/public/my-tickets/validate_transfer_link/{token}</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/public/my-tickets/validate_transfer_link/81c2f71536ac3168a423f2721d81576f \
    -H "Accept: application/json" \
    -H "Authorization: Bearer my_token" \
````

> JSON response example:

```json
{
  "success": true,
  "data": {
    "event_id": "8cbc8fbe-b81e-4240-b93d-b5c1a714624a",
    "title": "Como configurar uma boa página para seu Evento",
    "start_date": "2020-10-09 07:45:00",
    "end_date": "2020-10-17 19:41:00",
    "place": "Shopping Center Norte",
    "type": "presential",
    "event_img_src": "/myeduzz/upload/1b/3u/1a3a1e7a5eff4f6b676513735dcd1333",
    "sale_url": "teste_de_evento_como_configurar_api",
    "ticket_name": "Inscrição - VIP",
    "id": "8dc122e4-01de-447f-8448-e716a9e74a9d",
    "name": "José da Silva",
    "invite_key": "92137-2",
    "status": "paid",
    "eduzz_owner_id": 21321219
  }
}
```

**Parâmetros**

| Nome  | Tipo do parâmetro | Descrição                   | Obrigatório | Tipo de dado |
| ----- | ----------------- | --------------------------- | ----------- | ------------ |
| token | path              | Token obtido do link gerado | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |
