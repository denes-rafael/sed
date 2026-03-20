# NCA011 - Matricular Aluno

> Esse metodo tem como finalidade a criacao de matriculas de continuidade (rematricula), efetivacao de inscricoes e definicoes (matricula antecipada) e matriculas nos demais tipos de ensino (educacao infantil, ensino profissionalizante, atividade complementar, etc..)

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA011 |
| **Metodo HTTP** | POST |
| **URL** | `/Matricula/MatricularAluno` |
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
| inAnoLetivo | Alfanumerico (4) | Sim | Ano letivo da classe da matricula |
| **inAluno** | **Alfanumerico** | **Sim** | **Grupo de dados identificador do aluno** |
| inNumRA | Alfanumerico (12) | Sim | Numero do RA |
| inDigitoRA | Alfanumerico (2) | Nao | Digito do RA |
| inSiglaUFRA | Alfanumerico (2) | Sim | UF do RA |
| **inMatricula** | **Alfanumerico** | **Sim** | **Grupo de dados base da matricula** |
| inDataInicioMatricula | Alfanumerico (10) | Sim | Data de inicio do aluno na classe |
| inNumAluno | Alfanumerico (7) | Sim | Esse campo e gerado automaticamente. Sempre deve ser preenchido com "00". |
| inNumClasse | Alfanumerico (9) | Sim | Numero da classe da matricula (999999999) |
| **inNivelEnsino** | **Alfanumerico** | **Sim** | **Grupo de indicacao no nivel de ensino da matricula** |
| inCodTipoEnsino | Alfanumerico (3) | Sim | Tipo de ensino da classe ou grau do nivel do ensino, caso classe seja multisseriada |
| inCodSerieAno | Alfanumerico (2) | Sim | Serie / Ano da classe ou serie do nivel do ensino, caso classe seja multisseriada |

## Exemplo de Request

```json
{
  "inAnoLetivo": "",
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inMatricula": {
    "inDataInicioMatricula": "",
    "inNumAluno": "",
    "inNumClasse": ""
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
- O campo inNumAluno e gerado automaticamente e deve ser sempre preenchido com "00"
- O campo inCodTipoEnsino foi alterado de Alfanumerico (2) para Alfanumerico (3) na versao 1.5
- Para classes multisseriadas, inCodTipoEnsino representa o grau do nivel de ensino e inCodSerieAno representa a serie do nivel de ensino
- Este metodo suporta matriculas de continuidade (rematricula), efetivacao de inscricoes/definicoes (matricula antecipada) e matriculas em tipos de ensino como educacao infantil, ensino profissionalizante e atividade complementar
