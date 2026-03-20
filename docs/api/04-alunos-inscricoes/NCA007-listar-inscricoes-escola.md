# NCA007 - Listar Inscricoes por Escola

> Esse metodo tem como finalidade extrair e retornar ao solicitante todas as inscricoes de um determinado tipo, cadastradas no sistema NCA em um determinado ano letivo, em uma determinada escola publica, independentemente de sua situacao.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA007 |
| **Metodo HTTP** | GET |
| **URL** | `/Inscricao/ListarInscricoesEscola` |
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
| inCodEscola | Alfanumerico (7) | Sim | Codigo da escola publica que sera pesquisada |
| inTipoInscricao | Alfanumerico (1) | Sim | Identificador do tipo da inscricao (fase): 0 - Inscricao de Alunos por Transferencia, 1 - Definicao de Alunos para o 1o Ano do Ensino Fundamental, 2 - Definicao de Alunos para o 6o Ano do Ensino Fundamental, 4 - Inscricao de Aluno Fora da Rede Publica (Ensino Fundamental), 6 - Definicao de Alunos para o Ensino Medio, 7 - Inscricao de Aluno Fora da Rede Publica (Ensino Medio), 8 - Inscricao de Alunos por Deslocamento, 9 - Inscricao por Intencao de Transferencia |

## Exemplo de Request

**Query Parameters:**
```
/Inscricao/ListarInscricoesEscola?inAnoLetivo=&inCodEscola=&inTipoInscricao=
```

**Body:**
```json
{
  "inAnoLetivo": "",
  "inCodEscola": "",
  "inTipoInscricao": ""
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outInscricoes | Alfanumerico (Array) | Grupo de inscricoes efetuadas na escola no formato ARRAY [1 : N] |
| outInscricoes[].outAlunos | Alfanumerico (Array) | Grupo com os dados do RA do aluno inscrito na escola formato ARRAY [1 : N] |
| outInscricoes[].outAlunos.outNumRA | Alfanumerico (12) | Numero do RA |
| outInscricoes[].outAlunos.outDigitoRA | Alfanumerico (2) | Digito do RA |
| outInscricoes[].outAlunos.outSiglaUFRA | Alfanumerico (2) | UF do RA |
| outInscricoes[].outDataInscricao | Alfanumerico (10) | Data de criacao da inscricao (DD/MM/AAAA) |
| outInscricoes[].outCodTipoEnsino | Alfanumerico (3) | Codigo identificador do tipo de ensino da inscricao |
| outInscricoes[].outCodSerieAno | Alfanumerico (2) | Codigo identificador da serie ou ano da inscricao |
| outInscricoes[].outTipoInscricao | Alfanumerico (1) | Codigo identificador da fase de inscricao no processo da matricula antecipada: 0 - Inscricao por Transferencia, 1 - Definicao de alunos para 1o ano do ensino fundamental, 2 - Definicao de alunos para 6o ano do Ensino Fundamental, 4 - Inscricao de aluno de fora da rede publica para o Ensino Fundamental, 6 - Definicao de alunos para 1a serie do Ensino Medio, 7 - Inscricao de aluno de fora da rede publica para o Ensino Medio, 8 - Inscricao por Deslocamento, 9 - Intencao de Transferencia |
| outInscricoes[].outDescTipoInscricao | Alfanumerico (50) | Descricao da fase de inscricao |
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
      "outAluno": {
        "outNumRA": "",
        "outDigitoRA": "",
        "outSiglaUFRA": ""
      },
      "outDataInscricao": "",
      "outCodTipoEnsino": "",
      "outCodSerieAno": "",
      "outTipoInscricao": "",
      "outDescTipoInscricao": "",
      "outCodEscolaAlocacao": "",
      "outNomeEscolaAlocacao": "",
      "outRedeEnsinoEscAlocacao": "",
      "outMunicipioEscAlocacao": "",
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
- O campo inTipoInscricao aceita os valores: 0 (Transferencia), 1 (Definicao 1o ano EF), 2 (Definicao 6o ano EF), 4 (Fora da rede publica EF), 6 (Definicao EM), 7 (Fora da rede publica EM), 8 (Deslocamento), 9 (Intencao de Transferencia)
