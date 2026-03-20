# NCA113 - Municipios por UF

> **Versao:** 1.0 | **Ultima atualizacao:** 08/11/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | MunicipiosPorUF |
| **Codigo** | NCA113 |
| **Descricao** | Retornar uma relacao de municipios brasileiros de um determinado estado. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/MunicipiosPorUF` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/MunicipiosPorUF` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inUF | Alfanumerico (5) | Sim | Codigo identificador da unidade da federacao |

---

## Exemplo de Request

**Query Parameters:**
```
GET /DadosBasicos/MunicipiosPorUF?inUF=
```

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outMunicipio | Alfanumerico | Grupo de municipios no formato ARRAY [1 : N] |
| outCodMunicipio | Alfanumerico (4) | Codigo DNE do municipio (codigo identificador padrao dos Correios) |
| outDescMunicipio | Alfanumerico (72) | Nome do municipio |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outMunicipio": [
    {
      "outCodMunicipio": "",
      "outDescMunicipio": ""
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

- O codigo do municipio retornado (outCodMunicipio) e o codigo DNE padrao dos Correios.
