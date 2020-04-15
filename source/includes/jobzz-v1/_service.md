# Jobzz: Serviço #

A API de serviços que permite gerenciar conteúdos na plataforma.

## Propriedades do serviço ##

| Atributo | Tipo de dado | Descrição
| --------- | ---- | ----------------------------------------------|
`id` | number | Identificador do serviço
`key` | string | Chave do serviço
`user_id` | number | Identificador do prestador do serviço
`work_type` | string | Tipo do serviço (online, presencial)
`moderation` | number | Status da moderação do serviço
`type` | string | Tipo de pagamento do serviço (normal, assinatura)
`signature` | string | Código do contrato de assinatura
`cnt_cod` | number | Código do serviço
`category_id` | number | Identificador da categoria do serviço
`sub_category_id` | number | Identificador da subcategoria do serviço
`group_id` | number | Identificador do grupo de serviços
`title` | string | Título do serviço
`description` | string | Descrição do serviço
`visible` | number | Campo informando se o serviço está visível na vitrine
`active` | number | Campo informando se o serviço está disponível para venda
`value` | number | Valor do serviço
`value_type` | string | Tipo de cobrança
`deadline` | number | Prazo de entrega do serviço
`deadline_type` | string | Tipo do prazo de entrega (meses, anos)
`automatic_start` | number | Configuração para início automático do serviço
`images` | array | Imagens do serviço
`locations` | array | Locais onde seu serviço será prestado caso seja presencial
`certifications` | array | Certificações que o prestador possui
`negotiate` | number | Campo informando se o serviço está aberto à negociações
`value_to_be_discussed` | boolean | Configuração de valor incial aberto a negociação
`created` | string - date-time | Data de criação do serviço
`modified` | string - date-time | Data da última modificação do serviço
`deleted` | string - date-time | Data em que o serviço foi deletado
