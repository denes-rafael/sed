# NCA049 - Incluir Rendimento Aluno

> Esse método tem como finalidade efetuar o lançamento do rendimento escolar (aprovação ou reprovação) de um aluno em uma determinada turma dos ensinos fundamental, médio, educação de jovens e adultos (EJA) e profissional, seguindo as regras do Sistema Cadastro de Alunos.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA049 |
| **Método HTTP** | POST |
| **URL** | `/Rendimento/IncluirRendimentoAluno` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token (gerado pelo método ValidarUsuario, expira em 30 minutos) |

## Parâmetros de Entrada (Request)

**Formato:** BODY (JSON)

### Grupo: inAluno

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inAluno | Alfanumérico | Sim | Grupo de dados identificador do aluno |
| inNumRA | Alfanumérico (12) | Sim | Número do RA |
| inDigitoRA | Alfanumérico (2) | Não | Dígito do RA |
| inSiglaUFRA | Alfanumérico (2) | Sim | UF do RA |

### Grupo: inMatricula

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inMatricula | Alfanumérico | Sim | Grupo de dados base da matrícula |
| inAnoLetivo | Alfanumérico (4) | Sim | Ano letivo da classe |
| inNumClasse | Alfanumérico (9) | Sim | Número de classe que terá o rendimento lançado (999999999) |
| inRendimento | Alfanumérico (1) | Sim | Rendimento do aluno: 1=Aprovado, 2=Aprovado Parcialmente, 3=Retido por Frequência, 4=Retido por Rendimento, 5=Retido Parcialmente, 7=Terminalidade Específica, 8=Curso Em Andamento |
| inConcluinte | Alfanumérico (1) | Sim | 0=Não, 1=Sim |

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inMatricula": {
    "inAnoLetivo": "",
    "inNumClasse": "",
    "inRendimento": "",
    "inConcluinte": ""
  }
}
```

## Parâmetros de Saída (Response)

**Formato:** JSON

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outSucesso | Alfanumérico (100) | Parâmetro preenchido caso a matrícula seja efetivada |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outSucesso": "",
  "outErro": "",
  "outProcessoID": ""
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

- Valores de rendimento: 1=Aprovado, 2=Aprovado Parcialmente, 3=Retido por Frequência, 4=Retido por Rendimento, 5=Retido Parcialmente, 7=Terminalidade Específica, 8=Curso Em Andamento
- O campo inConcluinte é obrigatório (alterado na versão 1.1): 0=Não, 1=Sim
- Aplicável aos ensinos fundamental, médio, EJA e profissional
