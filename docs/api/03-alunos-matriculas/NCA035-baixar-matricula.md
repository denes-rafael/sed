# NCA035 - Baixar Matricula

> Esse metodo tem como finalidade o encerramento de matriculas ativas devido transferencia, evasao (abandono) ou nao comparecimento do aluno, seguindo as regras do Sistema Cadastro de Alunos.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA035 |
| **Metodo HTTP** | POST |
| **URL** | `/Matricula/BaixarMatricula` |
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
| inTipoBaixa | Alfanumerico (1) | Sim | Identificador do tipo de encerramento da matricula (ver tabela abaixo) |
| inMotivoBaixa | Alfanumerico (1) | Condicional | Motivo da baixa por transferencia. Obrigatorio quando inTipoBaixa = 1 (ver tabela de motivos abaixo) |
| inDataBaixa | Alfanumerico (10) | Sim | Data de encerramento da matricula (DD/MM/AAAA) |
| inNumClasse | Alfanumerico (9) | Sim | Numero da classe da matricula |
| **inArquivo** | **Alfanumerico** | **Condicional** | **Grupo de dados do arquivo (obrigatorio se inTipoBaixa = 11)** |
| inNome | Alfanumerico | Condicional | Nome do Arquivo. Obrigatorio se inTipoBaixa = 11. Nao deve ser informado para os demais tipos. |
| inConteudoBase64 | Alfanumerico | Condicional | Conteudo do Arquivo em Base64. Obrigatorio se inTipoBaixa = 11. Nao deve ser informado para os demais tipos. |

## Tabela de Tipos de Baixa (inTipoBaixa)

| Codigo | Descricao |
|--------|-----------|
| 1 | Baixa por Transferencia |
| 2 | Nao Comparecimento |
| 3 | Abandono (Evasao) |
| 6 | Cessao por objetivos atingidos |
| 9 | Cessao por Desistencia |
| 11 | Cessao por Exame |

## Tabela de Motivos de Transferencia (inMotivoBaixa)

| Codigo | Descricao do Motivo |
|--------|---------------------|
| 1 | Mudanca de residencia |
| 2 | Mudanca para outra escola particular/publica |
| 3 | Mudanca para outro estado |
| 4 | Mudanca para outro pais |
| 5 | Mudanca para escola da rede particular |
| 6 | Decisoes Judiciais |
| 9 | Melhor ajustamento escolar |
| 11 | Cessao por Exame |

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inTipoBaixa": "",
  "inMotivoBaixa": "",
  "inDataBaixa": "",
  "inNumClasse": "",
  "inArquivo": {
    "inNome": "",
    "inConteudoBase64": ""
  }
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a baixa seja efetivada |
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
- O campo inMotivoBaixa e obrigatorio apenas quando inTipoBaixa = 1 (Baixa por Transferencia)
- Para Cessao por Exame (inTipoBaixa = 11), os campos inNome e inConteudoBase64 sao obrigatorios e devem conter o arquivo em Base64
- Para os demais tipos de baixa, os campos inNome e inConteudoBase64 NAO devem ser informados
- Este metodo encerra matriculas ativas por motivos de transferencia, evasao (abandono) ou nao comparecimento
