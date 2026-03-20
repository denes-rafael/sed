# NCA125 - SIAU - Consultar Assunto

> Esse método tem como finalidade consultar assunto da legislação.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA125 |
| **Método HTTP** | GET |
| **URL** | `/ncaApi/api/NovoSistemaSIAU/ConsultarAssunto` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token |

## Parâmetros de Entrada (Request)

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| N/A | - | - | Não se aplica |

## Exemplo de Request

```
GET https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/NovoSistemaSIAU/ConsultarAssunto
```

> Não requer parâmetros de entrada.

## Parâmetros de Saída (Response)

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outSucesso | Alfanumérico (100) | Parâmetro preenchido caso a inscrição seja efetivada |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outAssunto | Alfanumérico | ARRAY [1 : N] |
| outAssunto.outCodigo | Alfanumérico | Código do assunto |
| outAssunto.outNome | Alfanumérico | Nome do assunto |
| outAssunto.outStatus | Alfanumérico | Status do assunto |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outErro": "string",
  "outSucesso": "string",
  "outAssunto": [
    {
      "outCodigo": "string",
      "outNome": "string",
      "outStatus": "string"
    }
  ],
  "outProcessoID": "string"
}
```

## Códigos de Erro

| Código | Mensagem | Descrição |
|--------|----------|-----------|
| 200 | OK | Requisição processada com sucesso: Retorno de dados |
| 200 | Erro de negócio | Requisição processada com sucesso: Erro de negócio, outErro preenchido |
| 401 | Unauthorized | Requisição rejeitada: Token inválido ou expirado |
| 500 | Internal Server Error | Erro de infraestrutura: outErro preenchido |

## Observações

- Token de acesso gerado pelo método ValidarUsuario com tempo de expiração de 30 minutos.
- Tipo de dado: ConsultarAssunto
- Este método não requer parâmetros de entrada.
