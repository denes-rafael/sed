# NCA037 - Classificar Numero de Chamada

> Esse metodo tem como finalidade a classificacao dos numeros de chamada de uma ou mais classes utilizando a ordenacao alfabetica e/ou o sexo informado na ficha do aluno.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA037 |
| **Metodo HTTP** | POST |
| **URL** | `/Matricula/ClassificarNrChamada` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

## Endpoints

| Ambiente | URL |
|----------|-----|
| Producao | `https://integracaosed.educacao.sp.gov.br/ncaapi/api` |
| Homologacao | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api` |

## Parametros de Entrada (Request)

Formato: BODY

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inAnoLetivo | Alfanumerico (4) | Sim | Ano letivo da(s) classe(s) |
| inTipoOrdenacao | Alfanumerico (1) | Sim | Formato da ordenacao dos alunos na classe (ver tabela abaixo) |
| inNumClasse | Alfanumerico (9) | Condicional | Numero da classe que sera ordenada. Obrigatorio na ausencia de inEscola. |
| **inEscola** | **Alfanumerico** | **Condicional** | **Grupo de dados relacionados a escola. Obrigatorio na ausencia de inNumClasse.** |
| inCodEscola | Alfanumerico (7) | Nao | Codigo CIE da escola que tera as classes ordenadas |
| inCodTipoEnsino | Alfanumerico (3) | Nao | Tipo de ensino das classes que serao ordenadas |
| inCodSerieAno | Alfanumerico (2) | Nao | Serie / Ano das classes que serao ordenadas |

## Tabela de Tipos de Ordenacao (inTipoOrdenacao)

| Codigo | Descricao |
|--------|-----------|
| 1 | Primeiros alunos do sexo feminino e depois alunos do sexo masculino, ambos ordenados alfabeticamente |
| 2 | Primeiros alunos do sexo masculino e depois alunos do sexo feminino, ambos ordenados alfabeticamente |
| 3 | Ordenacao de alunos alfabeticamente, independente do sexo informado na ficha |
| 4 | Reorganizacao dos numeros de chamadas da(s) classe(s) |

## Exemplo de Request

```json
{
  "inAnoLetivo": "",
  "inTipoOrdenacao": "",
  "inNumClasse": "",
  "inEscola": {
    "inCodEscola": "",
    "inCodTipoEnsino": "",
    "inCodSerieAno": ""
  }
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a classificacao seja efetivada |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

## Exemplo de Response

```json
{
  "outSucesso": "",
  "outErro": "",
  "outProcessoID": ""
}
```

## Codigos de Erro

| Codigo | Mensagem | Descricao |
|--------|----------|-----------|
| 200 | Sucesso | Requisicao processada com sucesso: Retorno de dados |
| 200 | Erro de negocio | Requisicao processada com sucesso: Erro de negocio, outErro preenchido |
| 401 | Token invalido ou expirado | Requisicao rejeitada: Token invalido ou expirado |
| 500 | Erro de infraestrutura | Erro de infraestrutura: outErro preenchido |

## Observacoes

- O token de acesso e gerado pelo metodo ValidarUsuario e tem tempo de expiracao de 30 minutos
- E obrigatorio informar inNumClasse OU inEscola (pelo menos um dos dois)
- Quando inNumClasse e informado, apenas aquela classe sera ordenada
- Quando inEscola e informado, todas as classes da escola (filtradas opcionalmente por tipo de ensino e serie/ano) serao ordenadas
- O campo inCodTipoEnsino foi alterado de Alfanumerico (2) para Alfanumerico (3) na versao 1.1
