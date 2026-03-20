# NCA111 - Escolas

> **Versao:** 1.3 | **Ultima atualizacao:** 19/10/2021 | **Autor:** Flavio J. Leamari

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | Escolas |
| **Codigo** | NCA111 |
| **Descricao** | Retorno da relacao de escolas ativa na rede publica, utilizando um ou varios parametros combinados como filtro. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/Escolas` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/Escolas` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** QUERY Parameters

> Pelo menos um dos parametros de entrada abaixo e obrigatorio.

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inNomeEscola | Alfanumerico (72) | Opcional (minimo 5 caracteres) | Nome da escola |
| inBairro | Alfanumerico (40) | Opcional (minimo 5 caracteres) | Bairro do endereco da escola |
| inEndereco | Alfanumerico (100) | Opcional (minimo 5 caracteres) | Endereco da escola |
| inMunicipio | Alfanumerico (60) | Opcional (minimo 5 caracteres) | Municipio da escola |

---

## Exemplo de Request

**Query Parameters:**
```
GET /DadosBasicos/Escolas?inNomeEscola=&inBairro=&inEndereco=&inMunicipio=
```

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outCodEscola | Alfanumerico (4) | Codigo CIE da escola |
| outDescNomeEscola | Alfanumerico (60) | Nome completo da escola |
| outCodDiretoria | Alfanumerico (5) | Codigo identificador da diretoria |
| outDescNomeDiretoria | Alfanumerico (40) | Nome da diretoria de ensino |
| outTipoLogradouro | Alfanumerico (100) | Tipo do logradouro do endereco da escola |
| outDescEndereco | Alfanumerico (100) | Endereco da escola |
| outNumero | Alfanumerico (100) | Numero da escola |
| outDescBairro | Alfanumerico (72) | Bairro do endereco da escola |
| outDescComplemento | Alfanumerico (40) | Complemento do endereco |
| outCodMunicipio | Alfanumerico (4) | Codigo DNE do municipio (codigo identificador padrao dos Correios) |
| outDescMunicipio | Alfanumerico (72) | Nome do municipio |
| outCodRedeEnsino | Alfanumerico (1) | Identificador da rede de ensino |
| outNomeRedeEnsino | Alfanumerico (20) | Nome da rede ensino |
| outLatitude | Alfanumerico (100) | Latitude do endereco da escola |
| outLongitude | Alfanumerico (100) | Longitude do endereco da escola |
| **outUnidades** | Alfanumerico | Grupo de unidades da escola no formato ARRAY [1 : N] |
| outCodUnidade | Alfanumerico (8) | Codigo identificador da unidade |
| outDescNomeUnidade | Alfanumerico (60) | Identificacao da unidade |
| outNumSalas | Alfanumerico (10) | Lista das salas das unidades |
| outTipoSala | Alfanumerico (60) | Tipo de sala |
| outTipoEnsino | Alfanumerico (80) | Tipo de ensino da sala |
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
      "outCodDiretoria": "",
      "outDescNomeDiretoria": "",
      "outTipoLogradouro": "",
      "outDescEndereco": "",
      "outNumero": "",
      "outDescBairro": "",
      "outDescComplemento": "",
      "outCodMunicipio": "",
      "outDescMunicipio": "",
      "outLatitude": "",
      "outLongitude": "",
      "outCodRedeEnsino": "",
      "outNomeRedeEnsino": "",
      "outUnidades": [
        {
          "outCodUnidade": "",
          "outDescNomeUnidade": "",
          "outNumSalas": "",
          "outTipoSala": "",
          "outTipoEnsino": ""
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

- Pelo menos um dos parametros de entrada e obrigatorio.
- Todos os parametros de entrada requerem no minimo 5 caracteres para efetuar a pesquisa.
- Na versao 1.1 foi adicionada a regra de obrigatoriedade de pelo menos um parametro.
- Na versao 1.2 foi incluida a lista outNumSalas.
- Na versao 1.3 foram incluidas as listas outTipoSala e outTipoEnsino.
