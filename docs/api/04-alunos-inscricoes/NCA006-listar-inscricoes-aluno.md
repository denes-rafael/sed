# NCA006 - Listar Inscricoes por Aluno

> Listar inscricoes de alunos. Retorna a lista de inscricoes de um aluno por ano letivo.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA006 |
| **Metodo HTTP** | GET |
| **URL** | `/Inscricao/ListarInscricoesAluno` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

**Endpoints:**
- **Producao:** `https://integracaosed.educacao.sp.gov.br/ncaapi/api`
- **Homologacao:** `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api`

## Parametros de Entrada (Request)

Formato: **BODY** ou **QUERY Parameters**

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inAnoLetivo | Alfanumerico (4) | Sim | Ano letivo das inscricoes (AAAA) |
| inAluno | Alfanumerico | Sim | Grupo de dados identificador do aluno |
| inAluno.inNumRA | Alfanumerico (12) | Sim | Numero do RA |
| inAluno.inDigitoRA | Alfanumerico (2) | Nao | Digito do RA |
| inAluno.inSiglaUFRA | Alfanumerico (2) | Sim | UF do RA |

## Exemplo de Request

**Query Parameters:**
```
/Inscricao/ListarInscricoesAluno?inNumRA=&inDigitoRA=&inSiglaUFRA=&inAnoLetivo=
```

**Body:**
```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inAnoLetivo": ""
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outInscricoes | Alfanumerico (Array) | Grupo de inscricoes do aluno no formato ARRAY [1 : N] |
| outInscricoes[].outMunicipioEscInscricao | Alfanumerico (40) | Municipio da escola de inscricao |
| outInscricoes[].outRedeEnsinoEscInscricao | Alfanumerico (40) | Rede de ensino da escola de inscricao |
| outInscricoes[].outCodEscolaInscricao | Alfanumerico (7) | Codigo CIE da escola onde a inscricao efetuada ou associada |
| outInscricoes[].outNomeEscolaInscricao | Alfanumerico (60) | Nome abreviado da escola onde a inscricao efetuada ou associada |
| outInscricoes[].outCodTipoEnsino | Alfanumerico (3) | Codigo identificador do tipo de ensino da inscricao |
| outInscricoes[].outCodSerieAno | Alfanumerico (2) | Codigo identificador da serie ou ano da inscricao |
| outInscricoes[].outTipoInscricao | Alfanumerico (1) | Codigo identificador da fase de inscricao no processo da matricula antecipada: 0 - Inscricao por Transferencia, 1 - Definicao de alunos para 1o ano do ensino fundamental, 2 - Definicao de alunos para 6o ano do Ensino Fundamental, 4 - Inscricao de aluno de fora da rede publica para o Ensino Fundamental, 6 - Definicao de alunos para 1a serie do Ensino Medio, 7 - Inscricao de aluno de fora da rede publica para o Ensino Medio, 8 - Inscricao por Deslocamento, 9 - Intencao de Transferencia |
| outInscricoes[].outDescTipoInscricao | Alfanumerico (50) | Descricao da fase de inscricao |
| outInscricoes[].outDataInscricao | Alfanumerico (10) | Data de efetivacao da inscricao (DD/MM/AAAA) |
| outInscricoes[].outMunicipioEscAlocacao | Alfanumerico (40) | Municipio da escola de matricula |
| outInscricoes[].outRedeEnsinoEscAlocacao | Alfanumerico (40) | Rede de ensino da escola de matricula |
| outInscricoes[].outCodEscolaAlocacao | Alfanumerico (7) | Codigo CIE da escola de matricula |
| outInscricoes[].outNomeEscolaAlocacao | Alfanumerico (60) | Nome abreviado da escola de matricula |
| outInscricoes[].outNumClasseAlocacao | Alfanumerico (9) | Numero da classe de matricula (999999999) |
| outInscricoes[].outDataAlocacao | Alfanumerico (10) | Data de efetivacao da inscricao (DD/MM/AAAA) |
| outInscricoes[].outSituacao | Alfanumerico (30) | Descricao da situacao da inscricao |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

## Exemplo de Response

```json
{
  "outErro": "",
  "outProcessoID": "",
  "outInscricoes": [
    {
      "outMunicipioEscInscricao": "",
      "outRedeEnsinoEscInscricao": "",
      "outCodEscolaInscricao": "",
      "outNomeEscolaInscricao": "",
      "outCodTipoEnsino": "",
      "outCodSerieAno": "",
      "outTipoInscricao": "",
      "outDescTipoInscricao": "",
      "outDataInscricao": "",
      "outMunicipioEscAlocacao": "",
      "outRedeEnsinoEscAlocacao": "",
      "outCodEscolaAlocacao": "",
      "outNomeEscolaAlocacao": "",
      "outNumClasseAlocacao": "",
      "outDataAlocacao": "",
      "outSituacao": ""
    }
  ]
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

- Os parametros de entrada podem ser enviados tanto no formato BODY quanto como QUERY Parameters
- O token de acesso e gerado pelo metodo ValidarUsuario e tem um tempo de expiracao de 30 minutos
- O campo outTipoInscricao possui os seguintes valores possiveis: 0 (Transferencia), 1 (Definicao 1o ano EF), 2 (Definicao 6o ano EF), 4 (Fora da rede publica EF), 6 (Definicao 1a serie EM), 7 (Fora da rede publica EM), 8 (Deslocamento), 9 (Intencao de Transferencia)
