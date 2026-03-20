# NCA015 - Cancelar Inscricao e Definicao

> Esse metodo tem como finalidade o cancelamento de inscricoes (alunos fora da escola ou transferencias) e definicoes de alunos por escola e ano letivo que estejam com situacao ativa no Sistema Cadastro de Alunos.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA015 |
| **Metodo HTTP** | POST |
| **URL** | `/Inscricao/CancelarInscricaoDefinicao` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

**Endpoints:**
- **Producao:** `https://integracaosed.educacao.sp.gov.br/ncaapi/api`
- **Homologacao:** `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api`

## Parametros de Entrada (Request)

Formato: **BODY**

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inAluno | Alfanumerico | Sim | Grupo de dados identificador do aluno |
| inAluno.inNumRA | Alfanumerico (12) | Sim | Numero do RA |
| inAluno.inDigitoRA | Alfanumerico (2) | Nao | Digito do RA |
| inAluno.inSiglaUFRA | Alfanumerico (2) | Sim | UF do RA |
| inAnoLetivo | Alfanumerico (4) | Sim | Ano letivo da inscricao |
| inCodEscola | Alfanumerico (7) | Sim | Codigo CIE da escola da inscricao |
| inTipoInscricao | Alfanumerico (1) | Sim | Tipo de inscricoes (inscricoes, transferencias e definicoes): 0 - Inscricao de Alunos por Transferencia, 1 - Definicao dos Alunos para o 1o Ano do Ensino Fundamental, 2 - Definicao dos Alunos para o 6o Ano do Ensino Fundamental, 4 - Inscricao de Aluno Fora da Rede Publica (Ensino Fundamental), 6 - Definicao dos Alunos para o Ensino Medio, 7 - Inscricao de Aluno Fora da Rede Publica (Ensino Medio), 8 - Inscricao de Alunos por Deslocamento, 9 - Inscricao por Intencao de Transferencia |

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inAnoLetivo": "",
  "inCodEscola": "",
  "inTipoInscricao": ""
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a inscricao seja efetivada |
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

- Este metodo cancela inscricoes, definicoes e transferencias de alunos que estejam com situacao ativa
- O campo inTipoInscricao aceita os valores: 0 (Transferencia), 1 (Definicao 1o ano EF), 2 (Definicao 6o ano EF), 4 (Fora da rede publica EF), 6 (Definicao EM), 7 (Fora da rede publica EM), 8 (Deslocamento), 9 (Intencao de Transferencia)
- O token de acesso e gerado pelo metodo ValidarUsuario e tem um tempo de expiracao de 30 minutos
