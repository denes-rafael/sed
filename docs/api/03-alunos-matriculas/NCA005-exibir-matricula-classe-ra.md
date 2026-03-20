# NCA005 - Exibir Matricula na Classe por RA

> Esse metodo tem como finalidade extrair e retornar ao solicitante dados sobre uma determinada matricula cadastrada no sistema NCA, para isso sera necessario informar o RA do aluno e a classe da matricula.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA005 |
| **Metodo HTTP** | GET |
| **URL** | `/Matricula/ExibirMatriculaClasseRA` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

## Endpoints

| Ambiente | URL |
|----------|-----|
| Producao | `https://integracaosed.educacao.sp.gov.br/ncaapi/api` |
| Homologacao | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api` |

## Parametros de Entrada (Request)

Formato: BODY ou QUERY Parameters

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inAluno | Alfanumerico | Sim | Grupo de dados identificador do aluno |
| inNumRA | Alfanumerico (12) | Sim | Numero do RA |
| inDigitoRA | Alfanumerico (2) | Nao | Digito do RA |
| inSiglaUFRA | Alfanumerico (2) | Sim | UF do RA |
| inNumClasse | Alfanumerico (9) | Sim | Numero da classe (turma) da matricula |
| inSituacao | Alfanumerico (3) | Sim | Identificador da situacao da matricula do aluno (ver tabela abaixo) |
| inDataInicioMatricula | Alfanumerico (10) | Nao | Data de inicio da matricula do aluno na classe (DD/MM/AAAA) |

## Exemplo de Request

**Query Parameters:**

```
/Matricula/ExibirMatriculaClasseRA?inNumRA=&inDigitoRA=&inSiglaUFRA=&inNumClasse=&inSituacao&inDataInicioMatricula=
```

**Body:**

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inNumClasse": "",
  "inSituacao": "",
  "inDataInicioMatricula": ""
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| **outAluno** | **Alfanumerico** | **Grupo de dados pessoais do aluno** |
| outNumRA | Alfanumerico (12) | Numero do RA |
| outDigitoRA | Alfanumerico (2) | Digito do RA |
| outSiglaUFRA | Alfanumerico (2) | UF do RA |
| outNomeAluno | Alfanumerico (100) | Nome completo do Aluno |
| outNomeMae | Alfanumerico (100) | Nome completo da Mae (Filiacao 01) |
| outNomePai | Alfanumerico (100) | Nome completo do Pai (Filiacao 02) |
| outDataNascimento | Alfanumerico (10) | Data de Nascimento do Aluno (DD/MM/AAAA) |
| **outMatricula** | **Alfanumerico** | **Grupo com dados da matricula pesquisada** |
| outAnoLetivo | Alfanumerico (4) | Ano de letivo da matricula |
| outCodEscola | Alfanumerico (7) | Codigo CIE da escola de matricula |
| outDescNomeAbrevEscola | Alfanumerico (60) | Nome abreviado da escola da matricula |
| outNumClasse | Alfanumerico (9) | Numero na classe da matricula |
| outNumAluno | Alfanumerico (2) | Numero do aluno na classe |
| outCodTurno | Alfanumerico (1) | Codigo identificador do turno da classe |
| outDescricaoTurno | Alfanumerico (30) | Descricao do turno da classe |
| outCodTipoEnsino | Alfanumerico (3) | Codigo identificador do tipo de ensino da classe |
| outDescTipoEnsino | Alfanumerico (100) | Descricao do tipo de ensino da classe |
| outCodSerieAno | Alfanumerico (2) | Codigo identificador da serie ou ano da classe |
| outDescSerieAno | Alfanumerico (30) | Descricao da serie / ano da classe |
| outGrauNivel | Alfanumerico (2) | Nivel de ensino do aluno em classe multisseriada ou EEE - Tipo de ensino |
| outSerieNivel | Alfanumerico (2) | Nivel de ensino do aluno em classe multisseriada ou EEE - Serie/Ano |
| outTurma | Alfanumerico (3) | Identificador da turma |
| outDescTurma | Alfanumerico (100) | Descricao da turma |
| outCodHabilitacao | Alfanumerico (6) | Codigo identificador da habilitacao da turma |
| outDescHabilitacao | Alfanumerico (100) | Descricao da habilitacao da turma |
| outDataInicioMatricula | Alfanumerico (10) | Data de inicio da matricula do aluno na classe (DD/MM/AAAA) |
| outDataFimMatricula | Alfanumerico (10) | Data de encerramento da matricula do aluno na classe (DD/MM/AAAA) |
| outDataInclusaoMatricula | Alfanumerico (10) | Data e hora de cadastro da matricula do aluno na classe (DD/MM/AAAA HH:MM:SS) |
| outCodSitMatricula | Alfanumerico (2) | Codigo identificador da situacao da matricula |
| outDescSitMatricula | Alfanumerico (100) | Descricao da situacao da matricula |
| outCodSitTranspEscolar | Alfanumerico (1) | Codigo identificador da situacao do transporte escolar |
| outDescSitTranspEscolar | Alfanumerico (30) | Descricao da situacao do transporte escolar |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

## Exemplo de Response

```json
{
  "outAluno": {
    "outNumRA": "",
    "outDigitoRA": "",
    "outSiglaUFRA": "",
    "outNomeAluno": "",
    "outNomeMae": "",
    "outNomePai": "",
    "outDataNascimento": ""
  },
  "outMatricula": {
    "outAnoLetivo": "",
    "outCodEscola": "",
    "outDescNomeAbrevEscola": "",
    "outNumClasse": "",
    "outCodTipoEnsino": "",
    "outDescTipoEnsino": "",
    "outCodSerieAno": "",
    "outDescSerieAno": "",
    "outGrauNivel": "",
    "outSerieNivel": "",
    "outCodTurno": "",
    "outDescricaoTurno": "",
    "outNumAluno": "",
    "outCodHabilitacao": "",
    "outDescHabilitacao": "",
    "outTurma": "",
    "outDescTurma": "",
    "outDataInclusaoMatricula": "",
    "outDataFimMatricula": "",
    "outDataInicioMatricula": "",
    "outHoraFinal": "",
    "outHoraInicial": "",
    "outCodSitMatricula": "",
    "outDescSitMatricula": "",
    "outCodSitTranspEscolar": "",
    "outDescSitTranspEscolar": ""
  },
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

## Tabela de Situacao da Matricula (inSituacao / outCodSitMatricula)

| Codigo | Situacao |
|--------|----------|
| 0 | ATIVO / ENCERRADO |
| 1 | TRANSFERIDO |
| 2 | ABANDONOU |
| 3 | RECLASSIFICADO |
| 4 | FALECIDO |
| 5 | NAO COMPARECIMENTO |
| 6 | CESSAO POR OBJETIVOS ATINGIDOS |
| 7 | CESSAO POR NAO FREQUENCIA |
| 8 | CESSAO POR TRANSFERENCIA/REMANEJAMENTO |
| 9 | CESSAO POR DESISTENCIA |
| 10 | REMANEJAMENTO |
| 11 | CESSAO POR EXAME |
| 12 | CESSAO POR NUMERO REDUZIDO DE ALUNOS |
| 13 | CESSAO POR FALTA DE DOCENTE |
| 14 | CESSAO POR DISPENSA |
| 15 | CESSAO POR CONCLUSAO DO CURSO |
| 16 | TRANSFERIDO (CONVERSAO DO ABANDONO) |
| 17 | REMANEJADO (CONVERSAO DO ABANDONO) |
| 18 | NAO COMPARECIMENTO / FORA DO PRAZO |
| 19 | TRANSFERIDO - CEEJA / EAD |
| 20 | NAO COMPARECIMENTO - CEEJA / EAD |
| 31 | BAIXA - TRANSFERENCIA |

## Observacoes

- O token de acesso e gerado pelo metodo ValidarUsuario e tem tempo de expiracao de 30 minutos
- Os parametros de entrada podem ser enviados via BODY (JSON) ou QUERY Parameters
- O campo outCodTipoEnsino teve seu tamanho alterado de Alfanumerico (2) para Alfanumerico (3) na versao 1.4
- O response inclui campos outHoraFinal e outHoraInicial que aparecem no exemplo JSON mas nao estao documentados na tabela de parametros de saida
