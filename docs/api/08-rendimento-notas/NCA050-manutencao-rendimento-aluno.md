# NCA050 - Manutenção Rendimento Aluno

> Esse método tem como finalidade efetuar alterações no rendimento escolar de um aluno seguindo as regras estabelecidas no Sistema Cadastro de Alunos.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA050 |
| **Método HTTP** | POST |
| **URL** | `/Rendimento/ManutencaoRendimentoAluno` |
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
| inMotivo | Alfanumérico (1) | Sim | Motivo da alteração do rendimento do aluno: 1=Erro na Transcrição e/ou Digitação, 2=Recurso, 3=Ordem Judicial |
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
    "inMotivo": "",
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
- Motivos de alteração: 1=Erro na Transcrição e/ou Digitação, 2=Recurso, 3=Ordem Judicial
- O campo inConcluinte é obrigatório (alterado na versão 1.1): 0=Não, 1=Sim
- Diferente do NCA049 (inclusão), este método é para alteração de rendimento já existente e exige o campo inMotivo
