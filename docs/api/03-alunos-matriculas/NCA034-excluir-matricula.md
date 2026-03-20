# NCA034 - Excluir Matricula

> Esse metodo tem como finalidade a exclusao de matriculas ativas, seguindo as regras do Sistema Cadastro de Alunos.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA034 |
| **Metodo HTTP** | POST |
| **URL** | `/Matricula/ExcluirMatricula` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: BearerToken (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

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
| inNumClasse | Alfanumerico (9) | Sim | Numero da classe da matricula |

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inNumClasse": ""
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a exclusao seja efetivada |
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
- Este metodo exclui apenas matriculas ativas
- A exclusao segue as regras vigentes do Sistema Cadastro de Alunos
