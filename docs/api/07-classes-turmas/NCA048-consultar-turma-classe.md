# NCA048 - Consultar Turma Classe

> **Versao:** 1.2 | **Ultima atualizacao:** 31/08/2026 | **Autor:** Flavio L. / Italo Galetti

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | ConsultaTurmaClasse |
| **Codigo** | NCA048 |
| **Descricao** | A finalidade desse servico e a visualizacao dos dados de uma classe coletada. Dados como: turno, horas inicial e final, tipo de ensino, habilitacao, serie, turma, capacidade fisica, numero da sala, inicio e fim aula e dias da semana, atividades cadastradas, etc., serao os parametros de saida do servico. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/TurmaClasse/ConsultaTurmaClasse` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/TurmaClasse/ConsultaTurmaClasse` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inAnoLetivo | Alfanumerico (04) | Obrigatorio | Ano letivo ao qual a classe pertence |
| inNumClasse | Alfanumerico (09) | Obrigatorio | Numero da classe a ser consultada |

---

## Exemplo de Request

**Query Parameters:**

```
/TurmaClasse/ConsultaTurmaClasse?inAnoLetivo=2023&inNumClasse=272323593
```

---

## Parametros de Saida

### Dados da Classe

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outAnoLetivo | Alfanumerico | Ano Letivo |
| outCodSituacao | Numerico | 0 - Ativo / 99 - Excluido |
| outCodEscola | Alfanumerico | Codigo da Escola |
| outNomeEscola | Alfanumerico | Nome da Escola |
| outCodUnidade | Alfanumerico | Codigo da Unidade |
| outCodTurmaClasse | Alfanumerico | Codigo da Turma |
| outCodTipoClasse | Alfanumerico | Codigo do Tipo de Classe |
| outCodTurno | Alfanumerico | Codigo do Turno |
| outDescricaoTurno | Alfanumerico | Descricao do Turno |
| outTurma | Alfanumerico | Codigo da Turma |
| outDescricaoTurma | Alfanumerico | Descricao da Turma |
| outNrCapacidadeFisicaMaxima | Numerico | Capacidade fisica maxima da sala |
| outNrAlunosAtivos | Numerico | Quantidade de alunos ativos |
| outDataInicioAula | dd/mm/aaaa | Data inicio aula |
| outDataFimAula | dd/mm/aaaa | Data final aula |
| outHorarioInicioAula | hh:mm | Horario inicio aula |
| outHorarioFimAula | hh:mm | Horario fim aula |
| outCodDuracao | Numerico | Codigo de duracao |
| outCodHabilitacao | Numerico | Codigo de Habilitacao |
| outCodTipoHabilitacao | Numerico | Tipo do Codigo de Habilitacao |
| outAtividadesComplementar | Numerico | Codigo Atividade Complementar |
| outCodTipoEnsino | Numerico | Codigo do Tipo de Ensino |
| outNomeTipoEnsino | Alfanumerico | Descricao do Tipo de Ensino |
| outNumeroSala | Alfanumerico | Numero da Sala |
| outCodSerieAno | Numerico | Codigo Serie/Ano |
| outDescricaoSerieAno | Alfanumerico | Descricao Serie/Ano |

### Grupo outDiasSemana (dias da semana)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outDiasSemana | Lista | Grupo de Dias da Semana |
| outFlagSegunda | Boolean | Indica se tem aula |
| outHoraIniAulaSegunda | hh:mm | Hora inicio aula |
| outHoraFimAulaSegunda | hh:mm | Hora fim aula |
| outFlagTerca | Boolean | Indica se tem aula |
| outHoraIniAulaTerca | hh:mm | Hora inicio aula |
| outHoraFimAulaTerca | hh:mm | Hora fim aula |
| outFlagQuarta | Boolean | Indica se tem aula |
| outHoraIniAulaQuarta | hh:mm | Hora inicio aula |
| outHoraFimAulaQuarta | hh:mm | Hora fim aula |
| outFlagQuinta | Boolean | Indica se tem aula |
| outHoraIniAulaQuinta | hh:mm | Hora inicio aula |
| outHoraFimAulaQuinta | hh:mm | Hora fim aula |
| outFlagSexta | Boolean | Indica se tem aula |
| outHoraIniAulaSexta | hh:mm | Hora inicio aula |
| outHoraFimAulaSexta | hh:mm | Hora fim aula |
| outFlagSabado | Boolean | Indica se tem aula |
| outHoraIniAulaSabado | hh:mm | Hora inicio aula |
| outHoraFimAulaSabado | hh:mm | Hora fim aula |
| outFlagDomingo | Boolean | Indica se tem aula |
| outHoraIniAulaDomingo | hh:mm | Hora inicio aula |
| outHoraFimAulaDomingo | hh:mm | Hora fim aula |

### Outros parametros de saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outSucesso | Alfanumerico | Sucesso |
| outErro | Alfanumerico | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Alfanumerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outAnoLetivo": 2023,
    "outCodSituacao": 0,
    "outCodEscola": 280768,
    "outNomeEscola": "ELZA MARIA DE SOUZA FAVA FIGUEIRA PROFESSORA CEMEI",
    "outCodUnidade": 15468,
    "outCodTurmaClasse": 38703159,
    "outCodTipoClasse": 0,
    "outCodTurno": 6,
    "outDescricaoTurno": "INTEGRAL",
    "outTurma": "C",
    "outDescricaoTurma": "MATERNAL 2 C INTEGRAL ANUAL",
    "outNrCapacidadeFisicaMaxima": 25,
    "outNrAlunosAtivos": 21,
    "outDataInicioAula": "31/01/2023",
    "outDataFimAula": "20/12/2023",
    "outHorarioInicioAula": "08:30",
    "outHorarioFimAula": "17:30",
    "outCodDuracao": 0,
    "outCodHabilitacao": 0,
    "outCodTipoHabilitacao": 0,
    "outAtividadesComplementar": [],
    "outCodTipoEnsino": 6,
    "outNomeTipoEnsino": "EDUCACAO INFANTIL",
    "outNumeroSala": "008",
    "outCodSerieAno": 7,
    "outDescricaoSerieAno": "MATERNAL 2",
    "outDiasSemana": {
        "outFlagSegunda": true,
        "outHoraIniAulaSegunda": "08:30",
        "outHoraFimAulaSegunda": "17:30",
        "outFlagTerca": true,
        "outHoraIniAulaTerca": "08:30",
        "outHoraFimAulaTerca": "17:30",
        "outFlagQuarta": true,
        "outHoraIniAulaQuarta": "08:30",
        "outHoraFimAulaQuarta": "17:30",
        "outFlagQuinta": true,
        "outHoraIniAulaQuinta": "08:30",
        "outHoraFimAulaQuinta": "17:30",
        "outFlagSexta": true,
        "outHoraIniAulaSexta": "08:30",
        "outHoraFimAulaSexta": "17:30",
        "outFlagSabado": false,
        "outHoraIniAulaSabado": "08:30",
        "outHoraFimAulaSabado": "17:30",
        "outFlagDomingo": false,
        "outHoraIniAulaDomingo": "08:30",
        "outHoraFimAulaDomingo": "17:30"
    },
    "outProcessoID": "428029625"
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

- O campo outCodSituacao foi incluido na versao 1.1, com valores: 0 - Ativo, 99 - Excluido.
- O campo outCodTipoHabilitacao (tipo do codigo de habilitacao) foi incluido na versao 1.2 (31/08/2026).
- Este metodo retorna todos os dados de configuracao de uma turma/classe, incluindo dias da semana e horarios detalhados.
- Os parametros de entrada devem ser enviados via QUERY Parameters.
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
