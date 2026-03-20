# NCA110 - Escolas CEEJA

> **Versao:** 1.0 | **Ultima atualizacao:** 01/10/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | EscolasCEEJA |
| **Codigo** | NCA110 |
| **Descricao** | Retorno da relacao de escolas do tipo CEEJA no estado de Sao Paulo, pertencentes a rede publica. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/EscolasCEEJA` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/EscolasCEEJA` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

Nao ha parametros de entrada.

---

## Exemplo de Request

```
GET /DadosBasicos/EscolasCEEJA
```

Nao ha parametros de entrada.

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outCEEJA | Alfanumerico | Relacao de escolas do tipo CEEJA no formato ARRAY [1 : N] |
| outCodEscola | Alfanumerico (4) | Codigo CIE da escola |
| outDescNomeEscola | Alfanumerico (72) | Nome completo da escola |
| outCodRedeEnsino | Alfanumerico (5) | Identificador da rede de ensino |
| outNomeRedeEnsino | Alfanumerico (20) | Nome da rede de ensino |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outCEEJA": [
    {
      "outCodEscola": "",
      "outDescNomeEscola": "",
      "outCodRedeEnsino": "",
      "outNomeRedeEnsino": ""
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
- CEEJA = Centro Estadual de Educacao de Jovens e Adultos.
- Retorna apenas escolas da rede publica do estado de Sao Paulo.
