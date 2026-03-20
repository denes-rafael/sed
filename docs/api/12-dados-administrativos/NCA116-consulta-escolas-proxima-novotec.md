# NCA116 - Consulta Escolas Proxima NovoTec

> **Versao:** 1.0 | **Ultima atualizacao:** 28/10/2020 | **Autor:** Flavio Leamari

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | ConsultaEscolasProximaNovoTec |
| **Codigo** | NCA116 |
| **Descricao** | Retorno das escolas/unidades proximas NovoTec no sistema NCA a partir de uma pesquisa por latitude, longitude e codigo DNE do municipio. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/ConsultaEscolasProximaNovoTec` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/ConsultaEscolasProximaNovoTec` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inLatitude | Alfanumerico (17) | Sim | Latitude do endereco residencial do aluno |
| inLongitude | Alfanumerico (17) | Sim | Longitude do endereco residencial do aluno |
| inCD_DNE | Numerico (4) | Sim | Codigo DNE do municipio |

---

## Exemplo de Request

**Query Parameters:**
```
GET /DadosBasicos/ConsultaEscolasProximaNovoTec?inLatitude=&inLongitude=&inCD_DNE=
```

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outEscolas | Alfanumerico | Grupo de dados escolas NovoTec no formato ARRAY [1 : N] |
| outCodEscola | Numerico (7) | Codigo da Escola NovoTec |
| outCodUnidade | Numerico (8) | Codigo da Unidade NovoTec |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outEscolas": [
    {
      "outCodEscola": "",
      "outCodUnidade": ""
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

- A busca e baseada nas coordenadas geograficas (latitude/longitude) e no codigo DNE do municipio.
- Retorna escolas/unidades proximas cadastradas no programa NovoTec.
