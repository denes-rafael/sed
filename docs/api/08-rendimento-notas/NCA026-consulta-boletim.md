# NCA026 - Consulta Boletim

> Esse método tem como finalidade a geração por ano letivo do boletim escolar do aluno matriculado na rede estadual.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA026 |
| **Método HTTP** | GET |
| **URL** | `/Boletim/ConsultaBoletim` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token (gerado pelo método ValidarUsuario, expira em 30 minutos) |

## Parâmetros de Entrada (Request)

**Formato:** QUERY Parameters

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inAluno | Alfanumérico | Sim | Grupo de dados identificador do aluno |
| inNumRA | Alfanumérico (12) | Sim | Número do RA |
| inDigitoRA | Alfanumérico (2) | Não | Dígito do RA |
| inSiglaUFRA | Alfanumérico (2) | Sim | UF do RA |
| inDataNascimento | Alfanumérico (10) | Sim | Data de nascimento do aluno |
| inAnoLetivo | Alfanumérico (4) | Sim | Ano letivo da matrícula |

## Exemplo de Request

```
GET /Boletim/ConsultaBoletim?inNumRA=&inDigitoRA=&inSiglaUFRA=&inDataNascimento=&inAnoLetivo=
```

## Parâmetros de Saída (Response)

**Formato:** JSON

### Grupo: outListaBoletins (Array [1:N])

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outListaBoletins | Alfanumérico | Grupo de disciplinas do aluno no formato ARRAY [1:N] |
| outListaDisciplinas | Alfanumérico | Grupo de disciplinas do aluno no formato ARRAY [1:N] |
| outListaDisciplinas (interno) | Alfanumérico | Grupo de notas e frequências do aluno no formato ARRAY [1:N] |
| outNota | Alfanumérico (5) | Nota bimestral da disciplina |
| outNotaMediaFinal | Alfanumérico (5) | Nota média final da disciplina |
| outNumeroFaltas | Alfanumérico (5) | Número de faltas bimestral |
| outNumeroTotalFaltas | Alfanumérico (5) | Total de faltas da disciplina |
| outNumeroFaltasCompensadas | Alfanumérico (5) | Número de faltas compensadas |
| outPercentualFrequencia | Alfanumérico (5) | Percentual de frequência da disciplina |
| outCodigoTipoFechamento | Alfanumérico (5) | Código identificador do bimestre: 5=1o Bimestre, 6=2o Bimestre, 7=3o Bimestre, 8=4o Bimestre, 10=Conceito Final |
| outCodigoDisciplina | Alfanumérico (4) | Código identificador da disciplina |
| outNomeDisciplina | Alfanumérico (60) | Nome identificador da disciplina |
| NumeroAulasPlanejadas | Alfanumérico | Número de aulas planejadas |
| NumeroAulasRealizadas | Alfanumérico | Número de aulas realizadas |

### Dados do boletim

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outQuantidadeBimestre | Alfanumérico (1) | Total de bimestre do boletim |
| outExisteCF | Booleano | Identifica se há conceito final |
| outResultadoFinal | Alfanumérico (20) | Conceito final |
| outNomeAluno | Alfanumérico (100) | Nome do Aluno |
| outNumeroRa | Alfanumérico (12) | Número do RA do Aluno |
| outDigitoRa | Alfanumérico (2) | Dígito do RA do Aluno |
| outUfRa | Alfanumérico (2) | Sigla UF do RA |
| outNomeDiretoria | Alfanumérico (60) | Nome da Diretoria da escola de matrícula |
| outCodigoEscola | Alfanumérico (7) | Código CIE da escola de matrícula |
| outNomeEscola | Alfanumérico (100) | Nome da escola de matrícula |
| outNomeTurma | Alfanumérico (30) | Descrição da turma |
| outNomeTipoEnsino | Alfanumérico (60) | Tipo de ensino da matrícula |
| outAnoLetivo | Alfanumérico (4) | Ano letivo da matrícula |
| outArquivoJSON | Alfanumérico (10000) | Saída Base64 para a geração do boletim |

### Outros parâmetros

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outSucesso | Alfanumérico (1000) | Parâmetro destinado para retorno de sucesso |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outListaBoletins": [
    {
      "outListaDisciplinas": [
        {
          "outListaDisciplinas": [
            {
              "outNota": "",
              "outNumeroFaltas": "",
              "outNumeroTotalFaltas": "",
              "outNumeroFaltasCompensadas": "",
              "outPercentualFrequencia": "",
              "outCodigoTipoFechamento": "",
              "NumeroAulasPlanejadas": "",
              "NumeroAulasRealizadas": ""
            },
            {
              "outNotaMediaFinal": "",
              "outNumeroFaltas": "",
              "outNumeroTotalFaltas": "",
              "outNumeroFaltasCompensadas": "",
              "outPercentualFrequencia": "",
              "outCodigoTipoFechamento": "",
              "NumeroAulasPlanejadas": "",
              "NumeroAulasRealizadas": ""
            }
          ],
          "outCodigoTipoFechamento": "",
          "outCodigoDisciplina": "",
          "outNomeDisciplina": ""
        }
      ],
      "outQuantidadeBimestre": "",
      "outExisteCF": true,
      "outResultadoFinal": "",
      "outNomeAluno": "",
      "outNumeroRa": "",
      "outDigitoRa": "",
      "outUfRa": "SP",
      "outNomeDiretoria": "",
      "outCodigoEscola": "",
      "outNomeEscola": "",
      "outNomeTurma": "",
      "outNomeTipoEnsino": "",
      "outAnoLetivo": "",
      "outArquivoPDF": "Texto do pdf"
    }
  ],
  "outSucesso": "OK",
  "outProcessoID": "343337664"
}
```

## Códigos de Erro

| Código | Mensagem | Descrição |
|--------|----------|-----------|
| 200 | OK | Requisição processada com sucesso: Retorno de dados |
| 200 | outErro preenchido | Requisição processada com sucesso: Erro de negócio |
| 401 | Token inválido ou expirado | Requisição rejeitada |
| 500 | outErro preenchido | Erro de infraestrutura |

## Observações

- Apenas para alunos matriculados na rede estadual
- O parâmetro outListaBoletins foi incluído na versão 1.2 para atender a situação do aluno que possui 2 matrículas vigentes no mesmo ano letivo
- outCodigoTipoFechamento: 5=1o Bimestre, 6=2o Bimestre, 7=3o Bimestre, 8=4o Bimestre, 10=Conceito Final
- O campo outArquivoPDF retorna o boletim em formato Base64
