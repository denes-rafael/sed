# NCA054 - Gerar Carteirinha Aluno

> Esse metodo tem como finalidade a emissao da carteirinha do aluno no formato base64.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA054 |
| **Metodo HTTP** | POST |
| **URL** | `/Carteirinha/GerarCarteirinha` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

## Parametros de Entrada (Request)

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inNumRA | Alfanumerico (12) | Obrigatorio | Numero do RA do Aluno |
| inDigitoRA | Alfanumerico (02) | Obrigatorio | Digito do RA do Aluno |
| inSiglaUFRA | Alfanumerico (02) | Obrigatorio | UF do RA do Aluno |
| inDataNascimento | Alfanumerico (10) | Obrigatorio | Data de nascimento do Aluno (DD/MM/AAAA) |

## Exemplo de Request

```json
{
  "inNumRA": "string",
  "inDigitoRA": "string",
  "inSiglaUFRA": "string",
  "inDataNascimento": "string"
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| OutNChamada | Alfanumerico (02) | N. chamada do aluno |
| outNome | Alfanumerico (60) | Nome do Aluno |
| outPDF | Alfanumerico (10000) | Saida Base64 para a geracao da carteirinha |
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a inscricao seja efetivada |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

## Exemplo de Response

```json
{
  "outNChamada": "",
  "outNome": "",
  "outPDF": "",
  "outSucesso": "",
  "outErro": "",
  "outProcessoID": ""
}
```

## Codigos de Erro

| Codigo | Mensagem | Descricao |
|--------|----------|-----------|
| 200 | OK | Requisicao processada com sucesso: Retorno de dados |
| 200 | Erro de negocio | Requisicao processada com sucesso: Erro de negocio, outErro preenchido |
| 401 | Unauthorized | Requisicao rejeitada: Token invalido ou expirado |
| 500 | Internal Server Error | Erro de infraestrutura: outErro preenchido |

## Observacoes

- O token de acesso e gerado pelo metodo **ValidarUsuario** e tem um tempo de expiracao de **30 minutos**
- O retorno `outPDF` contem a carteirinha em formato **Base64**
- Todos os parametros de entrada sao obrigatorios
- O formato da data de nascimento e DD/MM/AAAA
