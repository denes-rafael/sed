# NCA123 - Consultar Atividade Complementar

> Efetuar consulta das atividades complementares de uma escola/ano letivo, seguindo as regras do Sistema Secretaria Digital (SED).

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA123 |
| **Método HTTP** | GET |
| **URL** | `TipoEnsino/ConsultaTipoEnsinoAtividadeComplementar` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: BearerToken |

## Parâmetros de Entrada (Request)

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inAnoLetivo | Alfanumérico (4) | Sim | Ano Letivo |
| inCodEscola | Alfanumérico (7) | Sim | Código CIE da escola |
| inCodUnidade | Alfanumérico (8) | Condicional | Código da unidade. Torna-se obrigatório quando a escola tem mais de uma unidade |
| inMunicipio | Alfanumérico (50) | Não | Nome do Município |
| inCodQuadroResumo | Alfanumérico (8) | Não | Código do quadro resumo |

## Exemplo de Request

```
GET https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/TipoEnsino/ConsultaTipoEnsinoAtividadeComplementar?inAnoLetivo={inAnoLetivo}&inCodEscola={inCodEscola}&inCodUnidade={inCodUnidade}&inMunicipio={inMunicipio}&inCodQuadroResumo={inCodQuadroResumo}
```

## Parâmetros de Saída (Response)

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outSucesso | Alfanumérico | Retorno de sucesso da requisição |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outRequestID | Alfanumérico | Código identificador da requisição processada |
| AtividadesComplementar | Lista | Descrição das atividades complementares da Escola |
| AtividadesComplementar.outCodigoAtividadeComplementar | Numérico | Código atividade complementar |
| AtividadesComplementar.outNomeAtividadeComplementar | Alfanumérico (50) | Nome Atividade Complementar |
| AtividadesComplementar.outCodigoTipoEnsino | Numérico | Código tipo de ensino |
| AtividadesComplementar.outNomeTipoEnsino | Alfanumérico (50) | Nome Tipo Ensino |

## Exemplo de Response

```json
{
  "outSucesso": "string",
  "outErro": "string",
  "outRequestID": "string",
  "AtividadesComplementar": [
    {
      "outCodigoAtividadeComplementar": 0,
      "outNomeAtividadeComplementar": "string",
      "outCodigoTipoEnsino": 0,
      "outNomeTipoEnsino": "string"
    }
  ]
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
- Tipo de dado: ConsultaTipoEnsinoAtividadeComplementar
- O parâmetro inCodUnidade torna-se obrigatório quando a escola tem mais de uma unidade.
