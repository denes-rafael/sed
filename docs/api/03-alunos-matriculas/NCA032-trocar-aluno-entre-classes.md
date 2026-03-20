# NCA032 - Trocar Aluno Entre Classes

> Esse metodo tem como finalidade efetuar a troca de aluno entre classes da mesma escola antes do inicio do ano letivo, atendendo as regras vigentes no sistema Cadastro de Alunos.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA032 |
| **Metodo HTTP** | POST |
| **URL** | `/Matricula/TrocarAlunoEntreClasses` |
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
| **inAluno** | **Alfanumerico** | **Sim** | **Grupo de dados identificador do aluno** |
| inNumRA | Alfanumerico (12) | Sim | Numero do RA |
| inDigitoRA | Alfanumerico (2) | Nao | Digito do RA |
| inSiglaUFRA | Alfanumerico (2) | Sim | UF do RA |
| **inMatricula** | **Alfanumerico** | **Sim** | **Grupo de dados base da matricula** |
| inAnoLetivo | Alfanumerico (4) | Sim | Ano letivo da matricula |
| inDataTroca | Alfanumerico (10) | Sim | Data da efetivacao da troca |
| inNumAluno | Alfanumerico (7) | Sim | Numero do aluno na classe. Informar "00" para geracao automatica. |
| inNumClasseOrigem | Alfanumerico (9) | Sim | Numero da classe da matricula atual |
| inNumClasseDestino | Alfanumerico (9) | Sim | Numero da classe da futura matricula |
| **inNivelEnsino** | **Alfanumerico** | **Sim** | **Grupo de indicacao no nivel de ensino da matricula** |
| inCodTipoEnsino | Alfanumerico (3) | Sim | Tipo de ensino da classe ou grau do nivel do ensino, caso classe seja multisseriada |
| inCodSerieAno | Alfanumerico (2) | Sim | Serie / Ano da classe ou serie do nivel do ensino, caso classe seja multisseriada |

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
    "inDataTroca": "",
    "inNumAluno": "",
    "inNumClasseOrigem": "",
    "inNumClasseDestino": ""
  },
  "inNivelEnsino": {
    "inCodSerieAno": "",
    "inCodTipoEnsino": ""
  }
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a matricula seja efetivada |
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
- O campo inNumAluno deve ser informado como "00" para geracao automatica
- O campo inCodTipoEnsino foi alterado de Alfanumerico (2) para Alfanumerico (3) na versao 1.1
- Este metodo efetua a troca de aluno entre classes da mesma escola ANTES do inicio do ano letivo
- Para classes multisseriadas, inCodTipoEnsino representa o grau do nivel de ensino e inCodSerieAno representa a serie do nivel de ensino
