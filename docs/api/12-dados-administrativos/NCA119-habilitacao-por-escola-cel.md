# NCA119 - Habilitacao por Escola Cel

> **Versao:** 1.0 | **Ultima atualizacao:** 06/11/2020 | **Autor:** Flavio Leamari

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | HabilitacaoPorEscolaCel |
| **Codigo** | NCA119 |
| **Descricao** | Retorno das habilitacoes Cel das escolas no sistema NCA a partir de uma pesquisa por codigo CIE da escola e codigo da unidade. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/HabilitacaoPorEscolaCel` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/HabilitacaoPorEscolaCel` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCodEscola | Alfanumerico (7) | Sim | Codigo CIE da escola |
| inCodUnidade | Alfanumerico (8) | Sim | Codigo da unidade da escola |

---

## Exemplo de Request

**Query Parameters:**
```
GET /DadosBasicos/HabilitacaoPorEscolaCel?inCodEscola=&inCodUnidade=
```

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outHabilitacao | Grupo | Grupo das Habilitacoes no formato ARRAY [1 : N] |
| outCodHabilitacao | Numerico (7) | Codigo da Habilitacao Cel |
| outNomeHabilitacaoQualificacao | Alfanumerico (50) | Descricao da Habilitacao Cel |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outHabilitacao": [
    {
      "outCodHabilitacao": "",
      "outNomeHabilitacaoQualificacao": ""
    }
  ],
  "outErro": "",
  "outProcessoID": ""
}
```

---

## Codigos de Erro

| Codigo | Mensagem | Descricao |
|---|---|---|
| 200 | Sucesso | Requisicao processada com sucesso: Retorno de dados |
| 200 | Erro de negocio | Requisicao processada com sucesso: Erro de negocio, outErro preenchido |
| 401 | Token invalido ou expirado | Requisicao rejeitada: Token invalido ou expirado |
| 500 | Erro de infraestrutura | Erro de infraestrutura: outErro preenchido |

---

## Observacoes

- Retorna as habilitacoes disponiveis no programa Cel (Centro de Estudos de Linguas) para uma determinada escola e unidade.
- A pesquisa e feita pelo codigo CIE da escola e codigo da unidade.
