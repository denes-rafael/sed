# NCA114 - Unidades por Escola

> **Versao:** 1.1 | **Ultima atualizacao:** 07/10/2021 | **Autor:** Flavio J. Leamari

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | UnidadesPorEscola |
| **Codigo** | NCA114 |
| **Descricao** | Retornar as unidades ativas de uma escola, independente da rede de ensino. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/UnidadesPorEscola` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/UnidadesPorEscola` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCodEscola | Alfanumerico (7) | Sim | Codigo identificador da escola (Codigo CIE) |

---

## Exemplo de Request

**Query Parameters:**
```
GET /DadosBasicos/UnidadesPorEscola?inCodEscola=
```

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outUnidade | Alfanumerico | Grupo de unidades no formato ARRAY [1 : N] |
| outCodUnidade | Alfanumerico (8) | Codigo da unidade escolar |
| outDescUnidade | Alfanumerico (200) | Nome da unidade escolar |
| outNrDependencia | Alfanumerico (10) | Nr das dependencias da unidade (Lista/array) |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outUnidade": [
    {
      "outCodUnidade": "",
      "outDescUnidade": "",
      "outNrDependencia": []
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

- Retorna unidades ativas independente da rede de ensino.
- Na versao 1.1 foi incluida a lista outNrDependencia.
