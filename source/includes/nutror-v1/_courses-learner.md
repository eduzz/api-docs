# Nutror: Cursos do aluno #

API de listagem de cursos do aluno.

## Propriedades da listagem ##

| Atributo                                 | Tipo de dado       | Descrição                                                                            |
|------------------------------------------|--------------------|--------------------------------------------------------------------------------------|
| `id`                                     | integer            | Identificador do curso                                                               |
| `title`                                  | string             | Título do curso                                                                      |
| `type`                                   | string             | Tipo do curso. Veja [Tipos de curso](#tipos-de-curso)                                |
| `logo`                                   | string             | Link do logo                                                                         |
| `slug`                                   | string             | Slug                                                                                 |
| `published`                              | boolean            | Se o curso esta publicado                                                            |
| `hash`                                   | string             | Hash do curso                                                                        |
| `release_at`                             | string - date-time | Data de liberação (formato: UTC)                                                     |
| `status`                                 | string             | Estado do aluno no curso. Veja [Estado do aluno no curso](#estado-do-aluno-no-curso) |
| `link`                                   | string             | Link do curso no Nutror                                                              |
| `producer.id`                            | integer            | Identificador do produtor                                                            |
| `producer.name`                          | string             | Nome do produtor                                                                     |
| `producer.avatar`                        | string             | Link da imagem do avatar do produtor                                                 |
| `category.id`                            | integer            | Identificador da categoria                                                           |
| `category.name`                          | string             | Nome da categoria                                                                    |
| `author.id`                              | integer            | Identificador do autor                                                               |
| `author.name`                            | string             | Nome do autor                                                                        |
| `author.avatar`                          | string             | Link da imagem do avatar do autor                                                    |
| `author.description`                     | string             | Descrição do autor                                                                   |
| `customization.header_background_color`  | string             | Cor do cabeçalho                                                                     |
| `customization.image_cover`              | string             | Link da imagem do banner de capa                                                     |
| `customization.title_color`              | string             | Cor do título                                                                        |
| `customization.header_link_color`        | string             | Cor dos links do cabeçalho                                                           |
| `customization.avatar`                   | string             | Link da imagem de identificação                                                      |
| `customization.cover_background_color`   | string             | Cor de fundo                                                                         |
| `customization.logo_login`               | string             | Link da imagem do logo para o login                                                  |
| `customization.login_background_image`   | string             | Link da imagem do de fundo para o login                                              |
| `customization.theme`                    | integer            | Tema                                                                                 |
| `customization.layout`                   | boolean            | Se o curso esta usando o layout novo                                                 |
| `customization.description_color`        | string             | Cor da descrição                                                                     |
| `customizations.header_background_color` | string             | Cor do cabeçalho                                                                     |
| `customizations.image_cover`             | string             | Link da imagem do banner de capa                                                     |
| `customizations.title_color`             | string             | Cor do título                                                                        |
| `customizations.header_link_color`       | string             | Cor dos links do cabeçalho                                                           |
| `customizations.avatar`                  | string             | Link da imagem de identificação                                                      |
| `customizations.cover_background_color`  | string             | Cor de fundo                                                                         |
| `customizations.logo_login`              | string             | Link da imagem do logo para o login                                                  |
| `customizations.login_background_image`  | string             | Link da imagem do de fundo para o login                                              |
| `customizations.theme`                   | integer            | Tema                                                                                 |
| `customizations.layout`                  | boolean            | Se o curso esta usando o layout novo                                                 |
| `customizations.description_color`       | string             | Cor da descrição                                                                     |

## Tipos de curso

| Atributo  | Descrição             |
|-----------|-----------------------|
| `course`  | Curso                 |
| `club`    | Portal de recorrência |
| `package` | Pacote                |

## Listar cursos do aluno

**Description:** Lista de cursos

### HTTP Request 
<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">GET</i>
		<h6>/nutror/v1/courses</h6>
	</div>
</div>

```shell
curl GET https://example.com/nutror/v1/courses?page=1&items_per_page=1
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
            "id": 123213,
            "title": "Curso",
            "type": "course",
            "logo": "https://cdn.nutror.com/assets/img/logo.png",
            "slug": "curso",
            "published": true,
            "hash": "gs17692ge6g12",
            "release_at": "2020-05-14T20:18:32Z",
            "status": "learner",
            "link": "https://cursos.nutror.com/curso/gs17692ge6g12/curso",
            "producer": {
                "id": 167123490,
                "name": "Produtor",
                "avatar": "https://cdn.nutror.com/assets/img/logo.png"
            },
            "customization": {
                "header_background_color": null,
                "image_cover": "https://cdn.nutror.com/assets/img/logo.png",
                "title_color": null,
                "header_link_color": null,
                "avatar": "https://cdn.nutror.com/assets/img/logo.png",
                "cover_background_color": null,
                "logo_login": "https://cdn.nutror.com/assets/img/logo.png",
                "login_background_image": "https://cdn.nutror.com/assets/img/logo.png",
                "theme": 1,
                "layout": true,
                "description_color": null
            },
            "customizations": {
                "header_background_color": null,
                "image_cover": "https://cdn.nutror.com/assets/img/logo.png",
                "title_color": null,
                "header_link_color": null,
                "avatar": "https://cdn.nutror.com/assets/img/logo.png",
                "cover_background_color": null,
                "logo_login": "https://cdn.nutror.com/assets/img/logo.png",
                "login_background_image": "https://cdn.nutror.com/assets/img/logo.png",
                "theme": 1,
                "layout": true,
                "description_color": null
            },
            "category": {
                "id": 513123126,
                "name": "Nome da categoria"
            },
            "author": {
                "id": 45453,
                "name": "Nome do autor",
                "avatar": "https://cdn.nutror.com/assets/img/logo.png",
                "description": "Descrição do autor"
            }
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
