# NCA102 - Municipios por Diretoria

> **Versao:** 1.1 | **Ultima atualizacao:** 30/09/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | MunicipiosPorDiretoria |
| **Codigo** | NCA102 |
| **Descricao** | Retornar uma relacao de municipios contidos em uma determinada diretoria de ensino estadual existente no sistema Cadastro de Alunos (NCA). |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/MunicipiosPorDiretoria` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/MunicipiosPorDiretoria` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY ou QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCodDiretoria | Alfanumerico (5) | Sim | Codigo identificador da diretoria de ensino estadual |

---

## Exemplo de Request

**Query Parameters:**
```
GET /DadosBasicos/MunicipiosPorDiretoria?inCodDiretoria=
```

**Body:**
```json
{
  "inCodDiretoria": ""
}
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
