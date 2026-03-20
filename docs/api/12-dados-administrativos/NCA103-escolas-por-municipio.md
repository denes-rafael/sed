# NCA103 - Escolas por Municipio

> **Versao:** 1.1 | **Ultima atualizacao:** 03/10/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | EscolasPorMunicipio |
| **Codigo** | NCA103 |
| **Descricao** | Retornar uma relacao de escolas contidas em um determinado municipio e filtrados pela rede de ensino. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/EscolasPorMunicipio` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/EscolasPorMunicipio` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCodDiretoria | Alfanumerico (5) | Opcional | Codigo identificador da diretoria estadual |
| inCodMunicipio | Alfanumerico (4) | Sim | Codigo DNE do municipio |
| inCodRedeEnsino | Alfanumerico (1) | Sim | Codigo identificador da rede de ensino: 1 - Estadual, 2 - Municipal, 3 - Privada, 4 - Federal, 5 - Estadual Outros (Centro Paula Souza) |

---

## Exemplo de Request

**Query Parameters:**
```
GET /DadosBasicos/EscolasMunicipio?inCodDiretoria=&inCodMunicipio=&inCodRedeEnsino=
```

**Body:**
```json
{
  "inCodDiretoria": "",
  "inCodMunicipio": "",
  "inCodRedeEnsino": ""
}
```

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outEscolas | Alfanumerico | Grupo de escolas no formato ARRAY [1 : N] |
| outCodEscola | Alfanumerico (7) | Codigo CIE da escola |
| outDescNomeEscola | Alfanumerico (60) | Nome completo da escola |
| outUnidades | Alfanumerico | Grupo de unidades da escola no formato ARRAY [1 : N] |
| outCodUnidade | Alfanumerico (8) | Codigo identificador da unidade |
| outDescNomeUnidade | Alfanumerico (60) | Identificacao da unidade |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outEscolas": [
    {
      "outCodEscola": "",
      "outDescNomeEscola": "",
      "outUnidades": [
        {
          "outCodUnidade": "",
          "outDescNomeUnidade": ""
        }
      ]
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

- O parametro inCodDiretoria foi alterado de Obrigatorio para Opcional na versao 1.1.
- Cada escola pode conter multiplas unidades (outUnidades).
- Codigos de rede de ensino: 1 - Estadual, 2 - Municipal, 3 - Privada, 4 - Federal, 5 - Estadual Outros (Centro Paula Souza).
