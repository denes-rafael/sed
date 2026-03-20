# NCA124 - SIAU - Consultar Legislação

> Esse método tem como finalidade consultar a legislação.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA124 |
| **Método HTTP** | GET e POST |
| **URL** | `/ncaApi/api/NovoSistemaSIAU/ConsultarLegislacao` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token |

## Parâmetros de Entrada (Request)

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inAno | Alfanumérico | Não | Ano a ser pesquisado |
| inEmenta | Alfanumérico | Não | Ementa a ser pesquisada |
| inAssunto | Alfanumérico | Não | Assunto a ser pesquisado |
| inId | Alfanumérico | Não | Código da legislação a ser pesquisado |

## Exemplo de Request

```json
{
  "inAno": "string",
  "inEmenta": "string",
  "inAssunto": "string",
  "inId": "string"
}
```

## Parâmetros de Saída (Response)

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outSucesso | Alfanumérico (100) | Parâmetro preenchido caso a inscrição seja efetivada |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outLegislacao | Alfanumérico | ARRAY [1 : N] |
| outLegislacao.outCodigoAto | Alfanumérico | Código Ato da Legislação |
| outLegislacao.outNumeroAto | Alfanumérico | Número Ato da Legislação |
| outLegislacao.outDataAto | Alfanumérico | Data Ato da Legislação |
| outLegislacao.outTitulo | Alfanumérico | Título da Legislação |
| outLegislacao.outAssunto | Alfanumérico | Assunto da Legislação |
| outLegislacao.outEmenta | Alfanumérico | Ementa da Legislação |
| outLegislacao.outTipo | Alfanumérico | Tipo da Legislação |
| outLegislacao.outAno | Alfanumérico | Ano da Legislação |
| outLegislacao.outAnexarDocumento | Alfanumérico | Documentos Anexos da Legislação |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outSucesso": "string",
  "outErro": "string",
  "outLegislacao": [
    {
      "outCodigoAto": "string",
      "outNumeroAto": "string",
      "outDataAto": "string",
      "outTitulo": "string",
      "outAssunto": "string",
      "outEmenta": "string",
      "outTipo": "string",
      "outAno": "string",
      "outAnexarDocumento": "string"
    }
  ],
  "outProcessoId": "string"
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
- Tipo de dado: ConsultarLegislacao
- Parâmetros de entrada podem ser enviados via BODY ou Query Parameters.
- Suporta tanto GET quanto POST.
