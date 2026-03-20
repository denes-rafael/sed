# NCA004 - Listar Matriculas por RA

> Esse metodo tem como finalidade extrair e retornar ao solicitante todas as matriculas cadastradas no sistema NCA, independentemente da situacao, de um determinado aluno utilizando como base para pesquisa o RA do mesmo.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA004 |
| **Metodo HTTP** | GET |
| **URL** | `/Matricula/ListarMatriculasRA` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: BearerToken (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

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

## Exemplo de Request

**Query Parameters:**

```
/Matricula/ListarMatriculasRA?inNumRA=&inDigitoRA=&inSiglaUFRA=
```

**Body:**

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  }
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
| outNomeMae | Alfanumerico (100) | Nome completo da Mae |
| outNomePai | Alfanumerico (100) | Nome completo do Pai |
| outDataNascimento | Alfanumerico (10) | Data de Nascimento do Aluno (DD/MM/AAAA) |
| **outListaMatriculas** | **Alfanumerico** | **Grupo de matriculas do aluno no formato ARRAY [1 : N]. Matriculas em ordem decrescente de ano letivo** |
| outAnoLetivo | Alfanumerico (4) | Ano de letivo da matricula |
| outMunicipio | Alfanumerico (40) | Nome do municipio da escola de matricula |
| outRedeEnsino | Alfanumerico (40) | Nome da rede de ensino da escola de matricula |
| outCodEscola | Alfanumerico (7) | Codigo CIE da escola de matricula |
| outCodUnidade | Alfanumerico (7) | Codigo da unidade da escola CIE de matricula |
| outDescNomeAbrevEscola | Alfanumerico (60) | Nome abreviado da escola da matricula |
| outNumClasse | Alfanumerico (9) | Numero na classe da matricula |
| outCodTurno | Alfanumerico (1) | Codigo identificador do turno da classe |
| outCodTipoEnsino | Alfanumerico (3) | Codigo identificador do tipo de ensino da classe |
| outCodSerieAno | Alfanumerico (2) | Codigo identificador da serie ou ano da classe |
| outGrauNivel | Alfanumerico (2) | Nivel de ensino do aluno em classe multisseriada ou EEE - Tipo de ensino |
| outSerieNivel | Alfanumerico (2) | Nivel de ensino do aluno em classe multisseriada ou EEE - Serie/Ano |
| outTurma | Alfanumerico (3) | Identificador da turma |
| outDescSerieAno | Alfanumerico (100) | Descricao da serie ou ano da classe de matricula |
| outDescTipoEnsino | Alfanumerico (100) | Descricao do tipo de ensino da classe de matricula |
| outDescTurma | Alfanumerico (100) | Descricao da turma |
| outDescricaoTurno | Alfanumerico (60) | Descricao do turno da classe de matricula |
| outCodHabilitacao | Alfanumerico (6) | Codigo identificador da habilitacao da turma |
| outDescHabilitacao | Alfanumerico (100) | Descricao da habilitacao da turma |
| outNumAluno | Alfanumerico (2) | Numero do aluno na classe |
| outDataInicioMatricula | Alfanumerico (10) | Data de inicio da matricula do aluno na classe (DD/MM/AAAA) |
| outDataFimMatricula | Alfanumerico (10) | Data de encerramento da matricula do aluno na classe (DD/MM/AAAA) |
| outDataInclusaoMatricula | Alfanumerico (10) | Data e hora de cadastro da matricula do aluno na classe (DD/MM/AAAA HH:MM:SS) |
| outCodSitMatricula | Alfanumerico (2) | Codigo identificador da situacao da matricula (ver tabela abaixo) |
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
  "outListaMatriculas": [
    {
      "outAnoLetivo": "",
      "outMunicipio": "",
      "outNomeRedeEnsino": "",
      "outCodEscola": "",
      "outCodUnidade": "",
      "outDescNomeAbrevEscola": "",
      "outNumClasse": "",
      "outNumAluno": "",
      "outCodTurno": "",
      "outDescricaoTurno": "",
      "outCodTipoEnsino": "",
      "outDescTipoEnsino": "",
      "outCodSerieAno": "",
      "outDescSerieAno": "",
      "outGrauNivel": "",
      "outSerieNivel": "",
      "outTurma": "",
      "outDescTurma": "",
      "outCodHabilitacao": "",
      "outDescHabilitacao": "",
      "outDataInicioMatricula": "",
      "outDataFimMatricula": "",
      "outDataInclusaoMatricula": "",
      "outCodSitMatricula": "",
      "outDescSitMatricula": "",
      "outCodSitTranspEscolar": "",
      "outDescSitTranspEscolar": ""
    }
  ],
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

## Tabela de Situacao da Matricula (outCodSitMatricula)

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
- As matriculas sao retornadas em ordem decrescente de ano letivo
- O campo outCodTipoEnsino teve seu tamanho alterado de Alfanumerico (2) para Alfanumerico (3) na versao 1.8
