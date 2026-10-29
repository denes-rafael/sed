# NCA046 - Manutencao Turma Classe

> **Versao:** 1.4 | **Ultima atualizacao:** 31/08/2026 | **Autor:** Flavio Leamari / Italo Galetti

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | ManutencaoTurmaClasse |
| **Codigo** | NCA046 |
| **Descricao** | Esse metodo tem como finalidade a manutencao de turmas (classes) seguindo as regras existentes no Sistema Cadastro de Alunos. |
| **Metodo HTTP** | POST |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/TurmaClasse/ManutencaoTurmaClasse` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/TurmaClasse/ManutencaoTurmaClasse` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY

### Parametros principais

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inAnoLetivo | Alfanumerico (4) | Obrigatorio | Ano letivo da turma |
| inNumClasse | Alfanumerico (9) | Obrigatorio | Numero da classe |
| inCodEscola | Alfanumerico (7) | Opcional | Codigo CIE da escola |
| inCodUnidade | Alfanumerico (8) | Opcional; obrigatorio quando a escola possui mais de uma unidade | Codigo da Unidade Escolar |
| inCodTipoEnsino | Alfanumerico (3) | Opcional | Tipo de ensino da classe. Obtidos via /DadosBasicos/TipoEnsino |
| inCodSerieAno | Alfanumerico (2) | Opcional, dependendo do tipo de ensino | Serie / Ano / Termo do Tipo de Ensino. Obtidos via /DadosBasicos/TipoEnsino |
| inCodTipoClasse | Alfanumerico (2) | Obrigatorio, dependendo do tipo de ensino | Tipo da Classe. Obtidos via /DadosBasicos/TipoClasse |
| inCodTurno | Alfanumerico (1) | Obrigatorio | Turno de funcionamento da classe. Obtidos via /DadosBasicos/TabelasDominio/{outTurno} |
| inTurma | Alfanumerico (2) | Opcional | Turma (Ex. A, B, 1, 2, A1, B1) |
| inNrCapacidadeFisicaMaxima | Alfanumerico (2) | Obrigatorio | Quantidade maxima permitida de alunos na sala |
| inNumeroSala | Alfanumerico (3) | Obrigatorio (dependendo do tipo de ensino) | Numero da sala, com base no cadastro de dependencias da unidade escolar |
| inDataInicioAula | Alfanumerico (10) | Obrigatorio | Dia inicio da Aula (DD/MM/AAAA) |
| inDataFimAula | Alfanumerico (10) | Obrigatorio | Dia fim da Aula (DD/MM/AAAA) |
| inHorarioInicioAula | Alfanumerico (5) | Obrigatorio | Horario de inicio da turma (hh:mm) |
| inHorarioFimAula | Alfanumerico (5) | Obrigatorio | Horario de termino da turma (hh:mm) |
| inCodDuracao | Alfanumerico (1) | Obrigatorio | Periodo de funcionamento da turma: 0 - Anual, 1 - Primeiro Semestre, 2 - Segundo Semestre |
| inCodHabilitacao | Alfanumerico (6) | Opcional; obrigatorio caso tipo de ensino seja educacao profissional | Codigo de habilitacao (INEP / MEC) |
| inCodTipoHabilitacao | Alfanumerico (6) | Opcional; obrigatorio quando existir mais de um tipo para o mesmo inCodHabilitacao | Codigo do Tipo de habilitacao (INEP / MEC). Obtido via /DadosBasicos/HabilitacaoPorEscolaNEM |
| inCodigoAtividadeComplementar | Alfanumerico | Opcional; dependendo do tipo de ensino | Array com codigos das atividades oferecidas na turma, separados por virgula. Obtidos via /DadosBasicos/AtividadeComplementar |

### Grupo inDiasDaSemana (dias e horarios de funcionamento)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDiasDaSemana | Alfanumerico | Opcional | Grupo de dados com os dias e horarios de funcionamento da turma |
| inFlagSegunda | Alfanumerico (1) | Opcional | Funcionamento as segundas-feiras. Informar fixo "1" |
| inHoraIniAulaSegunda | Alfanumerico (5) | Obrigatorio se inFlagSegunda informado | Hora do inicio da aula as segundas-feiras (hh:mm) |
| inHoraFimAulaSegunda | Alfanumerico (5) | Obrigatorio se inFlagSegunda informado | Hora do final da aula as segundas-feiras (hh:mm) |
| inFlagTerca | Alfanumerico (1) | Opcional | Funcionamento as tercas-feiras. Informar fixo "2" |
| inHoraIniAulaTerca | Alfanumerico (5) | Obrigatorio se inFlagTerca informado | Hora do inicio da aula as tercas-feiras (hh:mm) |
| inHoraFimAulaTerca | Alfanumerico (5) | Obrigatorio se inFlagTerca informado | Hora do final da aula as tercas-feiras (hh:mm) |
| inFlagQuarta | Alfanumerico (1) | Opcional | Funcionamento as quartas-feiras. Informar fixo "3" |
| inHoraIniAulaQuarta | Alfanumerico (5) | Obrigatorio se inFlagQuarta informado | Hora do inicio da aula as quartas-feiras (hh:mm) |
| inHoraFimAulaQuarta | Alfanumerico (5) | Obrigatorio se inFlagQuarta informado | Hora do final da aula as quartas-feiras (hh:mm) |
| inFlagQuinta | Alfanumerico (1) | Opcional | Funcionamento as quintas-feiras. Informar fixo "4" |
| inHoraIniAulaQuinta | Alfanumerico (5) | Obrigatorio se inFlagQuinta informado | Hora do inicio da aula as quintas-feiras (hh:mm) |
| inHoraFimAulaQuinta | Alfanumerico (5) | Obrigatorio se inFlagQuinta informado | Hora do final da aula as quintas-feiras (hh:mm) |
| inFlagSexta | Alfanumerico (1) | Opcional | Funcionamento as sextas-feiras. Informar fixo "5" |
| inHoraIniAulaSexta | Alfanumerico (5) | Obrigatorio se inFlagSexta informado | Hora do inicio da aula as sextas-feiras (hh:mm) |
| inHoraFimAulaSexta | Alfanumerico (5) | Obrigatorio se inFlagSexta informado | Hora do final da aula as sextas-feiras (hh:mm) |
| inFlagSabado | Alfanumerico (1) | Opcional | Funcionamento aos sabados. Informar fixo "6" |
| inHoraIniAulaSabado | Alfanumerico (5) | Obrigatorio se inFlagSabado informado | Hora do inicio da aula aos sabados (hh:mm) |
| inHoraFimAulaSabado | Alfanumerico (5) | Obrigatorio se inFlagSabado informado | Hora do final da aula aos sabados (hh:mm) |

---

## Exemplo de Request

```json
{
  "inAnoLetivo": "",
  "inNumClasse": "",
  "inCodTipoClasse": "",
  "inCodTurno": "",
  "inTurma": "",
  "inNrCapacidadeFisicaMaxima": "",
  "inDataInicioAula": "",
  "inDataFimAula": "",
  "inHorarioInicioAula": "",
  "inHorarioFimAula": "",
  "inCodDuracao": "",
  "inCodHabilitacao": "",
  "inCodTipoHabilitacao": "",
  "inCodigoAtividadeComplementar": [
    "", "", "", "", ""
  ],
  "inNumeroSala": "",
  "inDiasSemana": {
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
    "inHoraFimAulaSexta": ""
  }
}
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outSucesso | Alfanumerico (9) | OK/Erro |
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

## Observacoes

- O campo inDiasSemana foi alterado para inDiasDaSemana na versao 1.1.
- O campo inCodTipoEnsino foi alterado de alfanumerico (2) para alfanumerico (3) na versao 1.3.
- Na versao 1.4 (31/08/2026) foi incluido o campo inCodTipoHabilitacao (Codigo do Tipo de Habilitacao, INEP / MEC), obrigatorio quando existir mais de um tipo para o mesmo inCodHabilitacao. O PDF oficial registra o tamanho como Alfanumerico (6), enquanto o NCA045 1.7 registra Alfanumerico (02) para o mesmo campo; mantido como escrito em cada documento.
- A capa do PDF oficial ainda traz "Versao 1.3"; o historico de revisoes e o cabecalho das paginas trazem 1.4 (31/08/2026).
- As flags de dias da semana devem conter valores fixos: "1" para segunda, "2" para terca, "3" para quarta, "4" para quinta, "5" para sexta, "6" para sabado.
- Quando uma flag de dia e informada, os horarios de inicio e fim daquele dia tornam-se obrigatorios.
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
