# Nutror: Certificados do aluno #

API de listagem de certificados do aluno.

## Propriedades da listagem ##

| Atributo     | Tipo de dado | Descrição                         |
|--------------|--------------|-----------------------------------|
| url          | string       | Link do certificado para download |
| course_image | string       | Link da imagem do curso           |
| title        | string       | Título do curso                   |

## Listar certificados do aluno

**Description:** Lista de certificados

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/nutror/v1/certificates</h6>
	</div>
</div>

```shell
curl GET https://example.com/nutror/v1/certificates?page=1&items_per_page=1
    -H "Accept: application/json"
    -H "Authorization: Bearer my_token"
```

> Exemplo de resposta JSON:

```json
{
  "pages": 1,
  "items_per_page": 1,
  "page": 1,
  "total_items": 1,
  "items": [
    {
      "url": "https://cdn.nutror.com/assets/img/logo.png",
      "course_image": "https://cdn.nutror.com/assets/img/logo.png",
      "title": "Curso"
    }
  ]
}
```

**Parâmetros**

| Nome           | Tipo do Parâmetro | Descrição                              | Obrigatório | Tipo de dado |
|----------------|-------------------|----------------------------------------|-------------|--------------|
| page           | query             | Número da página referente a paginação | Não         | integer      |
| items_per_page | query             | Items por página                       | Não         | integer      |

**Respostas**

| Código | Descrição |
|--------|-----------|
| 200    | Sucesso   |
