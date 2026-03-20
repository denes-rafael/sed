# NCA109 - Municipios SP

> **Versao:** 1.2 | **Ultima atualizacao:** 03/10/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | MunicipiosSP |
| **Codigo** | NCA109 |
| **Descricao** | Retorno da relacao dos municipios do estado de Sao Paulo e a identificacao da diretoria a que eles pertencem. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/MunicipiosSP` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/MunicipiosSP` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

Nao ha parametros de entrada.

---

## Exemplo de Request

```
GET /DadosBasicos/MunicipiosSP
```

Nao ha parametros de entrada.

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outMunicipio | Alfanumerico | Relacao de municipios no formato ARRAY [1 : N] |
| outCodMunicipio | Alfanumerico (4) | Codigo DNE do municipio (codigo identificador padrao dos Correios) |
| outDescMunicipio | Alfanumerico (72) | Nome do municipio |
| ~~outCodDiretoria~~ | ~~Alfanumerico (5)~~ | ~~Codigo da diretoria estadual~~ (removido na v1.2) |
| ~~outDescNomeDiretoria~~ | ~~Alfanumerico (40)~~ | ~~Nome da diretoria estadual~~ (removido na v1.2) |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outMunicipio": [
    {
      "outCodMunicipio": "",
      "outDescMunicipio": "",
      "outCodDiretoria": ""
    }
  ],
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

- Nao ha parametros de entrada para este metodo.
- Na versao 1.1 foi incluido o parametro outDescNomeDiretoria.
- Na versao 1.2 foram removidos os parametros outCodDiretoria e outDescNomeDiretoria.
- O codigo do municipio (outCodMunicipio) e o codigo DNE padrao dos Correios.
