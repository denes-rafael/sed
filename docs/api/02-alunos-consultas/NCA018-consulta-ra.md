# NCA018 - Consulta RA

> **Versao:** 1.2 | **Ultima atualizacao:** 04/11/2021 | **Autor:** Flavio J. Leamari

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | ConsultaRA |
| **Codigo** | NCA018 |
| **Descricao** | Retorno do RA de aluno cadastrado no sistema NCA a partir de uma pesquisa pelo nome do aluno, nome da mae, data de nascimento e escola de matricula. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/ConsultaRA` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/ConsultaRA` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY ou QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCodEscola | Alfanumerico (7) | Opcional | Codigo CIE da escola da matricula do aluno |
| inNomeAluno | Alfanumerico (100) | Obrigatorio | Nome completo do aluno |
| inNomeMae | Alfanumerico (100) | Obrigatorio | Nome completo da mae do aluno (Filiacao 01) |
| inDataNascimento | Alfanumerico (10) | Obrigatorio | Data de nascimento do aluno (DD/MM/AAAA) |

---

## Exemplo de Request

**Query Parameters:**

```
/Aluno/ConsultaRA?inCodEscola=&inNomeAluno=&inNomeMae=&inDataNascimento=
```

**Body:**

```json
{
    "inCodEscola": "",
    "inNomeAluno": "",
    "inNomeMae": "",
    "inDataNascimento": ""
}
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outAluno | Alfanumerico | Grupo de dados aluno |
| outNumRA | Alfanumerico (12) | Numero do RA |
| outDigitoRA | Alfanumerico (2) | Digito do RA |
| outSiglaUFRA | Alfanumerico (2) | UF do RA |
| outNomeAluno | Alfanumerico (100) | Nome completo do Aluno |
| outNomeMae | Alfanumerico (100) | Nome completo da Mae do Aluno (Filiacao 01) |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outAluno": {
        "outNumRA": "",
        "outDigitoRA": "",
        "outSiglaUFRA": "",
        "outNomeAluno": "",
        "outNomeMae": ""
    },
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

- Os parametros inNomeAluno, inNomeMae e inDataNascimento sao obrigatorios.
- O parametro inCodEscola e opcional (desde a versao 1.2).
- O retorno inclui o RA completo do aluno (numero, digito e UF) junto com o nome do aluno e da mae.
