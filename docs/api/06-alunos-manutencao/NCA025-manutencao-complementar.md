# NCA025 - Manutencao de Inscricoes

> **Versao:** 1.2 | **Ultima atualizacao:** 27/02/2023 | **Autor:** Alexandre Mendes / Flavio J. Leamari / Italo Galetti

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | Manutencao (Inscricao) |
| **Codigo** | NCA025 |
| **Descricao** | Esse metodo tem como finalidade a manutencao de inscricoes, definicoes e transferencias ainda nao atendidas, seguindo os criterios do processo da matricula antecipada. |
| **Metodo HTTP** | POST |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Inscricao/Manutencao` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Inscricao/Manutencao` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY

### Grupo inAluno (identificador do aluno)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inAluno | Alfanumerico | Obrigatorio | Grupo de dados identificador do aluno |
| inNumRA | Alfanumerico (12) | Obrigatorio | Numero do RA |
| inDigitoRA | Alfanumerico (2) | Opcional | Digito do RA |
| inSiglaUFRA | Alfanumerico (2) | Obrigatorio | UF do RA |

### Grupo inInscricao (dados base da inscricao)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inInscricao | Alfanumerico | Obrigatorio | Grupo de dados base da inscricao |
| inAnoLetivo | Alfanumerico (4) | Obrigatorio | Ano letivo da inscricao |
| inCodEscola | Alfanumerico (7) | Obrigatorio | Codigo CIE da escola de inscricao |
| inFase | Alfanumerico (1) | Obrigatorio | Codigo identificador da fase de inscricao no processo da matricula antecipada (ver tabela item 2.1) |
| inInteresseIntegral | Alfanumerico (1) | Opcional | Indica interesse em futura matricula no turno integral. Preencher com "1" caso haja interesse. |
| inFl_AceiteEscolaPEIDistante | Alfanumerico (1) | Opcional | Aceite Escola PEI distante: 1 = sim, 0 = nao |
| inInteresseEspanhol | Alfanumerico (1) | Opcional | Indica interesse em futura matricula com o curso de espanhol (Exclusivo para a rede Estadual). Preencher com "1" caso haja interesse. |
| inNecesAtendNoturno | Alfanumerico (1) | Opcional | Indica necessidade em futura matricula no periodo noturno (Exclusivo para a rede Estadual). Preencher com "1" caso haja interesse. |
| inInteresseNovoTec | Alfanumerico (1) | Opcional | Indica interesse no programa Novotec (Exclusivo para o ensino medio da rede Estadual). Preencher com "1" caso haja interesse. |
| inCodigoObservacaoOpcaoNoturno | Alfanumerico (1) | Opcional | Justificativa para necessidade de matricula no periodo noturno (ver tabela item 2.3) |
| inCodigoEixoNovotecOpcaoUm | Alfanumerico (1) | Opcional | Opcao um de curso Novotec (ver tabela item 2.4) |
| inCodigoEixoNovotecOpcaoDois | Alfanumerico (1) | Opcional | Opcao dois de curso Novotec (ver tabela item 2.4) |
| inCodigoEixoNovotecOpcaoTres | Alfanumerico (1) | Opcional | Opcao tres de curso Novotec (ver tabela item 2.4) |

### Grupo inNivelEnsino (indicacao do nivel de ensino)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inNivelEnsino | Alfanumerico | Obrigatorio | Grupo de indicacao no nivel de ensino da inscricao |
| inCodTipoEnsino | Alfanumerico (3) | Obrigatorio | Codigo do tipo de ensino pretendido (ver tabela item 2.2) |
| inCodSerieAno | Alfanumerico (2) | Obrigatorio | Codigo da Serie ou Ano pretendido (ver tabela item 2.1) |

---

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
  "inInscricao": {
    "inAnoLetivo": "",
    "inCodEscola": "",
    "inFase": "",
    "inInteresseIntegral": "",
    "inFl_AceiteEscolaPEIDistante": "",
    "inInteresseEspanhol": "",
    "inNecesAtendNoturno": "",
    "inInteresseNovoTec": "",
    "inCodigoObservacaoOpcaoNoturno": "",
    "inCodigoEixoNovotecOpcaoUm": "",
    "inCodigoEixoNovotecOpcaoDois": "",
    "inCodigoEixoNovotecOpcaoTres": ""
  },
  "inNivelEnsino": {
    "inCodTipoEnsino": "",
    "inCodSerieAno": ""
  }
}
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a inscricao seja efetivada |
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

### 2.1 - Fase de Inscricao

Dados disponiveis em:
- `/api/DadosBasicos/TabelasDominio` [outFaseInscricao]
- `/api/DadosBasicos/TabelasDominio` [outFaseDefinicao]
- `/api/DadosBasicos/TabelasDominio` [outFaseMovimentacao]

| Codigo | Descricao |
|---|---|
| 0 | Inscricao por Transferencia |
| 1 | Definicao de alunos para 1o ano do ensino fundamental |
| 2 | Definicao de alunos para 6o ano do Ensino Fundamental |
| 4 | Inscricao de aluno de fora da rede publica para o Ensino Fundamental |
| 6 | Definicao de alunos para 1a serie do Ensino Medio |
| 7 | Inscricao de aluno de fora da rede publica para o Ensino Medio |
| 8 | Inscricao por Deslocamento |
| 9 | Intencao de Transferencia |

### 2.2 - Tipo de Ensino e Serie/Ano/Termo

Dados disponiveis em: `/api/DadosBasicos/TipoEnsino`

### 2.3 - Opcao Noturno

Dados disponiveis em: `/api/DadosBasicos/TabelasDominio` [OpcaoNoturno]

| Codigo | Justificativa |
|---|---|
| 1 | Trabalho |
| 2 | Cursos em periodo diurno |
| 3 | Opcao do aluno |
| 4 | Outros |

### 2.4 - Cursos Novotec

Dados disponiveis em: `/api/DadosBasicos/EixoNovotec`

| Codigo | Curso |
|---|---|
| 1 | Administracao |
| 2 | Logistica |
| 3 | Marketing |
| 4 | Recursos Humanos |
| 5 | Informatica |
| 6 | Informatica para Internet |
| 7 | Redes de Computadores |
| 8 | Desenvolvimento de Sistemas |

---

## Observacoes

- Este metodo e utilizado para manutencao de inscricoes do processo de matricula antecipada.
- O campo inCodTipoEnsino foi alterado de alfanumerico (2) para alfanumerico (3) na versao 1.2.
- O campo inFl_AceiteEscolaPEIDistante foi incluido na versao 1.1.
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
