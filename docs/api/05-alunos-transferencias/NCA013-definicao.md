# NCA013 - Definicao

> Esse metodo tem como finalidade a indicacao de alunos matriculados na rede publica e que estejam em troca de ciclo de ensino (definicao de alunos), seguindo os criterios determinados no processo da matricula antecipada.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA013 |
| **Metodo HTTP** | POST |
| **URL** | `/Inscricao/Definicao` |
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
| inDefinicao | Alfanumerico | Sim | Grupo de dados base da definicao |
| inDefinicao.inAnoLetivo | Alfanumerico (4) | Sim | Ano letivo da definicao (posterior ao da matricula atual) |
| inDefinicao.inCodEscola | Alfanumerico (7) | Sim | Codigo CIE da escola da matricula atual (ativa) |
| inDefinicao.inNumClasseMatriculaAtual | Alfanumerico (9) | Sim | Numero da classe da matricula atual (ativa) |
| inDefinicao.inFase | Alfanumerico (1) | Sim | Tipo de definicoes: 1 - Definicao dos Alunos para o 1o Ano do Ensino Fundamental, 2 - Definicao dos Alunos para o 6o Ano do Ensino Fundamental, 6 - Definicao dos Alunos para o Ensino Medio |
| inDefinicao.inInteresseIntegral | Alfanumerico (1) | Nao | Indica interesse em uma futura matricula no turno integral. Preencher com "1" caso haja interesse |
| inDefinicao.inAutorizacaoVacina | Alfanumerico (1) | Nao | Indica autorizacao de vacina. Preencher com "1" se SIM, "0" se NAO |
| inNivelEnsino | Alfanumerico | Sim | Grupo de indicacao no nivel de ensino da inscricao |
| inNivelEnsino.inCodTipoEnsino | Alfanumerico (3) | Sim | Codigo do tipo de ensino pretendido |
| inNivelEnsino.inCodSerieAno | Alfanumerico (2) | Sim | Codigo da Serie ou Ano pretendido |

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inDefinicao": {
    "inAnoLetivo": "",
    "inCodEscola": "",
    "inNumClasseMatriculaAtual": "",
    "inFase": "",
    "inInteresseIntegral": "",
    "inAutorizacaoVacina": ""
  },
  "inNivelEnsino": {
    "inCodTipoEnsino": "",
    "inCodSerieAno": ""
  }
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

- Este metodo e exclusivo para alunos matriculados na rede publica que estejam em troca de ciclo de ensino
- O campo inFase aceita os valores 1 (Definicao 1o ano EF), 2 (Definicao 6o ano EF) e 6 (Definicao EM)
- O campo inAnoLetivo deve ser posterior ao da matricula atual
- O campo inAutorizacaoVacina foi incluido na versao 1.2 (28/08/2024)
- O token de acesso e gerado pelo metodo ValidarUsuario e tem um tempo de expiracao de 30 minutos
