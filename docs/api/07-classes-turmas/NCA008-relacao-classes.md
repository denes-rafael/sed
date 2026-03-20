# NCA008 - Relacao de Classes

> **Versao:** 1.3 | **Ultima atualizacao:** 27/02/2023 | **Autor:** Alexandre Mendes / Italo Galetti

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | RelacaoClasses |
| **Codigo** | NCA008 |
| **Descricao** | Esse metodo tem como finalidade extrair e retornar a relacao de classes ativas de uma determinada escola por ano-letivo. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/RelacaoAlunosClasse/RelacaoClasses` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/RelacaoAlunosClasse/RelacaoClasses` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY ou QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inAnoLetivo | Alfanumerico (4) | Obrigatorio | Ano letivo da pesquisa |
| inCodEscola | Alfanumerico (7) | Obrigatorio | Codigo da escola que sera pesquisada |
| inCodTipoEnsino | Alfanumerico (3) | Opcional | Codigo do tipo de ensino |
| inCodSerieAno | Alfanumerico (7) | Opcional | Codigo da serie ou ano |
| inCodTurno | Alfanumerico (7) | Opcional | Codigo do turno |
| inSemestre | Alfanumerico (1) | Opcional | Identificador do semestre: 0 - classes do tipo anual, 1 - classes de primeiro semestre, 2 - classes de segundo semestre, Nao informado - retorna classes independente da duracao |

---

## Exemplo de Request

**Query Parameters:**

```
/RelacaoAlunosClasse/RelacaoClasses?inAnoLetivo=&inCodEscola=&inCodTipoEnsino=&inCodSerieAno=&inCodTurno=&inSemestre=
```

**Body:**

```json
{
   "inAnoLetivo": "",
   "inCodEscola": "",
   "inCodTipoEnsino": "",
   "inCodSerieAno": "",
   "inCodTurno": "",
   "inSemestre": ""
}
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outAnoLetivo | Alfanumerico (4) | Ano letivo pesquisado |
| outCodEscola | Alfanumerico (7) | Codigo da escola pesquisada |
| outDescNomeAbrevEscola | Alfanumerico (60) | Nome abreviado da escola |
| outClasses | Alfanumerico | Grupo de classes no formato ARRAY [1 : N] |
| outNumClasse | Alfanumerico (7) | Numero da classe (turma) consultada |
| outCodTipoEnsino | Alfanumerico (3) | Codigo do tipo de ensino da classe (turma) |
| outDescTipoEnsino | Alfanumerico (60) | Descricao do tipo de ensino |
| outCodSerieAno | Alfanumerico (2) | Codigo da Serie ou Ano da classe (turma) |
| outTurma | Alfanumerico (2) | Codigo identificador da turma (ex: A, 1B, BM) |
| outCodTurno | Alfanumerico (2) | Codigo do turno de funcionamento da classe (turma) |
| outDescricaoTurno | Alfanumerico (30) | Descricao do turno da classe (turma) |
| outCodHabilitacao | Alfanumerico (6) | Codigo da habilitacao da classe (turma) |
| outNumSala | Alfanumerico (3) | Numero da sala de funcionamento da classe (turma) |
| outHorarioInicio | Alfanumerico (5) | Horario do inicio da aula (HH:MM) |
| outHorarioFim | Alfanumerico (5) | Horario do final da aula (HH:MM) |
| outCodTipoClasse | Alfanumerico (2) | Codigo identificador do tipo de classe (turma) |
| outDescTipoClasse | Alfanumerico (60) | Descricao do tipo da classe |
| outSemestre | Alfanumerico (1) | Indicador do periodo da classe: 0 - Anual, 1 - Primeiro semestre, 2 - Segundo semestre |
| outQtdAtual | Alfanumerico (3) | Quantidade de alunos ativos na classe (turma) |
| outQtdDigitados | Alfanumerico (3) | Total de alunos matriculados na classe (turma) |
| outQtdEvadidos | Alfanumerico (3) | Quantidade de alunos com a situacao de matricula: abandono |
| outQtdNCom | Alfanumerico (3) | Quantidade de alunos com a situacao de matricula: nao comparecimento |
| outQtdTransferidos | Alfanumerico (3) | Quantidade de alunos transferidos para outra escola |
| outQtdRemanejados | Alfanumerico (3) | Quantidade de alunos remanejados para outras classes na mesma escola |
| outQtdCessados | Alfanumerico (3) | Quantidade de alunos com a situacao de matricula cessada |
| outQtdReclassificados | Alfanumerico (3) | Quantidade de alunos reclassificados para serie ou ano superior na mesma escola |
| outQtdOutros | Alfanumerico (3) | Total de alunos com as situacoes: Falecido, Baixa transferencia, Remanejado convertido de abandono, Transferido convertido de abandono |
| outCapacidadeFisicaMax | Alfanumerico (3) | Capacidade Fisica Maxima de alunos na classe |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outAnoLetivo": "",
    "outCodEscola": "",
    "outDescNomeAbrevEscola": "",
    "outClasses": [
        {
            "outNumClasse": "",
            "outCodTipoEnsino": "",
            "outDescTipoEnsino": "",
            "outCodSerieAno": "",
            "outTurma": "",
            "outCodTurno": "",
            "outDescricaoTurno": "",
            "outCodHabilitacao": "",
            "outNumSala": "",
            "outHorarioInicio": "",
            "outHorarioFim": "",
            "outCodTipoClasse": "",
            "outDescTipoClasse": "",
            "outSemestre": "",
            "outQtdAtual": "",
            "outQtdDigitados": "",
            "outQtdEvadidos": "",
            "outQtdNCom": "",
            "outQtdOutros": "",
            "outQtdTransferidos": "",
            "outQtdRemanejados": "",
            "outQtdCessados": "",
            "outQtdReclassificados": "",
            "outCapacidadeFisicaMax": ""
        }
    ],
    "outErro": "",
    "outProcessoID": ""
}
```

---

## Codigos de Erro

| Status | Descricao |
|---|---|
| 200 | Requisicao processada com sucesso: Retorno de dados |
| 200 | Requisicao processada com sucesso: Erro de negocio, outErro preenchido |
| 401 | Requisicao rejeitada: Token invalido ou expirado |
| 500 | Erro de infraestrutura: outErro preenchido |

---

## Observacoes

- Os parametros de entrada podem ser enviados via BODY ou QUERY Parameters.
- Os campos inCodTipoEnsino e outCodTipoEnsino foram alterados de alfanumerico (2) para alfanumerico (3) na versao 1.3.
- O parametro inSemestre, quando nao informado, retorna classes independente da duracao.
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
