# NCA009 - Formacao da Classe

> **Versao:** 1.5 | **Ultima atualizacao:** 09/02/2024 | **Autor:** Alexandre Mendes / Italo Galetti

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | FormacaoClasse |
| **Codigo** | NCA009 |
| **Descricao** | Esse metodo tem como finalidade extrair e retornar informacoes (escola, tipo de ensino e totais de alunos) de uma turma especifica e a relacao de alunos dela, independente da situacao da matricula. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/RelacaoAlunosClasse/FormacaoClasse` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/RelacaoAlunosClasse/FormacaoClasse` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY ou QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inNumClasse | Alfanumerico (9) | Obrigatorio | Numero da classe (turma) |

---

## Exemplo de Request

**Query Parameters:**

```
/RelacaoAlunosClasse/FormacaoClasse?inNumClasse=
```

**Body:**

```json
{
  "inNumClasse": ""
}
```

---

## Parametros de Saida

### Dados da Classe

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outCodEscola | Alfanumerico (7) | Codigo da escola onde a classe (turma) foi criada |
| outDescNomeAbrevEscola | Alfanumerico (60) | Nome abreviado da escola |
| outCodTipoEnsino | Alfanumerico (3) | Codigo do tipo de ensino da classe (turma) |
| outDescTipoEnsino | Alfanumerico (60) | Descricao do tipo de ensino |
| outAnoLetivo | Alfanumerico (4) | Ano letivo da classe |
| outNumClasse | Alfanumerico (7) | Numero da classe (turma) consultada |
| outCodSerieAno | Alfanumerico (2) | Codigo da Serie ou Ano da classe (turma) |
| outTurma | Alfanumerico (2) | Codigo identificador da turma (ex: A, 1B, BM) |
| outCodTurno | Alfanumerico (2) | Codigo do turno de funcionamento da classe (turma) |
| outDescricaoTurno | Alfanumerico (30) | Descricao do turno da classe (turma) |
| outCodHabilitacao | Alfanumerico (6) | Codigo da habilitacao da classe (turma) |
| outCodTipoClasse | Alfanumerico (2) | Codigo identificador do tipo de classe (turma) |
| outNumSala | Alfanumerico (3) | Numero da sala de funcionamento da classe (turma) |
| outHorarioInicio | Alfanumerico (5) | Horario do inicio da aula (HH:MM) |
| outHorarioFim | Alfanumerico (5) | Horario do final da aula (HH:MM) |
| outQtdAtual | Alfanumerico (3) | Quantidade de alunos ativos na classe (turma) |
| outQtdDigitados | Alfanumerico (3) | Total de alunos matriculados na classe (turma) |
| outQtdEvadidos | Alfanumerico (3) | Quantidade de alunos com a situacao de matricula: abandono |
| outQtdNCom | Alfanumerico (3) | Quantidade de alunos com a situacao de matricula: nao comparecimento |
| outQtdTransferidos | Alfanumerico (3) | Quantidade de alunos transferidos para outra escola |
| outQtdRemanejados | Alfanumerico (3) | Quantidade de alunos remanejados para outras classes na mesma escola |
| outQtdCessados | Alfanumerico (3) | Quantidade de alunos com a situacao de matricula cessada |
| outQtdReclassificados | Alfanumerico (3) | Quantidade de alunos reclassificados para serie ou ano superior na mesma escola |
| outQtdOutros | Alfanumerico (3) | Total de alunos com as situacoes: Falecido, Baixa transferencia, Remanejado convertido de abandono, Transferido convertido de abandono |
| outCapacidadeFisicaMax | Alfanumerico (3) | Capacidade Fisica Maxima de alunos na classe |
| outDataInicioAula | Alfanumerico (10) | Data de inicio da classe (turma). Formato DD/MM/AAAA |
| outDataFimAula | Alfanumerico (10) | Data de encerramento da classe (turma). Formato DD/MM/AAAA |

### Grupo outAlunos (alunos matriculados - ARRAY [1 : N])

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outAlunos | Alfanumerico | Grupo de alunos matriculados na classe (turma). Ordenados pelo numero do aluno na classe |
| outNumRA | Alfanumerico (12) | Numero do RA |
| outDigitoRA | Alfanumerico (2) | Digito do RA |
| outSiglaUFRA | Alfanumerico (2) | UF do RA |
| outNomeAluno | Alfanumerico (100) | Nome completo do Aluno |
| outNumAluno | Alfanumerico (2) | Numero do aluno na classe (turma) |
| outDataNascimento | Alfanumerico (10) | Data de Nascimento do Aluno (DD/MM/AAAA) |
| outGrauNivel | Alfanumerico (2) | Nivel de ensino do aluno em classe multisseriada ou EEE - Tipo de ensino |
| outSerieNivel | Alfanumerico (2) | Nivel de ensino do aluno em classe multisseriada ou EEE - Serie/Ano |
| outCodSitMatricula | Alfanumerico (2) | Codigo identificador da situacao da matricula (ver tabela 2.2.1) |
| outDescSitMatricula | Alfanumerico (100) | Descricao da situacao da matricula |
| outDataInicioMatricula | Alfanumerico (10) | Data de Inicio da Matricula (DD/MM/AAAA) |
| outDataFimMatricula | Alfanumerico (10) | Data de Fim da Matricula (DD/MM/AAAA) |

### Outros parametros de saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outCodEscola": "",
    "outDescNomeAbrevEscola": "",
    "outCodTipoEnsino": "",
    "outDescTipoEnsino": "",
    "outAnoLetivo": "",
    "outNumClasse": "",
    "outCodSerieAno": "",
    "outTurma": "",
    "outCodTurno": "",
    "outDescricaoTurno": "",
    "outCodHabilitacao": "",
    "outCodTipoClasse": "",
    "outNumSala": "",
    "outHorarioInicio": "",
    "outHorarioFim": "",
    "outQtdAtual": "",
    "outQtdDigitados": "",
    "outQtdEvadidos": "",
    "outQtdNCom": "",
    "outQtdOutros": "",
    "outQtdTransferidos": "",
    "outQtdRemanejados": "",
    "outQtdCessados": "",
    "outQtdReclassificados": "",
    "outCapacidadeFisicaMax": "",
    "outDataInicioAula": "",
    "outDataFimAula": "",
    "outAlunos": [
        {
            "outNumRA": "",
            "outDigitoRA": "",
            "outSiglaUFRA": "",
            "outNomeAluno": "",
            "outNumAluno": "",
            "outDataNascimento": "",
            "outGrauNivel": "",
            "outSerieNivel": "",
            "outCodSitMatricula": "",
            "outDescSitMatricula": "",
            "outDataInicioMatricula": "",
            "outDataFimMatricula": ""
        }
    ],
    "outErro": "",
    "outProcessoID": ""
}
```

---

## Codigos de Erro

| Status | Descricao |
|---|---|
| 200 | Requisicao processada com sucesso: Retorno de dados |
| 200 | Requisicao processada com sucesso: Erro de negocio, outErro preenchido |
| 401 | Requisicao rejeitada: Token invalido ou expirado |
| 500 | Erro de infraestrutura: outErro preenchido |

---

## Tabelas de Apoio

### 2.2.1 - Situacao da Matricula

| Codigo | Descricao |
|---|---|
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

---

## Observacoes

- Os parametros de entrada podem ser enviados via BODY ou QUERY Parameters.
- O campo outCodTipoEnsino teve seu tamanho alterado de alfanumerico (2) para alfanumerico (3) na versao 1.4.
- Os campos outDataInicioMatricula e outDataFimMatricula foram incluidos na versao 1.5.
- Os campos outDataInicioAula e outDataFimAula foram incluidos na versao 1.3.
- A lista de alunos e ordenada pelo numero do aluno na classe (outNumAluno).
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
