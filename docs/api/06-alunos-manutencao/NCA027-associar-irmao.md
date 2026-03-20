# NCA027 - Associar Irmao

> **Versao:** 1.0 | **Ultima atualizacao:** 11/11/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | AssociarIrmao |
| **Codigo** | NCA027 |
| **Descricao** | Esse metodo tem como finalidade a associacao de irmaos, gemeos ou nao, a ficha de um determinado aluno atendendo as regras vigentes no sistema Cadastro de Alunos. |
| **Metodo HTTP** | POST |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/AssociarIrmao` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/AssociarIrmao` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY

### Grupo inAluno (identificador do aluno)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inAluno | Alfanumerico | Obrigatorio | Grupo de dados identificador do aluno |
| inNumRA | Alfanumerico (12) | Obrigatorio | Numero do RA |
| inDigitoRA | Alfanumerico (2) | Opcional | Digito do RA |
| inSiglaUFRA | Alfanumerico (2) | Obrigatorio | UF do RA |

### Grupo inIrmao (identificador do irmao)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inIrmao | Alfanumerico | Obrigatorio | Grupo de dados identificador do irmao |
| inNumRA | Alfanumerico (12) | Obrigatorio | Numero do RA do Irmao |
| inDigitoRA | Alfanumerico (2) | Opcional | Digito do RA do Irmao |
| inSiglaUFRA | Alfanumerico (2) | Obrigatorio | UF do RA do Irmao |

### Outros parametros

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inGemeo | Alfanumerico (1) | Opcional | Identifica se o irmao e gemeo: 0 - Irmao Nao Gemeo (ou vazio ou parametro ausente), 1 - Irmao Gemeo |

---

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inIrmao": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inGemeo": ""
}
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a inscricao seja efetivada |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outSucesso": "",
    "outErro": "",
    "outProcessoID": ""
}
```

---

## Codigos de Erro

| Status | Descricao |
|---|---|
| 200 | Requisicao processada com sucesso: Retorno de dados |
| 200 | Requisicao processada com sucesso: Erro de negocio, outErro preenchido |
| 401 | Requisicao rejeitada: Token invalido ou expirado |
| 500 | Erro de infraestrutura: outErro preenchido |

---

## Observacoes

- A associacao de irmaos pode ser de irmaos gemeos ou nao gemeos.
- O parametro inGemeo com valor "1" indica que o irmao e gemeo; valor "0", vazio ou ausente indica irmao nao gemeo.
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
