# NCA126 - Consulta Quadro Resumo

> Esse método tem como finalidade consultar o Quadro Resumo.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA126 |
| **Método HTTP** | GET |
| **URL** | `/QuadroResumo/ConsultaQuadroResumo` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token |

## Parâmetros de Entrada (Request)

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inAnoLetivo | Alfanumérico (4) | Sim | Ano letivo da pesquisa |
| inCodEscola | Alfanumérico (7) | Sim | Código da escola que será pesquisada |
| inCodUnidade | Alfanumérico (8) | Condicional | Código da Unidade. Obrigatório caso a escola possua mais de uma unidade |
| inCodTipoEnsino | Alfanumérico (3) | Não | Código do Tipo de Ensino |

## Exemplo de Request

**Query Parameters:**
```
GET /QuadroResumo/ConsultaQuadroResumo?inAnoLetivo=9999&inCodEscola=999999&inCodUnidade=9999&inCodTipoEnsino=999
```

**Body:**
```json
{
  "inAnoLetivo": "",
  "inCodEscola": "",
  "inCodUnidade": "",
  "inCodTipoEnsino": ""
}
```

## Parâmetros de Saída (Response)

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outListaQuadroResumo | Alfanumérico | Grupo de classes no formato ARRAY [1 : N] |
| outListaQuadroResumo.outAnoLetivo | Alfanumérico (4) | Ano letivo |
| outListaQuadroResumo.outCodEscola | Alfanumérico (7) | Código da escola |
| outListaQuadroResumo.outCodUnidade | Alfanumérico (8) | Código da unidade |
| outListaQuadroResumo.outCodTipoEscola | Alfanumérico (10) | Código do tipo de escola |
| outListaQuadroResumo.outCodMunicipioDNE | Alfanumérico (10) | Código do município DNE |
| outListaQuadroResumo.outDescTipoEnsino | Alfanumérico (100) | Descrição do tipo de ensino |
| outListaQuadroResumo.outNRProjetadoSeriada | Alfanumérico (10) | Número projetado seriada |
| outListaQuadroResumo.outNRProjetadoMultisseriada | Alfanumérico (10) | Número projetado multisseriada |
| outListaQuadroResumo.outNRProjetadoSemipresencial | Alfanumérico (10) | Número projetado semipresencial |
| outQuadroResumoSerieResponse | Alfanumérico | Grupo de classes no formato ARRAY [1 : N] |
| outQuadroResumoSerieResponse.outAnoLetivo | Alfanumérico (4) | Ano letivo |
| outQuadroResumoSerieResponse.outCodQuadroResumo | Alfanumérico (19) | Código do quadro resumo |
| outQuadroResumoSerieResponse.outCodSerieTipoEnsino | Alfanumérico (10) | Código série tipo ensino |
| outQuadroResumoSerieResponse.outCodAspectoTurmaClasse | Alfanumérico (10) | Código aspecto turma classe |
| outQuadroResumoSerieResponse.outCodTipoEnsino | Alfanumérico (2) | Código tipo de ensino |
| outQuadroResumoSerieResponse.outDescTipoEnsino | Alfanumérico (100) | Descrição tipo de ensino |
| outQuadroResumoSerieResponse.outNrSerieAno | Alfanumérico (5) | Número série/ano |
| outQuadroResumoSerieResponse.outDescSerieAno | Alfanumérico (30) | Descrição série/ano |
| outQuadroResumoSerieResponse.outNRProjetado | Alfanumérico (5) | Número projetado |
| outQuadroResumoSerieResponse.outNRColetado | Alfanumérico (5) | Número coletado |
| outSucesso | Alfanumérico (100) | Retorno de sucesso |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outListaQuadroResumo": [
    {
      "outAnoLetivo": "string",
      "outCodEscola": 0,
      "outCodUnidade": 0,
      "outCodTipoEscola": 0,
      "outCodMunicipioDNE": 0,
      "outCodTipoEnsino": 0,
      "outDescTipoEnsino": "string",
      "outNRProjetadoSeriada": 0,
      "outNRProjetadoMultisseriada": 0,
      "outNRProjetadoSemipresencial": 0,
      "outQuadroResumoSerieResponse": [
        {
          "outAnoLetivo": "string",
          "outCodQuadroResumo": 0,
          "outCodSerieTipoEnsino": 0,
          "outCodAspectoTurmaClasse": 0,
          "outCodTipoEnsino": 0,
          "outDescTipoEnsino": "string",
          "outNrSerieAno": 0,
          "outDescSerieAno": "string",
          "outNRProjetado": 0,
          "outNRColetado": 0
        }
      ]
    }
  ],
  "outSucesso": "string",
  "outErro": "string",
  "outRequestID": "string"
}
```

## Códigos de Erro

| Código | Mensagem | Descrição |
|--------|----------|-----------|
| 200 | OK | Requisição processada com sucesso: Retorno de dados |
| 200 | Erro de negócio | Requisição processada com sucesso: Erro de negócio, outErro preenchido |
| 401 | Unauthorized | Requisição rejeitada: Token inválido ou expirado |
| 500 | Internal Server Error | Erro de infraestrutura: outErro preenchido |

## Observações

- Token de acesso gerado pelo método ValidarUsuario com tempo de expiração de 30 minutos.
- Tipo de dado: ConsultaQuadroResumo
- Parâmetros de entrada podem ser enviados via BODY ou QUERY Parameters.
- O campo inCodUnidade é obrigatório caso a escola possua mais de uma unidade.
