# Órbita: Financeiro

A API de finanças do Órbita permite visualizar os dados financeiros.

## Composição de transferência

**Description:** Retorna a composição de uma transferência que você efetuou

### HTTP Request

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/transfers/{id:[0-9]+}/composition</h6>
	</div>
</div>

```shell
curl GET https://api-eduzz.com/orbita/v1/transfers/123456/composition \
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta CSV:

```csv
Descrição;Data;Fatura;Nome completo;Primeiro nome;Último nome;Documento;Valor da venda;Valor da taxa;Valor ganho;Ganho como;Data transferencia
Vendas Expressivas;2020-09-11;1234;Nicolas Diogo Bernardes;Nicolas;Bernardes;10426942060;127.59;5.58;122.01;produtor;2020-07-14
Ideal Marketing;2020-09-11;4321;Elza Aline da Luz;Elza;Luz;53502968098;200.00;9.98;51.20;produtor;2020-07-14
Vendas Expressivas;2020-09-11;10896453;Daiane Larissa Maria Freitas;Daiane;Freitas;70024034002;997.00;45.77;95.84;produtor;2020-07-14
Ideal Marketing;2020-09-11;8765;Alana Maitê Amanda Nogueira;Alana;Nogueira;39063032099;200.00;9.98;19.15;produtor;2020-07-14
```

**Parâmetros**

| Nome | Tipo do Parâmetro | Descrição                      | Obrigatório | Tipo de dado |
| ---- | ----------------- | ------------------------------ | ----------- | ------------ |
| id   | path              | Identificador da transferência | Sim         | integer      |

**Respostas**

| Código | Descrição |
| ------ | --------- |
| 200    | Sucesso   |
