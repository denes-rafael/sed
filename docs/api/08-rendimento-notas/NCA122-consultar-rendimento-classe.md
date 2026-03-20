# NCA122 - Consultar Rendimento Classe

> A finalidade desse serviço é efetuar consulta do lançamento do rendimento escolar (aprovação ou reprovação) dos alunos em uma determinada classe, seguindo as regras do Sistema Secretaria Digital (SED).

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA122 |
| **Método HTTP** | GET |
| **URL** | `/Rendimento/ConsultarRendimentoClasse` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token (gerado pelo método ValidarUsuario, expira em 30 minutos) |

## Parâmetros de Entrada (Request)

**Formato:** Parâmetros (Query)

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inAnoLetivo | Alfanumérico (4) | Sim | Ano Letivo |
| inNumClasse | Alfanumérico (9) | Sim | Numero da classe |
| inSemestre | Alfanumérico (1) | Sim | "1"=1o Semestre, "2"=2o Semestre, "0"=Anual |

## Exemplo de Request

```
GET /Rendimento/ConsultarRendimentoClasse?inAnoLetivo=&inNumClasse=&inSemestre=
```

## Parâmetros de Saída (Response)

**Formato:** JSON

### Dados da classe

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outDescTipoEnsino | Alfanumérico | Descrição do tipo de ensino |
| outDescSerie | Alfanumérico (15) | Descrição da série |
| outDescEscola | Alfanumérico (44) | Nome da escola |
| outHoraInicial | Alfanumérico (8) | Hora inicial da turma (hh:mm:ss) |
| outHoraFinal | Alfanumérico (8) | Hora final da turma (hh:mm:ss) |
| outNumSala | Alfanumérico (8) | Numero da sala |
| outDescTurma | Alfanumérico (2) | Sigla de identificação da Turma |
| outDescTurno | Alfanumérico (8) | Turno da classe |

### Totais de rendimento

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outTotAluAprovado | Alfanumérico (8) | Total de alunos aprovados |
| outTotAluAprovadoParc | Alfanumérico (8) | Total de alunos aprovados parcialmente |
| outTotAluEmAndamento | Alfanumérico (8) | Total de alunos com curso em andamento |
| outTotAluGeral | Alfanumérico (8) | Total geral de alunos |
| outTotAluRendFreqInsuf | Alfanumérico (8) | Total de alunos retidos por rendimento + retidos por frequência |
| outTotAluRetParcial | Alfanumérico (8) | Total de alunos retidos parcialmente |
| outTotAluTermEspecifica | Alfanumérico (8) | Total de aluno terminalidade específica |

### Lista: outAlunosRendimento (Array)

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outAlunoRendimento | Lista | Lista de alunos da classe e seus rendimentos |
| outNumRA | Alfanumérico (12) | RA do aluno |
| outDigitoRA | Alfanumérico (2) | Dígito RA aluno |
| outSiglaUFRA | Alfanumérico (2) | UF RA do aluno |
| outNumAluno | Alfanumérico (2) | Numero do aluno na classe |
| outDescRendimento | Alfanumérico (15) | Descrição do tipo de Rendimento |

### Outros parâmetros

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outProcesso | Grupo | Retorno da requisição |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outDescTipoEnsino": "string",
  "outDescSerie": "string",
  "outDescEscola": "string",
  "outHoraInicial": "string",
  "outHoraFinal": "string",
  "outNumSala": "string",
  "outDescTurma": "string",
  "outDescTurno": "string",
  "outTotAluAprovado": "string",
  "outTotAluAprovadoParc": "string",
  "outTotAluEmAndamento": "string",
  "outTotAluGeral": "string",
  "outTotAluRendFreqInsuf": "string",
  "outTotAluRetParcial": "string",
  "outTotAluTermEspecifica": "string",
  "outAlunosRendimento": [
    {
      "outNumRA": "string",
      "outDigitoRA": "string",
      "outSiglaUFRA": "string",
      "outNumAluno": "string",
      "outDescRendimento": "string"
    }
  ],
  "outErro": "string",
  "outProcessoID": "string"
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

- Retorna o rendimento escolar de todos os alunos de uma determinada classe
- O parâmetro inSemestre aceita: "1"=1o Semestre, "2"=2o Semestre, "0"=Anual
- A lista outAlunosRendimento contém os dados individuais de cada aluno com seu rendimento
