# NCA021 - Consulta RA Impressao

> **Versao:** 1.0 | **Ultima atualizacao:** 30/09/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | ConsultaRAImpressao |
| **Codigo** | NCA021 |
| **Descricao** | Retorno do RA de aluno cadastrado no sistema NCA no formato base64 a partir de uma pesquisa pelo nome do aluno, nome da mae, data de nascimento e escola de matricula. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/ConsultaRAImpressao` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/ConsultaRAImpressao` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY ou QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCodEscola | Alfanumerico (7) | Obrigatorio | Codigo CIE da escola da matricula do aluno |
| inNomeAluno | Alfanumerico (100) | Obrigatorio | Nome completo do aluno |
| inNomeMae | Alfanumerico (100) | Obrigatorio | Nome completo da mae do aluno (Filiacao 01) |
| inDataNascimento | Alfanumerico (10) | Obrigatorio | Data de nascimento do aluno (DD/MM/AAAA) |

---

## Exemplo de Request

**Query Parameters:**

```
/Aluno/ConsultaRAImpressao?inCodEscola=&inNomeAluno=&inNomeMae=&inDataNascimento=
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
| outArquivo | Alfanumerico (5000) | Saida Base64 para a geracao do PDF |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outArquivo": "",
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

- Todos os parametros de entrada sao obrigatorios (inCodEscola, inNomeAluno, inNomeMae e inDataNascimento).
- O retorno e um arquivo em formato Base64 (outArquivo) para geracao de PDF com os dados do RA do aluno.
- Diferente do NCA018 (ConsultaRA), este metodo retorna o resultado formatado para impressao e o parametro inCodEscola e obrigatorio.
