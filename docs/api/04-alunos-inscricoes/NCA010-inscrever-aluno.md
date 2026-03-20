# NCA010 - Inscrever Aluno

> Esse metodo tem como finalidade a criacao de inscricoes para alunos que estejam fora da rede publica, atendendo os criterios do processo da matricula antecipada.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA010 |
| **Metodo HTTP** | POST |
| **URL** | `/Inscricao/InscreverAluno` |
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
| inInscricao | Alfanumerico | Sim | Grupo de dados base da inscricao |
| inInscricao.inAnoLetivo | Alfanumerico (4) | Sim | Ano letivo da inscricao |
| inInscricao.inCodEscola | Alfanumerico (7) | Sim | Codigo CIE da escola de inscricao |
| inInscricao.inCodUnidade | Alfanumerico (8) | Condicional | Codigo da unidade da escola de inscricao. Torna-se obrigatorio caso a escola pertenca a rede Estadual ou possua mais de uma unidade ativa |
| inInscricao.inFase | Alfanumerico (1) | Sim | Tipo da inscricao: 4 - Inscricao de Aluno Fora da Rede Publica (Ensino Fundamental), 7 - Inscricao de Aluno Fora da Rede Publica (Ensino Medio) |
| inInscricao.inInteresseIntegral | Alfanumerico (1) | Nao | Indica interesse em uma futura matricula no turno integral. Preencher com "1" caso haja interesse |
| inInscricao.inInteresseEspanhol | Alfanumerico (1) | Nao | Indica interesse em uma futura matricula com o curso de espanhol (Exclusivo para a rede Estadual). Preencher com "1" caso haja interesse |
| inInscricao.inNecesAtendNoturno | Alfanumerico (1) | Nao | Indica necessidade em uma futura matricula no periodo noturno (Exclusivo para a rede Estadual). Preencher com "1" caso haja interesse |
| inInscricao.inInteresseNovoTec | Alfanumerico (1) | Nao | Indica interesse no programa Novotec (Exclusivo para o ensino medio da rede Estadual). Preencher com "1" caso haja interesse |
| inInscricao.inCodigoObservacaoOpcaoNoturno | Alfanumerico (1) | Nao | Justificativa para necessidade de matricula no periodo noturno (ver tabela Opcao Noturno) |
| inInscricao.inCodigoEixoNovotecOpcaoUm | Alfanumerico (1) | Nao | Opcao um de curso Novotec (ver tabela Cursos Novotec) |
| inInscricao.inCodigoEscolaNovotecOpcaoUm | Alfanumerico (7) | Nao | Codigo CIE da escola NovoTec OpcaoUm |
| inInscricao.inCodigoUnidadeNovotecOpcaoUm | Alfanumerico (8) | Nao | Codigo da unidade da escola NovoTec OpcaoUm |
| inInscricao.inFl_InteresseCentroIdiomas | Alfanumerico (1) | Nao | Interesse centro de idiomas: 1 = sim, 0 = nao |
| inInscricao.inFl_AceiteEscolaPEIDistante | Alfanumerico (1) | Nao | Aceite Escola PEI distante: 1 = sim, 0 = nao |
| inInscricao.inCodigoEixoCELOpcaoUm | Alfanumerico (1) | Nao | Opcao de um de curso CEL |
| inInscricao.inCodigoEscolaCELOpcaoUm | Alfanumerico (7) | Nao | Codigo CIE da escola CEL OpcaoUm |
| inInscricao.inCodigoUnidadeCELOpcaoUm | Alfanumerico (8) | Nao | Codigo da unidade da escola CEL OpcaoUm |
| inInscricao.inCodigoEixoNovotecOpcaoDois | Alfanumerico (1) | Nao | Opcao dois de curso Novotec (ver tabela Cursos Novotec) |
| inInscricao.inCodigoEixoNovotecOpcaoTres | Alfanumerico (1) | Nao | Opcao tres de curso Novotec (ver tabela Cursos Novotec) |
| inNivelEnsino | Alfanumerico | Sim | Grupo de indicacao no nivel de ensino da inscricao |
| inNivelEnsino.inCodTipoEnsino | Alfanumerico (3) | Sim | Codigo do tipo de ensino pretendido (ver tabela Tipo de Ensino) |
| inNivelEnsino.inCodSerieAno | Alfanumerico (2) | Sim | Codigo da Serie ou Ano pretendido (ver tabela Tipo de Ensino) |

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
    "inCodUnidade": "",
    "inFase": "",
    "inInteresseIntegral": "",
    "inInteresseEspanhol": "",
    "inNecesAtendNoturno": "",
    "inInteresseNovoTec": "",
    "inCodigoObservacaoOpcaoNoturno": "",
    "inCodigoEixoNovotecOpcaoUm": "",
    "inCodigoEscolaNovotecOpcaoUm": "",
    "inCodigoUnidadeNovotecOpcaoUm": "",
    "inFl_InteresseCentroIdiomas": "",
    "inFl_AceiteEscolaPEIDistante": "",
    "inCodigoEixoCELOpcaoUm": "",
    "inCodigoEscolaCELOpcaoUm": "",
    "inCodigoUnidadeCELOpcaoUm": "",
    "inCodigoEixoNovotecOpcaoDois": "",
    "inCodigoEixoNovotecOpcaoTres": ""
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

## Tabelas de Referencia

### Tipo de Ensino e Serie/Ano/Termo

| Codigo Tipo Ensino | Descricao | Codigo Serie/Ano | Descricao | Duracao |
|--------------------|-----------|-------------------|-----------|---------|
| 2 | ENSINO MEDIO | 1 | 1a Serie | Anual |
| 2 | ENSINO MEDIO | 2 | 2a Serie | Anual |
| 2 | ENSINO MEDIO | 3 | 3a Serie | Anual |
| 3 | EJA FUNDAMENTAL - ANOS INICIAIS | 1 | 1o Termo | Semestral |
| 3 | EJA FUNDAMENTAL - ANOS INICIAIS | 2 | 2o Termo | Semestral |
| 3 | EJA FUNDAMENTAL - ANOS INICIAIS | 3 | 3o Termo | Semestral |
| 3 | EJA FUNDAMENTAL - ANOS INICIAIS | 4 | 4o Termo | Semestral |
| 3 | EJA FUNDAMENTAL - ANOS INICIAIS | 9 | 1o Termo | Anual |
| 3 | EJA FUNDAMENTAL - ANOS INICIAIS | 10 | 2o Termo | Anual |
| 4 | EJA FUNDAMENTAL - ANOS FINAIS | 9 | 1o Termo | Semestral |
| 4 | EJA FUNDAMENTAL - ANOS FINAIS | 10 | 2o Termo | Semestral |
| 4 | EJA FUNDAMENTAL - ANOS FINAIS | 11 | 3o Termo | Semestral |
| 4 | EJA FUNDAMENTAL - ANOS FINAIS | 12 | 4o Termo | Semestral |
| 5 | EJA ENSINO MEDIO | 9 | 1o Termo | Semestral |
| 5 | EJA ENSINO MEDIO | 10 | 2o Termo | Semestral |
| 5 | EJA ENSINO MEDIO | 11 | 3o Termo | Semestral |
| 14 | ENSINO FUNDAMENTAL DE 9 ANOS | 1 | 1o Ano | Anual |
| 14 | ENSINO FUNDAMENTAL DE 9 ANOS | 2 | 2o Ano | Anual |
| 14 | ENSINO FUNDAMENTAL DE 9 ANOS | 3 | 3o Ano | Anual |
| 14 | ENSINO FUNDAMENTAL DE 9 ANOS | 4 | 4o Ano | Anual |
| 14 | ENSINO FUNDAMENTAL DE 9 ANOS | 5 | 5o Ano | Anual |
| 14 | ENSINO FUNDAMENTAL DE 9 ANOS | 6 | 6o Ano | Anual |
| 14 | ENSINO FUNDAMENTAL DE 9 ANOS | 7 | 7o Ano | Anual |
| 14 | ENSINO FUNDAMENTAL DE 9 ANOS | 8 | 8o Ano | Anual |
| 14 | ENSINO FUNDAMENTAL DE 9 ANOS | 9 | 9o Ano | Anual |

Esses dados poderao ser obtidos em: `/api/DadosBasicos/TipoEnsino`

### Opcao Noturno

| Codigo | Justificativa |
|--------|---------------|
| 1 | Trabalho |
| 2 | Cursos em periodo diurno |
| 3 | Opcao do aluno |
| 4 | Outros |

Esses dados poderao ser obtidos em: `/api/DadosBasicos/TabelasDominio [OpcaoNoturno]`

### Cursos Novotec

| Codigo | Curso |
|--------|-------|
| 1 | Administracao |
| 2 | Logistica |
| 3 | Marketing |
| 4 | Recursos Humanos |
| 5 | Informatica |
| 6 | Informatica para Internet |
| 7 | Redes de Computadores |
| 8 | Desenvolvimento de Sistemas |

Esses dados poderao ser obtidos em: `/api/DadosBasicos/EixoNovotec`

## Observacoes

- Este metodo e exclusivo para inscricoes de alunos que estejam fora da rede publica
- O campo inFase aceita apenas os valores 4 (Ensino Fundamental) e 7 (Ensino Medio)
- O campo inCodUnidade torna-se obrigatorio caso a escola pertenca a rede Estadual ou possua mais de uma unidade ativa
- Os campos relacionados ao Novotec sao exclusivos para o ensino medio da rede Estadual
- O campo inInteresseEspanhol e exclusivo para a rede Estadual
- O campo inNecesAtendNoturno e exclusivo para a rede Estadual
- O token de acesso e gerado pelo metodo ValidarUsuario e tem um tempo de expiracao de 30 minutos
