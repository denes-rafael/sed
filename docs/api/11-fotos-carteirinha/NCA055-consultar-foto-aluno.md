# NCA055 - Consultar Foto Aluno

> Esse metodo tem como finalidade consultar a foto do aluno no formato base64.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA055 |
| **Metodo HTTP** | GET |
| **URL** | `/Foto/ConsultarFotoAluno` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

## Parametros de Entrada (Request)

Os parametros devem ser enviados via **BODY**.

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inNumRA | Alfanumerico (12) | Obrigatorio | Numero do RA do Aluno |
| inDigitoRA | Alfanumerico (01) | Obrigatorio | Digito do RA do Aluno |
| inSiglaUFRA | Alfanumerico (02) | Obrigatorio | UF do RA do Aluno |
| InDataNascimento | Alfanumerico (10) | Obrigatorio | Nascimento do Aluno (DD/MM/AAAA) |

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
| outNRRA | Alfanumerico (15) | RA do Aluno |
| outDigitoRA | Alfanumerico (02) | Digito do RA do Aluno |
| outUFRA | Alfanumerico (02) | UF do RA do Aluno |
| outImagem | Alfanumerico (10000) | Saida Base64 para consulta da foto da carteirinha |
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a inscricao seja efetivada |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

## Exemplo de Response

```json
{
  "outNChamada": "",
  "outNome": "",
  "outNRRA": "",
  "outDigitoRA": "",
  "outUFRA": "",
  "outImagem": "",
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
- O retorno `outImagem` contem a foto em formato **Base64**
- Todos os parametros de entrada sao obrigatorios
- So aceita BODY por conta de InDataNascimento estar como campo DATE
- O formato da data de nascimento e DD/MM/AAAA
