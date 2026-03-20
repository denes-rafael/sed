# NCA052 - Excluir Responsavel pelo Aluno

> Esse metodo tem como finalidade excluir os dados do responsavel pelo aluno cadastrado no sistema NCA a partir de uma pesquisa pelo do CPF do responsavel e RG/UF, CPF ou RA/DG/UF do Aluno.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA052 |
| **Metodo HTTP** | POST |
| **URL** | `/Aluno/ExcluirResponsavelAluno` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

## Parametros de Entrada (Request)

Os parametros devem ser enviados via **BODY Parameters** (um dos grupos abaixo).

### Grupo: inResponsavel

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| InResponsavel | Alfanumerico | N/A | Dados do responsavel |
| inCPF | Alfanumerico (11) | Opcional. Obrigatorio quando houver mais de um responsavel | CPF do responsavel |

### Grupo: InDocumentosAluno

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| InDocumentosAluno | Alfanumerico | N/A | Grupo de documentos do aluno |
| inNRRG | Alfanumerico (15) | Opcional | RG do Aluno |
| inUFRG | Alfanumerico (02) | Opcional. Obrigatorio quando inNRRG informado | UF do RG do Aluno |
| inCPF | Alfanumerico (11) | Opcional | CPF do Aluno |

### Grupo: inAluno

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inAluno | Alfanumerico | N/A | Grupo de dados do aluno |
| inNumRA | Alfanumerico (12) | Opcional | RA do Aluno |
| inDigitoRa | Alfanumerico (01) | Opcional. Obrigatorio quando inNumRA informado | Digito do RA do aluno |
| inSiglaUFRa | Alfanumerico (02) | Opcional. Obrigatorio quando inRA informado | UF do RA do Aluno |

## Exemplo de Request

```json
{
  "inResponsavel": {
    "inCPF": "string"
  },
  "inAluno": {
    "inNumRA": "string",
    "inDigitoRA": "string",
    "inSiglaUFRA": "string"
  },
  "inDocumentosAluno": {
    "inCPF": "string",
    "inNRRG": "string",
    "inUFRG": "string"
  }
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outSucesso | Alfanumerico (1000) | Retorno de sucesso da execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

## Exemplo de Response

```json
{
  "outSucesso": "string",
  "outErro": "string",
  "outProcessoID": "string"
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
- A exclusao requer o CPF do responsavel (obrigatorio quando houver mais de um responsavel) e a identificacao do aluno via RG/UF, CPF ou RA/DG/UF
- Os parametros devem ser enviados via BODY
