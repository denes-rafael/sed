# NCA012 - Transferencia

> Esse metodo tem como finalidade a criacao de inscricoes para transferencia de alunos (inscricao transferencia, intencao transferencia ou deslocamento) entre escolas da rede publica, atendendo os criterios do processo da matricula antecipada.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA012 |
| **Metodo HTTP** | POST |
| **URL** | `/Inscricao/Transferencia` |
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
| inAluno.inEmailAluno | Alfanumerico (100) | Nao | E-mail do Aluno |
| inTransferencia | Alfanumerico | Sim | Grupo de dados base da transferencia |
| inTransferencia.inAnoLetivo | Alfanumerico (4) | Sim | Ano letivo da transferencia |
| inTransferencia.inCodEscola | Alfanumerico (7) | Sim | Codigo CIE da escola de inscricao |
| inTransferencia.inFase | Alfanumerico (1) | Sim | Tipo de transferencia: 0 - Inscricao de Alunos por Transferencia, 8 - Inscricao de Alunos por Deslocamento, 9 - Inscricao por Intencao de Transferencia |
| inTransferencia.inInteresseIntegral | Alfanumerico (1) | Nao | Indica interesse em uma futura matricula no turno integral. Preencher com "1" caso haja interesse |
| inTransferencia.inInteresseEspanhol | Alfanumerico (1) | Nao | Indica interesse em uma futura matricula com o curso de espanhol (Exclusivo para a rede Estadual). Preencher com "1" caso haja interesse |
| inTransferencia.inNecesAtendNoturno | Alfanumerico (1) | Nao | Indica necessidade em uma futura matricula no periodo noturno (Exclusivo para a rede Estadual). Preencher com "1" caso haja interesse |
| inTransferencia.inNumClasseMatriculaAtual | Alfanumerico (9) | Sim | Numero da classe da matricula atual (ativa) |
| inTransferencia.inMotivo | Alfanumerico (1) | Sim | Identifica qual o motivo da mudanca do endereco do aluno por tipo transferencia (ver tabela Motivos) |
| inNivelEnsino | Alfanumerico | Sim | Grupo de indicacao no nivel de ensino da inscricao |
| inNivelEnsino.inCodTipoEnsino | Alfanumerico (3) | Sim | Codigo do tipo de ensino pretendido (ver tabela Tipo de Ensino) |
| inNivelEnsino.inCodSerieAno | Alfanumerico (2) | Sim | Codigo da Serie ou Ano pretendido (ver tabela Tipo de Ensino) |
| inEnderecoResidencial | Alfanumerico | Sim | Grupo do endereco residencial do aluno |
| inEnderecoResidencial.inLogradouro | Alfanumerico (100) | Condicional | Logradouro do endereco residencial. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inNumero | Alfanumerico (10) | Condicional | Numero da residencia. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inAreaLogradouro | Alfanumerico (10) | Condicional | Area do logradouro: 0 - Urbana, 1 - Rural. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inComplemento | Alfanumerico (60) | Condicional | Complemento do endereco residencial. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inBairro | Alfanumerico (60) | Condicional | Nome do bairro da residencia. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inCep | Alfanumerico (8) | Condicional | CEP da residencia. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inNomeCidade | Alfanumerico (60) | Condicional | Nome da localidade da residencia. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inUFCidade | Alfanumerico (2) | Condicional | UF da localidade. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inCodMunicipioDNE | Alfanumerico (4) | Condicional | Codigo DNE (Correios) do municipio do endereco residencial. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inLatitude | Alfanumerico (100) | Condicional | Latitude do endereco residencial. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inLongitude | Alfanumerico (100) | Condicional | Longitude do endereco residencial. Obrigatorio se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inEnderecoResidencial.inCodLocalizacaoDiferenciada | Alfanumerico (1) | Condicional | Localizacao diferenciada do endereco do aluno (ver tabela Localizacao Diferenciada). Opcional se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido |
| inComprovanteBase64 | Alfanumerico | Condicional | Comprovante de Endereco no formato Base64 (Data URI Scheme). Opcional se inFase = 0 e inMotivo = 1; para as demais situacoes nao deve ser preenchido. **Atencao: Este campo nao pertence ao grupo inEnderecoResidencial** |

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": "",
    "inEmailAluno": ""
  },
  "inTransferencia": {
    "inAnoLetivo": "",
    "inCodEscola": "",
    "inFase": "",
    "inInteresseIntegral": "",
    "inInteresseEspanhol": "",
    "NecesAtendNoturno": "",
    "inMotivo": ""
  },
  "inNivelEnsino": {
    "inCodTipoEnsino": "",
    "inCodSerieAno": ""
  },
  "inEnderecoResidencial": {
    "inLogradouro": "",
    "inNumero": "",
    "inBairro": "",
    "inNomeCidade": "",
    "inUFCidade": "",
    "inComplemento": "",
    "inCep": "",
    "inAreaLogradouro": "",
    "inCodLocalizacaoDiferenciada": "",
    "inCodMunicipioDNE": "",
    "inLatitude": "",
    "inLongitude": ""
  },
  "inComprovanteBase64": ""
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

### Motivos por Tipo de Transferencia

**Inscricao de Alunos por Transferencia (inFase = 0):**

| Codigo | Motivo (Ensino e EJA Fundamental) | Motivo (Ensino e EJA Medio) |
|--------|-----------------------------------|----------------------------|
| 1 | Mudanca de Residencia | Mudanca de Residencia |
| 2 | Proximidade local de trabalho dos pais | Proximidade local trabalho e/ou horario trabalho aluno |
| 3 | Endereco dos familiares | - |

**Inscricao de Alunos por Deslocamento (inFase = 8):**

| Codigo | Motivo (Ensino e EJA Fundamental) | Motivo (Ensino e EJA Medio) |
|--------|-----------------------------------|----------------------------|
| 1 | Mudanca de Residencia | Mudanca de Residencia |
| 2 | Proximidade local de trabalho dos pais | Proximidade local trabalho e/ou horario trabalho aluno |
| 3 | Endereco dos familiares | - |
| 4 | - | Interesse do aluno |

**Inscricao por Intencao de Transferencia (inFase = 9):**

| Codigo | Motivo |
|--------|--------|
| 4 | Interesse do aluno |

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

### Localizacao Diferenciada

| Codigo | Descricao |
|--------|-----------|
| 1 | Area de assentamento |
| 2 | Terra indigena |
| 3 | Area onde se localiza comunidade remanescente de quilombos |
| 7 | Nao esta em area de localizacao diferenciada |

Esses dados poderao ser obtidos em: `/api/DadosBasicos/TabelasDominio [outLocalizacaoDiferencada]`

### Referencia - inComprovanteBase64

O campo inComprovanteBase64 segue o padrao "Data URI Scheme", que e uma implementacao do URI (Uniform Resource Identifier). O padrao segue o modelo: `data:content/type;base64,stringBase64`

Exemplo de uma URI contendo uma imagem no formato PNG:
```
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFCAYAAACNbyblAAAAHElEQVQI12P4//8/w38GIAXDIBKE0DHxgljNBAAO9TXL0Y4OHwAAAABJRU5ErkJggg==
```

## Observacoes

- Este metodo e exclusivo para transferencias entre escolas da rede publica
- O campo inFase aceita os valores 0 (Transferencia), 8 (Deslocamento) e 9 (Intencao de Transferencia)
- Os campos de endereco residencial sao obrigatorios apenas quando inFase = 0 e inMotivo = 1 (Mudanca de Residencia); para as demais situacoes nao devem ser preenchidos
- O campo inComprovanteBase64 NAO pertence ao grupo inEnderecoResidencial, deve ser enviado no nivel raiz do JSON
- O campo inInteresseEspanhol e exclusivo para a rede Estadual
- O campo inNecesAtendNoturno e exclusivo para a rede Estadual
- O token de acesso e gerado pelo metodo ValidarUsuario e tem um tempo de expiracao de 30 minutos
