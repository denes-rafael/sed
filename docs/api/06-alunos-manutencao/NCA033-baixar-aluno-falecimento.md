# NCA033 - Baixar Aluno por Falecimento

> **Versao:** 1.0 | **Ultima atualizacao:** 23/11/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | BaixarAlunoFalecimento |
| **Codigo** | NCA033 |
| **Descricao** | Esse metodo tem como finalidade a desativacao da ficha de um aluno devido ao seu falecimento. Como consequencia todas as matriculas e inscricoes ativas tambem sao encerradas. |
| **Metodo HTTP** | POST |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/BaixarAlunoFalecimento` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/BaixarAlunoFalecimento` |
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

### Outros parametros

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDataBaixa | Alfanumerico (10) | Obrigatorio | Data da desativacao da ficha do aluno (DD/MM/AAAA) |

---

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inDataBaixa": ""
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

- A baixa por falecimento desativa a ficha do aluno e encerra automaticamente todas as matriculas e inscricoes ativas.
- A data de baixa deve ser informada no formato DD/MM/AAAA.
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
