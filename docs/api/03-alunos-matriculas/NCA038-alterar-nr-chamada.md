# NCA038 - Alterar Numero de Chamada

> Esse metodo tem como finalidade a alteracao do numero de chamada de uma matricula ativa na classe.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA038 |
| **Metodo HTTP** | POST |
| **URL** | `/Matricula/AlterarNrChamada` |
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
| inAnoLetivo | Alfanumerico (4) | Sim | Ano letivo da matricula |
| inNumClasse | Alfanumerico (9) | Sim | Numero da classe da matricula |
| inNumAluno | Alfanumerico (2) | Sim | Futuro numero de chamada |

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inAnoLetivo": "",
  "inNumClasse": "",
  "inNumAluno": ""
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a alteracao seja efetivada |
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
- Este metodo altera o numero de chamada apenas de matriculas ativas
- O campo inNumAluno representa o futuro numero de chamada do aluno na classe
