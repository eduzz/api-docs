# Blinket: Participantes

Permite ao produtor Listar os participantes de seus eventos

## Participantes: Adicionar participantes: Por arquivo

**Descrição:** Adicionar participantes por arquivo (.csv ou xlsx )

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinket/v1/attendance_list/import_sheet</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/attendance_list/import_sheet \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
  "success": true,
  "data": {
    "status_msg": "Seus participantes estão sendo importados, assim que terminar o processo o avisaremos por e-mail."
  }
}
```

**Parâmetros**

| Nome        | Tipo do parâmetro | Descrição                 | Obrigatório | Tipo de dado |
| ----------- | ----------------- | ------------------------- | ----------- | ------------ |
| event_id    | body              | Código UUID do evento     | Sim         | uuid         |
| file_name   | body              | Nome do arquivo           | Sim         | string       |
| file_upload | body              | Arquivo em formato base64 | Sim         | base64       |
| ticket_id   | body              | Código UUID do ticket     | Sim         | uuid         |
| use_stock   | body              | Consumir estoque?         | Sim         | boolean      |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Participantes: Adicionar participantes: Individualmente

**Descrição:** Adicionar participante individualmente.

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinket/v1/attendance_list/create_manual</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/attendance_list/create_manual \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
  "success": true,
  "data": {
    "id": "91cdb9f1-cc21-43bd-ad40-62a5235eb850",
    "event_id": "91b14933-e6cc-4a68-b30e-a8e1bed132a3",
    "ticket_id": "91b14933-f668-476e-be2e-6029c452c1fd",
    "lot_id": "91b14934-98c3-4dcd-8fba-b34b2938f6d3",
    "invoice_id": null,
    "eduzz_content_id": 622970,
    "invite_key": "622970-98",
    "transaction_key": null,
    "name": "André Soares Ferreira",
    "document": "11111111111",
    "document_type": "cpf",
    "email": "example@eduzz.com",
    "phone_number": "11955555555",
    "status": "presence_confirmed",
    "subscribed": "2020-10-19 14:15:39",
    "modified": "2020-10-19 14:15:39",
    "eduzz_owner_id": 19311203,
    "eduzz_first_owner_id": 19311203,
    "manually_created": 1
  }
}
```

**Parâmetros**

| Nome          | Tipo do parâmetro | Descrição                                                               | Obrigatório | Tipo de dado        |
| ------------- | ----------------- | ----------------------------------------------------------------------- | ----------- | ------------------- |
| document      | body              | Nº do CPF do participante (sem pontos), ou passaporte caso estrangeiro. | Sim         | string              |
| document_type | body              | Tipo do documento.                                                      | Sim         | enum(cpf, passport) |
| email         | body              | E-mail do participante.                                                 | Sim         | string              |
| event_id      | body              | Código UUID do evento.                                                  | Sim         | uuid                |
| name          | body              | Nome do participante                                                    | Sim         | string              |
| phone         | body              | Contato do participante                                                 | Sim         | string              |
| ticket_id     | body              | Código UUID do ticket.                                                  | Sim         | uuid                |
| use_stock     | body              | Consumir estoque?                                                       | Não         | boolean             |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Participantes: Listagem de Participantes

**Descrição:** Permite ao produtor do evento listar todos os participantes de um de seus eventos

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinke/v1/attendance_list/list_grouped</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinke/v1/attendance_list/list_grouped \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
  "success": true,
  "data": [
    {
      "event_id": "91b14933-e6cc-4a68-b321e-a8e1bed132d8",
      "email": "example@eduzz.com",
      "name": "André Ferreira",
      "document": "12345678910",
      "document_type": "cpf",
      "manually_created": 1,
      "phone_number": "74991916456",
      "status": "presence_confirmed",
      "invite_key ": "622987-63",
      "ticket_names": "Ticket Automatizado;",
      "attendance_tags": "[{\"id\":\"manually\",\"title\":\"Adicionado Manualmente\",\"color\":\"blue\",\"invite_key\":\"622987-63 \"}]"
    },
    {
      "event_id": "91b14933-e6cc-4a68-b30e-a8e1bed132d4",
      "email": "example@eduzz.com",
      "name": "Eduarda Stefany Aurora Dias",
      "document": "15422737300",
      "document_type": "cpf",
      "manually_created": 1,
      "phone_number": "12345678910",
      "status": "confirmed",
      "invite_key ": "623572-8 622987-43",
      "ticket_names": "teste;Ticket Automatizado;",
      "attendance_tags": "[{\"id\":\"manually\",\"title\":\"Adicionado Manualmente\",\"color\":\"blue\",\"invite_key\":\"623572-8 622987-43 \"}]"
    }
  ]
}
```

**Parâmetros**

| Nome                 | Tipo do parâmetro | Descrição                                                     | Obrigatório | Tipo de dado |
| -------------------- | ----------------- | ------------------------------------------------------------- | ----------- | ------------ |
| event_id             | body              | Código UUID do evento                                         | Sim         | uuid         |
| page                 | body              | Numero da página                                              | Não         | integer      |
| pagesize             | body              | Nº de items por página                                        | Não         | uuid         |
| search               | body              | Palavra a ser pesquisada                                      | Não         | string       |
| only_first_last_name | body              | Retorna o primeiro e o ultimo nome dos participantes na lista | Não         | boolean      |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Participantes: Alteração de dados do ingresso

**Descrição:** Permite ao produtor alterar os dados de titularidade de um determinado ingresso

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinke/v1/attendance_list/edit_by_invite/{invite_key}</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/attendance_list/edit_by_invite/{invite_key} \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
  "success": true,
  "data": {
    "id": "91c3b17d-b55f-4ead-ac44-6591f3bd2889",
    "event_id": "91b14922-e6cc-4a68-b30e-a8e1bed132g4",
    "ticket_id": "91b14933-f668-476e-be2e-6029c482c1tf",
    "lot_id": "91b14934-18c3-4dcd-5fba-b34b2938f63d",
    "invoice_id": null,
    "eduzz_content_id": 628965,
    "invite_key": "628965-60",
    "transaction_key": null,
    "name": "André Ferreira",
    "document": "12345687910",
    "document_type": "cpf",
    "email": "example@eduzz.com",
    "phone_number": "74991916456",
    "status": "presence_confirmed",
    "subscribed": "2020-10-14 14:33:44",
    "modified": "2020-10-19 15:07:58",
    "eduzz_owner_id": 19311275,
    "eduzz_first_owner_id": 10311803,
    "manually_created": 1
  }
}
```

**Parâmetros**

| Nome          | Tipo do parâmetro | Descrição                                                               | Obrigatório | Tipo de dado        |
| ------------- | ----------------- | ----------------------------------------------------------------------- | ----------- | ------------------- |
| invite_key    | path              | Identificador numérico do ingresso                                      | Sim         | string              |
| document      | body              | Nº do CPF do participante (sem pontos), ou passaporte caso estrangeiro. | Sim         | string              |
| document_type | body              | Tipo do documento.                                                      | Sim         | enum(cpf, passport) |
| email         | body              | E-mail do participante.                                                 | Sim         | string              |
| event_id      | body              | Código UUID do evento.                                                  | Sim         | uuid                |
| name          | body              | Nome do participante                                                    | Sim         | string              |
| phone         | body              | Contato do participante                                                 | Sim         | string              |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Participantes: Checkin de Participantes

**Descrição:** Checki-n de participantes

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinket/v1/attendance_list/checkin_attendances</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/attendance_list/checkin_attendances \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
  "success": true
}
```

**Parâmetros**

| Nome                     | Tipo do parâmetro | Descrição                          | Obrigatório | Tipo de dado |
| ------------------------ | ----------------- | ---------------------------------- | ----------- | ------------ |
| attendances[].invite_key | body              | Identificador numérico do ingresso | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Participantes: Reenviar Ingresso

**Descrição:** Permite ao produtor reenviar o e-mail com os dados do ingresso para o detentor deste

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/blinket/v1/attendance_list/send_ticket_again</h6>
	</div>
</div>
```shell
curl POST https://api-eduzz.com/blinket/v1/attendance_list/send_ticket_again \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
    --form 'email=joao@gmail.com' \
    --form 'event_id=91b14922-e6cc-4a68-b30e-a8e1bed132g4'
```

> JSON response example:

```json
{
  "success": true
}
```

**Parâmetros**

| Nome     | Tipo do parâmetro | Descrição               | Obrigatório | Tipo de dado |
| -------- | ----------------- | ----------------------- | ----------- | ------------ |
| event_id | body              | Código UUID do evento.  | Sim         | string       |
| email    | body              | E-mail do participante. | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |

## Participantes: Detalhes de um ingresso

**Descrição:** Permite ao produtor listar os detalhes de um ingresso. Estes dados são exibidos no momento que o produtor clica em um dos itens da lista de participantes a fim de exibir os detalhes.

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/blinket/v1/attendance_list/attendance_detail_by_event/{event_id}/{eduzz_owner_id}</h6>
	</div>
</div>
```shell
curl GET https://api-eduzz.com/blinket/v1/attendance_list/attendance_detail_by_event/{event_id}/{eduzz_owner_id}  \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> JSON response example:

```json
{
  "success": true
}
```

**Parâmetros**

| Nome           | Tipo do parâmetro | Descrição                                       | Obrigatório | Tipo de dado |
| -------------- | ----------------- | ----------------------------------------------- | ----------- | ------------ |
| event_id       | param             | Código UUID do evento.                          | Sim         | string       |
| eduzz_owner_id | param             | Id Orbita de usuário do detentor deste ingresso | Sim         | string       |

**Respostas**

| Código | Descrição           |
| ------ | ------------------- |
| 200    | Sucesso             |
| 404    | Dado não encontrado |
