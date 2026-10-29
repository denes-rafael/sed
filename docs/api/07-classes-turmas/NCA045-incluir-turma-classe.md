# NCA045 - Incluir Turma Classe

> **Versao:** 1.7 | **Ultima atualizacao:** 31/08/2026 | **Autor:** Alexandre M. / Flavio Leamari / Italo G.

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | IncluirTurmaClasse |
| **Codigo** | NCA045 |
| **Descricao** | Esse metodo tem como finalidade a criacao de turmas (classes) seguindo as regras existentes no Sistema Cadastro de Alunos. |
| **Metodo HTTP** | POST |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/TurmaClasse/IncluirTurmaClasse` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/TurmaClasse/IncluirTurmaClasse` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY

### Parametros principais

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inAnoLetivo | Alfanumerico (04) | Obrigatorio | Ano Letivo da Turma |
| inCodEscola | Alfanumerico (07) | Obrigatorio | Codigo CIE da escola |
| inCodUnidade | Alfanumerico (08) | Opcional; obrigatorio quando a escola possui mais de uma unidade | Codigo da Unidade Escolar |
| inCodTipoEnsino | Alfanumerico (03) | Opcional, dependendo do tipo de ensino da classe | Obtidos via /DadosBasicos/TipoEnsino |
| inCodSerieAno | Alfanumerico (02) | Opcional, dependendo do tipo de ensino | Serie / Ano / Termo do Tipo de Ensino. Obtidos via /DadosBasicos/TipoEnsino |
| inCodTipoClasse | Alfanumerico (03) | Opcional, dependendo do tipo de ensino | Tipo da Classe (ver tabela 2.1) |
| inCodTurno | Alfanumerico (01) | Obrigatorio | Turno de funcionamento da classe. Obtidos via /DadosBasicos/TabelasDominio |
| inTurma | Alfanumerico (02) | Obrigatorio | Turma (Ex. A, B, 1, 2, A1, B1) |
| inNrCapacidadeFisicaMaxima | Alfanumerico (02) | Obrigatorio | Quantidade maxima permitida de alunos na sala |
| inNumeroSala | Alfanumerico (03) | Opcional, dependendo do tipo de ensino | Numero da sala, com base no cadastro de dependencias da unidade escolar |
| inDataInicioAula | Alfanumerico (10) | Obrigatorio | Dia inicio da Aula (DD/MM/AAAA) |
| inDataFimAula | Alfanumerico (10) | Obrigatorio | Dia fim da Aula (DD/MM/AAAA) |
| inHorarioInicioAula | Alfanumerico (05) | Obrigatorio | Horario de inicio da turma (hh:mm) |
| inHorarioFimAula | Alfanumerico (05) | Obrigatorio | Horario de fim da turma (hh:mm) |
| inCodDuracao | Alfanumerico (01) | Obrigatorio | Periodo de funcionamento: 0 - Anual, 1 - Primeiro Semestre, 2 - Segundo Semestre |
| inCodHabilitacao | Alfanumerico (06) | Opcional; obrigatorio caso tipo de ensino seja educacao profissional | Codigo de habilitacao (INEP / MEC) |
| inCodTipoHabilitacao | Alfanumerico (02) | Opcional; obrigatorio quando existir mais de um tipo para o mesmo inCodHabilitacao | Tipo do Codigo de Habilitacao (INEP / MEC). Obtido via /DadosBasicos/HabilitacaoPorEscolaNEM |
| inCodigoAtividadeComplementar | Alfanumerico | Opcional; dependendo do tipo de ensino | Array com codigos das atividades oferecidas na turma. Obtidos via /TipoEnsino/ConsultaTipoEnsinoAtividadeComplementar |

### Grupo inDiasDaSemana (dias e horarios de funcionamento)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDiasDaSemana | Alfanumerico | Obrigatorio | Grupo de dados com os dias e horarios de funcionamento da turma |
| inFlagSegunda | Alfanumerico (01) | Opcional | Funcionamento as segundas-feiras. Informar fixo "1" |
| inHoraIniAulaSegunda | Alfanumerico (05) | Obrigatorio se inFlagSegunda informado | Hora do inicio da aula (hh:mm) |
| inHoraFimAulaSegunda | Alfanumerico (05) | Obrigatorio se inFlagSegunda informado | Hora do fim da aula (hh:mm) |
| inFlagTerca | Alfanumerico (01) | Opcional | Funcionamento as tercas-feiras. Informar fixo "2" |
| inHoraIniAulaTerca | Alfanumerico (05) | Obrigatorio se inFlagTerca informado | Hora do inicio da aula (hh:mm) |
| inHoraFimAulaTerca | Alfanumerico (05) | Obrigatorio se inFlagTerca informado | Hora do fim da aula (hh:mm) |
| inFlagQuarta | Alfanumerico (01) | Opcional | Funcionamento as quartas-feiras. Informar fixo "3" |
| inHoraIniAulaQuarta | Alfanumerico (05) | Obrigatorio se inFlagQuarta informado | Hora do inicio da aula (hh:mm) |
| inHoraFimAulaQuarta | Alfanumerico (05) | Obrigatorio se inFlagQuarta informado | Hora do fim da aula (hh:mm) |
| inFlagQuinta | Alfanumerico (01) | Opcional | Funcionamento as quintas-feiras. Informar fixo "4" |
| inHoraIniAulaQuinta | Alfanumerico (05) | Obrigatorio se inFlagQuinta informado | Hora do inicio da aula (hh:mm) |
| inHoraFimAulaQuinta | Alfanumerico (05) | Obrigatorio se inFlagQuinta informado | Hora do fim da aula (hh:mm) |
| inFlagSexta | Alfanumerico (01) | Opcional | Funcionamento as sextas-feiras. Informar fixo "5" |
| inHoraIniAulaSexta | Alfanumerico (05) | Obrigatorio se inFlagSexta informado | Hora do inicio da aula (hh:mm) |
| inHoraFimAulaSexta | Alfanumerico (05) | Obrigatorio se inFlagSexta informado | Hora do fim da aula (hh:mm) |
| inFlagSabado | Alfanumerico (01) | Opcional | Funcionamento aos sabados. Informar fixo "6" |
| inHoraIniAulaSabado | Alfanumerico (05) | Obrigatorio se inFlagSabado informado | Hora do inicio da aula (hh:mm) |
| inHoraFimAulaSabado | Alfanumerico (05) | Obrigatorio se inFlagSabado informado | Hora do fim da aula (hh:mm) |

### Grupo inAreasConhecimentos (para tipos de ensino 101 e 109)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inAreasConhecimentos | Alfanumerico | Opcional; obrigatorio se inCodTipoEnsino = 101 ou 109 | Areas de Conhecimento |
| CodigoAreaConhecimento | Numerico | Obrigatorio | Codigo da area do conhecimento. Obtidos via /DadosBasicos/AreasItinerarioFormativo (GET, passando inRedeEnsino) |
| CodigoEscola | Alfanumerico (07) | Opcional | Codigo CIE da escola |
| FlagIntegrado | Boolean | Opcional | Informa se a area do conhecimento e integrada ou nao |
| NomeAreaConhecimento | Alfanumerico | Opcional | Obtido via /DadosBasicos/AreasItinerarioFormativo |
| FlagColetaIntegrada | Boolean | Opcional | Informa se a coleta informada e integrada ou nao |

### Campos adicionais (fora do grupo inAreasConhecimentos)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCodTipoCurso | Numerico | Opcional | Obtido via /DadosBasicos/TipoCursoItinerarioFormativo |
| inCodHabilitacaoSED | Alfanumerico | Opcional | Obtido via /DadosBasicos/HabilitacaoPorEscolaNEM |

---

## Exemplo de Request

```json
{
  "inAnoLetivo": "",
  "inCodEscola": "",
  "inCodUnidade": "",
  "inCodTipoEnsino": "",
  "inCodSerieAno": "",
  "inCodTipoClasse": "",
  "inCodTurno": "",
  "inCodDuracao": "",
  "inTurma": "",
  "inNumeroSala": "",
  "inNrCapacidadeFisicaMaxima": "",
  "inDataInicioAula": "",
  "inDataFimAula": "",
  "inHorarioInicioAula": "",
  "inHorarioFimAula": "",
  "inCodHabilitacao": "",
  "inCodTipoHabilitacao": "",
  "inCodigoAtividadeComplementar": [""],
  "inDiasDaSemana": {
    "inFlagSegunda": "",
    "inHoraIniAulaSegunda": "",
    "inHoraFimAulaSegunda": "",
    "inFlagTerca": "",
    "inHoraIniAulaTerca": "",
    "inHoraFimAulaTerca": "",
    "inFlagQuarta": "",
    "inHoraIniAulaQuarta": "",
    "inHoraFimAulaQuarta": "",
    "inFlagQuinta": "",
    "inHoraIniAulaQuinta": "",
    "inHoraFimAulaQuinta": "",
    "inFlagSexta": "",
    "inHoraIniAulaSexta": "",
    "inHoraFimAulaSexta": "",
    "inFlagSabado": "",
    "inHoraIniAulaSabado": "",
    "inHoraFimAulaSabado": ""
  },
  "inAreasConhecimentos": [
    {
      "CodigoAreaConhecimento": "",
      "CodigoEscola": "",
      "FlagIntegrado": "",
      "NomeAreaConhecimento": "",
      "FlagColetaIntegrada": ""
    }
  ],
  "inCodTipoCurso": "",
  "inCodHabilitacaoSED": ""
}
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outListaCandidatos | Alfanumerico | Grupo de certificados do candidato no formato ARRAY [1 : N] (consta na tabela de saida do PDF oficial, mas nao aparece no exemplo de retorno; conferir no PDF) |
| outSucesso | Alfanumerico (09) | Numero da classe recem criada |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outSucesso": "",
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

## Tabelas de Apoio

### 2.1 - Tipo de Classe

| Tipo | Descricao | Abreviacao |
|---|---|---|
| 0 | PADRAO | PA |
| 1 | MULTISSERIADA | MU |
| 2 | PRESENCA FLEXIVEL - SEMI PRESENCIAL | SM |
| 3 | ACELERACAO | AC |
| 4 | FLEXIBILIZADA | FL |
| 5 | RECUPERACAO DE CICLO | RC |
| 6 | SALA DE RECURSO | SR |
| 7 | PROGRAMA PROFISSAO | PP |
| 8 | CONVENIADA (APAE) | CO |
| 9 | RECUPERACAO DE CICLO MISTA | RM |
| 10 | PIC PROJETO INTENSIVO NO CICLO | PIC |
| 11 | ITINERANTE | ITI |
| 12 | TELETEC 1 | TL1 |
| 13 | TELETEC 2 | TL2 |
| 14 | TELECURSO PRESENCIAL | TPR |
| 15 | MULTIFUNCIONAL | MF |
| 16 | EDUCACAO PROFISSIONAL AOS SABADOS | EPS |
| 17 | ENSINO INTEGRAL | EI |

### Rotinas de Apoio

| API | Descricao | Metodo |
|---|---|---|
| /DadosBasicos/AreasItinerarioFormativo | Consulta Areas Itinerarios | GET (passando inRedeEnsino) |
| /DadosBasicos/TipoCursoItinerarioFormativo | Consulta Tipo de Curso | GET |
| /DadosBasicos/HabilitacaoPorEscolaNEM | Consulta a Habilitacao (retorna outCodHabilitacao, outCodTipoHabilitacao e outNomeHabilitacaoQualificacao) | POST (inCodEscola, inCodUnidade, inCodigoTipoEnsino, inAnoLetivo, inCodTipoClasse) |
| /DadosBasicos/TipoEnsino | Consulta Tipo de Ensino | GET |
| /DadosBasicos/TabelasDominio | Consulta Raca, Nacionalidade, Turno, etc | GET |
| /TipoEnsino/ConsultaTipoEnsinoAtividadeComplementar | Consulta Atividades Complementares | GET (inAnoLetivo, inCodEscola, inCodUnidade) |

---

## Observacoes

- Na versao 1.7 (31/08/2026) foi incluido o campo inCodTipoHabilitacao (Codigo de Tipo de Habilitacao, INEP / MEC), obrigatorio quando existir mais de um tipo para o mesmo inCodHabilitacao. O tipo e obtido em /DadosBasicos/HabilitacaoPorEscolaNEM (campo outCodTipoHabilitacao).
- Na versao 1.6 foi incluido tratamento para os Tipos de Ensino "109" (ITINERARIO FORMATIVO) e "101" (NOVO ENSINO MEDIO), com os campos inAreasConhecimentos, inCodTipoCurso e inCodHabilitacaoSED.
- O campo inDiasSemana foi alterado para inDiasDaSemana na versao 1.1.
- O campo inCodTipoEnsino foi alterado de alfanumerico (2) para alfanumerico (3) na versao 1.5.
- As flags de dias da semana devem conter valores fixos: "1" para segunda, "2" para terca, "3" para quarta, "4" para quinta, "5" para sexta, "6" para sabado.
- Quando uma flag de dia e informada, os horarios de inicio e fim daquele dia tornam-se obrigatorios.
- O campo outSucesso retorna o numero da classe recem criada quando a operacao e bem-sucedida.
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
