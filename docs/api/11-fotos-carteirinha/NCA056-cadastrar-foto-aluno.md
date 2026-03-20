# NCA056 - Cadastrar Foto Aluno

> Esse metodo tem como finalidade cadastrar a foto do aluno no formato base64.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA056 |
| **Metodo HTTP** | POST |
| **URL** | `/Foto/CadastrarFotoAluno` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

## Parametros de Entrada (Request)

Os parametros devem ser enviados via **BODY**.

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inNumRA | Alfanumerico (12) | Obrigatorio | Numero do RA do Aluno |
| inDigitoRA | Alfanumerico (02) | Obrigatorio | Digito do RA do Aluno |
| inSiglaUFRA | Alfanumerico (02) | Obrigatorio | UF do RA do Aluno |
| inDataNascimento | Alfanumerico (10) | Obrigatorio | Formato: DD/MM/AAAA |
| inFotoBase64 | Alfanumerico (10000) | N/A | Foto do Aluno Base64 |

## Exemplo de Request

```json
{
  "inNumRA": "string",
  "inDigitoRA": "string",
  "inSiglaUFRA": "string",
  "inDataNascimento": "string",
  "inFotoBase64": "string"
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| **OutAluno** | **Alfanumerico** | **Lista dados do aluno** |
| outNChamada | Alfanumerico (2) | N. chamada do Aluno |
| outNome | Alfanumerico (60) | Nome do Aluno |
| outNRRA | Alfanumerico (12) | RA do Aluno |
| outDigitoRA | Alfanumerico (1) | Digito do RA do Aluno |
| outUFRA | Alfanumerico (2) | UF do RA do Aluno |
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
- A foto deve ser enviada em formato **Base64** no campo `inFotoBase64`
- O grupo `OutAluno` contem os dados do aluno retornados apos o cadastro da foto
- Todos os parametros de entrada sao obrigatorios (exceto inFotoBase64 que e N/A)
- O formato da data de nascimento e DD/MM/AAAA
