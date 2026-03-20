# NCA107 - Tipo Ensino

> **Versao:** 1.0 | **Ultima atualizacao:** 26/09/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | TipoEnsino |
| **Codigo** | NCA107 |
| **Descricao** | Retorno da relacao de tipos de ensinos ativos no sistema Cadastro de Alunos. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/TipoEnsino` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/TipoEnsino` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

Nao ha parametros de entrada.

---

## Exemplo de Request

```
GET /DadosBasicos/TipoEnsino
```

Nao ha parametros de entrada.

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outTipoEnsino | Alfanumerico | Relacao de tipos de ensino no formato ARRAY [1 : N] |
| outCodTipoEnsino | Alfanumerico (3) | Codigo identificador do tipo de ensino |
| outDescTipoEnsino | Alfanumerico (10) | Descricao do tipo de Ensino |
| outSerieAno | Alfanumerico | Relacao de series associadas ao tipo de ensino no formato ARRAY [1 : N] |
| outCodSerieAno | Alfanumerico (2) | Codigo identificador da serie/ano |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outTipoEnsino": [
    {
      "outCodTipoEnsino": "",
      "outDescTipoEnsino": "",
      "outSerieAno": [
        {
          "outCodSerieAno": ""
        }
      ]
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
- Cada tipo de ensino possui uma relacao de series/anos associadas (outSerieAno).
