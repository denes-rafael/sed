# NCA016 - Ficha Aluno

> **Versao:** 2.9 | **Ultima atualizacao:** 28/10/2025 | **Autor:** Italo G.

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | FichaAluno |
| **Codigo** | NCA016 |
| **Descricao** | Cadastramento de novos alunos no sistema NCA (criacao da ficha do aluno) com o retorno do RA gerado em caso de sucesso, sendo que o mesmo devera ser utilizado nos demais processos do sistema (consultas, inscricoes, matriculas e movimentacoes). |
| **Metodo HTTP** | POST |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/FichaAluno` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/FichaAluno` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY

### Grupo inDadosPessoais

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDadosPessoais | Alfanumerico | Nao se aplica | Grupo de dados pessoais do aluno |
| inNomeAluno | Alfanumerico (100) | Obrigatorio | Nome completo do aluno |
| inNomeMae | Alfanumerico (100) | Obrigatorio | Nome completo da Mae (Filiacao 01) |
| inNomePai | Alfanumerico (100) | Opcional | Nome completo do Pai (Filiacao 02) |
| inNomeSocial | Alfanumerico (100) | Opcional | Nome social do aluno (item 2.1.5) |
| inNomeAfetivo | Alfanumerico (100) | Opcional | Nome afetivo do aluno (item 2.1.5) |
| inDataNascimento | Alfanumerico (10) | Obrigatorio | Data de Nascimento do aluno (DD/MM/AAAA) |
| inCorRaca | Alfanumerico (2) | Obrigatorio | Codigo da cor ou raca do aluno (item 2.1.1) |
| inSexo | Alfanumerico (1) | Obrigatorio | Identificacao do sexo do aluno: 1 - Masculino / 2 - Feminino |
| inEmail | Alfanumerico (100) | Opcional | Endereco do e-mail do aluno ou do responsavel |
| inNacionalidade | Alfanumerico (1) | Obrigatorio | Codigo identificador da nacionalidade: 1 - Brasileiro, 2 - Estrangeiro, 3 - Brasileiro Nascido no Exterior |
| inNomeMunNascto | Alfanumerico (60) | Opcional. Obrigatorio quando inNacionalidade = 1 | Municipio de nascimento do aluno |
| inUFMunNascto | Alfanumerico (2) | Opcional. Obrigatorio quando inNacionalidade = 1 | UF do municipio de nascimento do aluno |
| inCodPaisOrigem | Alfanumerico (3) | Obrigatorio | Codigo do pais de origem do aluno (item 2.1.2). Caso inNacionalidade = 1, informar: 76 |
| inPaisOrigem | Alfanumerico (60) | Obrigatorio | Nome do pais de origem do aluno (item 2.1.2). Caso inNacionalidade = 1, informar: Brasil |
| inCodMunNasctoDNE | Alfanumerico (4) | Opcional | Codigo DNE (Correios) do municipio de nascimento |
| inDataEntradaPais | Alfanumerico (10) | Opcional. Obrigatorio quando inNacionalidade = 2 | Data de entrada no Brasil (DD/MM/AAAA) |
| inBolsaFamilia | Alfanumerico (1) | Opcional | Indica se o aluno participa do programa Bolsa Familia: 0 - Nao / 1 - Sim |
| inQuilombola | Alfanumerico (1) | Opcional | Indica se o aluno e quilombola: 0 - Nao / 1 - Sim |
| inPossuiInternet | Alfanumerico (1) | Obrigatorio | Indica se o aluno possui internet: N - Nao / S - Sim |
| inPossuiNotebookSmartphoneTablet | Alfanumerico (1) | Obrigatorio | Indica se o aluno possui Notebook/Smartphone/Tablet: N - Nao / S - Sim |
| inTipoSanguineo | Alfanumerico (3) | Opcional | A+, A-, B+, B-, AB+, AB-, O+, O- |
| inDoadorOrgaos | Alfanumerico (3) | Opcional | SIM/NAO |
| inCodTipoIndigena | Alfanumerico (3) | Opcional, obrigatorio se inCorRaca = 5 | Identificacao dos povos indigenas (item 2.1.6) |

### Grupo inDocumentos

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDocumentos | Alfanumerico | Nao se aplica | Grupo de documentos do aluno |
| inCodigoINEP | Alfanumerico (12) | Opcional | Codigo identificador do INEP/MEC |
| inCPF | Alfanumerico (11) | Opcional | Numero do CPF do aluno |
| inNumNIS | Alfanumerico (11) | Opcional | Numero de identificacao social |
| inNumDoctoCivil | Alfanumerico (14) | Opcional | Numero do documento civil do aluno (RG ou RNE) |
| inDigitoDoctoCivil | Alfanumerico (2) | Opcional. Obrigatorio quando o documento civil for o RG >= 24.000.000 e inUFDoctoCivil = SP | Digito do documento civil |
| inUFDoctoCivil | Alfanumerico (2) | Opcional | UF de emissao do documento civil |
| inDataEmissaoDoctoCivil | Alfanumerico (10) | Opcional. Obrigatorio quando inNumDoctoCivil for informado | Data de emissao do documento civil (DD/MM/AAAA) |
| inJustificativaDocumentos | Alfanumerico (1) | Opcional. Obrigatorio quando inCPF, inNumNIS e inCertidaoNova nao forem preenchidos | Justificativa para a falta de documentos: 1 - O(A) aluno nao possui os documentos pessoais solicitados / 2 - A Escola nao dispoe ou nao recebeu os documentos pessoais do(a) aluno(a) |
| inNumeroCNS | Alfanumerico (15) | Opcional | N. Carteira Nacional de Saude |
| inCIN | Alfanumerico (1) | Opcional | Identificador do CIN (Carteira de Identificacao Nacional): S - Sim / N - Nao |
| inDataEmissaoCIN | Alfanumerico (10) | Obrigatorio se inCIN = S | Data de Emissao do CIN (DD/MM/AAAA) |

### Grupo inCertidaoNova (certidao de nascimento formato novo)

> Quando informado, todos os parametros contidos sao obrigatorios.

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCertidaoNova | Alfanumerico | Opcional | Grupo da certidao de nascimento no formato novo |
| inCertMatr01 | Alfanumerico (6) | Obrigatorio | Codigo do cartorio (999999) |
| inCertMatr02 | Alfanumerico (2) | Obrigatorio | Codigo do acervo (99) |
| inCertMatr03 | Alfanumerico (2) | Obrigatorio | Servico de registro civil das pessoas naturais (99) |
| inCertMatr04 | Alfanumerico (4) | Obrigatorio | Ano do registro (9999) |
| inCertMatr05 | Alfanumerico (1) | Obrigatorio | Tipo do Livro (9) |
| inCertMatr06 | Alfanumerico (5) | Obrigatorio | Numero do Livro (99999) |
| inCertMatr07 | Alfanumerico (3) | Obrigatorio | Numero da Folha (999) |
| inCertMatr08 | Alfanumerico (7) | Obrigatorio | Numero do Termo (9999999) |
| inCertMatr09 | Alfanumerico (2) | Obrigatorio | Digito de Controle (99) |
| inDataEmissaoCertidao | Alfanumerico (10) | Obrigatorio | Data de emissao da certidao de nascimento (DD/MM/AAAA) |

### Grupo inCertidaoAntiga (certidao de nascimento formato antigo)

> Quando informado, todos os parametros contidos sao obrigatorios.

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCertidaoAntiga | Alfanumerico | Opcional | Grupo da certidao de nascimento no formato antigo |
| inNumCertidao | Alfanumerico (6) | Obrigatorio | Numero da Certidao de Nascimento (999999) |
| inLivro | Alfanumerico (4) | Obrigatorio | Numero do livro de registro (XXXX) |
| inFolha | Alfanumerico (6) | Obrigatorio | Folha do livro de registro (XXXX) |
| inMunicipioComarca | Alfanumerico (100) | Obrigatorio | Municipio comarca do cartorio de registro |
| inUFComarca | Alfanumerico (2) | Obrigatorio | UF do municipio comarca |
| inDistritoCertidao | Alfanumerico (60) | Obrigatorio | Distrito do cartorio de registro |
| inDataEmissaoCertidao | Alfanumerico (10) | Obrigatorio | Data de emissao da certidao de nascimento (DD/MM/AAAA) |

### Grupo inEnderecoResidencial

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inEnderecoResidencial | Alfanumerico | Nao se aplica | Grupo do endereco residencial do aluno |
| inLogradouro | Alfanumerico (100) | Obrigatorio | Logradouro do endereco residencial |
| inNumero | Alfanumerico (10) | Obrigatorio | Numero da residencia |
| inAreaLogradouro | Alfanumerico (10) | Obrigatorio | Area do logradouro: 0 - Urbana / 1 - Rural |
| inComplemento | Alfanumerico (60) | Opcional | Complemento do endereco residencial |
| inBairro | Alfanumerico (60) | Obrigatorio | Nome do bairro da residencia |
| inCep | Alfanumerico (8) | Obrigatorio | CEP da residencia |
| inNomeCidade | Alfanumerico (60) | Obrigatorio | Nome da localidade da residencia |
| inUFCidade | Alfanumerico (2) | Obrigatorio | UF da localidade |
| inCodMunicipioDNE | Alfanumerico (4) | Obrigatorio | Codigo DNE (Correios) do municipio do endereco residencial |
| inLatitude | Alfanumerico (100) | Obrigatorio | Latitude do endereco residencial |
| inLongitude | Alfanumerico (100) | Obrigatorio | Longitude do endereco residencial |
| inCodLocalizacaoDiferenciada | Alfanumerico (1) | Opcional | Localizacao diferenciada do endereco do aluno (item 2.1.3) |

### Grupo inDeficiencia

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDeficiencia | Alfanumerico | Nao se aplica | Grupo das deficiencias do aluno |
| inCodNecessidade | Alfanumerico (40) | Opcional. Obrigatorio se inMobilidadeReduzida = 1 | Codigo de identificacao da necessidade (item 2.1.4). Informar uma ou mais necessidades separando os codigos com ponto e virgula (exemplo: 1; 8; 10) |
| inMobilidadeReduzida | Numerico (1) | Obrigatorio | Indica se aluno possui mobilidade reduzida: 0 - nao / 1 - sim |
| inTipoMobilidadeReduzida | Alfanumerico (1) | Opcional | Tipo da mobilidade reduzida: T - temporaria / P - permanente |
| inDataInicioMobilidadeReduzida | Alfanumerico (10) | Obrigatorio se Tipo Mobilidade Reduzida = T ou P | DD/MM/AAAA |
| intDataFimMobilidadeReduzida | Alfanumerico (10) | Obrigatorio se Tipo Mobilidade Reduzida = T | DD/MM/AAAA |
| inCodigoNivelSuporte | Alfanumerico (1) | Obrigatorio se informado alguma necessidade em inCodNecessidade | 1 - Nivel 1 / 2 - Nivel 2 / 3 - Nivel 3 |

### Subgrupo inProfissionalApoioEscolarVO

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inProfissionalApoioEscolarVO | Alfanumerico | Nao se aplica | Grupo de Informacoes do Apoio Escolar |
| inProfissionalApoioEscolar | Alfanumerico (1) | Opcional | Profissional de Apoio Escolar: 0 - nao / 1 - sim. Se igual a 1, e obrigatorio informar inAtividadeDiaria ou inAtividadeEscolar |
| inAtividadeDiaria | Alfanumerico (1) | Opcional | Atividade Diaria: 0 - nao / 1 - sim. Se igual a 1, e obrigatorio informar ao menos um apoio (Higiene, Locomocao, Alimentacao, Banheiro ou Medicamento) |
| inAtividadeEscolar | Alfanumerico (1) | Opcional | Atividade Escolar: 0 - nao / 1 - sim |
| inApoioHigiene | Alfanumerico (1) | Opcional | Apoio Higiene: 0 - nao / 1 - sim |
| inApoioLocomocao | Alfanumerico (1) | Opcional | Apoio Locomocao: 0 - nao / 1 - sim |
| inApoioAlimentacao | Alfanumerico (1) | Opcional | Apoio Alimentacao: 0 - nao / 1 - sim |
| inApoioBanheiro | Alfanumerico (1) | Opcional | Apoio Banheiro: 0 - nao / 1 - sim |
| inApoioMedicamento | Alfanumerico (1) | Opcional | Apoio Medicamento: 0 - nao / 1 - sim |
| inDataInicioVigenciaAtividadeDiaria | Alfanumerico (10) | Obrigatorio se inAtividadeDiaria = 1 | DD/MM/AAAA |
| inDataFimVigenciaAtividadeDiaria | Alfanumerico (10) | Obrigatorio se inAtividadeDiaria = 1 | DD/MM/AAAA |
| inDataInicioVigenciaAtividadeEscolar | Alfanumerico (10) | Obrigatorio se inAtividadeEscolar = 1 | DD/MM/AAAA |
| inDataFimVigenciaAtividadeEscolar | Alfanumerico (10) | Obrigatorio se inAtividadeEscolar = 1 | DD/MM/AAAA |

### Subgrupo inInvestigacaoDeficiencia

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inInvestigacaoDeficiencia | Alfanumerico (1) | Opcional | 0 ou Nulo - Deficiencia nao sendo investigada / 1 - Deficiencia sendo investigada |
| inComprovanteInvestigacao | Alfanumerico | Opcional | Item de Grupo com informacoes do Comprovante de Investigacao |
| inDataReferencia | Alfanumerico (10) | Obrigatorio se inInvestigacaoDeficiencia = 1 | Data da referencia |
| inObservacoes | Alfanumerico | Opcional. So pode ser preenchido se inInvestigacaoDeficiencia = 1 | Informacoes adicionais, consideradas pertinentes |
| inComprovanteURIBase64 | Alfanumerico | Obrigatorio se inInvestigacaoDeficiencia = 1 | Arquivo do Comprovante no formato URIBase64. Tamanho Maximo 5MB |

### Grupo inRecursoAvaliacao

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inRecursoAvaliacao | Alfanumerico | Nao se aplica | Grupo dos Recursos necessarios para a participacao do aluno em avaliacoes |
| inGuiaInterprete | Alfanumerico (1) | Opcional | Guia-Interprete: 0 - nao (parametro vazio) / 1 - sim |
| inInterpreteLibras | Alfanumerico (1) | Opcional | Interprete de Libras: 0 - nao (parametro vazio) / 1 - sim |
| inLeituraLabial | Alfanumerico (1) | Opcional | Leitura Labial: 0 - nao (parametro vazio) / 1 - sim |
| inNenhum | Alfanumerico (1) | Opcional | Indicador de nenhum recurso utilizado: 0 - nao (parametro vazio) / 1 - sim |
| inProvaAmpliada | Alfanumerico (1) | Opcional | Prova Ampliada: 0 - nao (parametro vazio) / 1 - sim |
| inFonteProva | Alfanumerico (1) | Opcional | Tamanho da fonte da prova ampliada: 1 - 16 / 0 - 24 |
| inFonteProva18 | Alfanumerico (1) | Opcional | 0 - Nao ativa nenhum recurso / 1 - Tamanho da fonte igual a 18 |
| inFonteProva20 | Alfanumerico (1) | Opcional | 0 - Nao ativa nenhum recurso / 1 - Tamanho da fonte igual a 20 |
| inProvaBraile | Alfanumerico (1) | Opcional | Prova em Braille: 0 - nao (parametro vazio) / 1 - sim |
| inAuxilioTranscricao | Alfanumerico (1) | Opcional | Auxilio transcricao: 0 - nao (parametro vazio) / 1 - sim |
| inAuxilioLeitor | Alfanumerico (1) | Opcional | Auxilio leitor: 0 - nao (parametro vazio) / 1 - sim |
| inProvaVideoLibras | Alfanumerico (1) | Opcional | Prova em Video em Libras: 0 - nao (parametro vazio) / 1 - sim |
| inProvaLinguaPortuguesa | Alfanumerico (1) | Opcional | Prova de Lingua Portuguesa como segunda lingua para surdos e deficientes auditivos: 0 - nao (parametro vazio) / 1 - sim |
| inCdAudioDefVisual | Alfanumerico (1) | Opcional | CD com audio para deficiente visual: 0 - nao (parametro vazio) / 1 - sim |

### Grupo inRastreio

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inRastreio | Alfanumerico | Nao se aplica | Grupo dos dados para identificacao do usuario do sistema remoto |
| inUsuarioRemoto | Alfanumerico (30) | Opcional | Identificacao do usuario no sistema remoto |
| inNomeUsuario | Alfanumerico (100) | Opcional | Nome do usuario no sistema remoto |
| inNumCPF | Alfanumerico (11) | Opcional | Numero do CPF do usuario |
| inLocalPerfilAcesso | Alfanumerico (60) | Opcional | Nome do perfil e local origem do acesso |

---

## Exemplo de Request

**Body:**

```json
{
  "inDadosPessoais": {
    "inNomeAluno": "",
    "inNomeMae": "",
    "inNomePai": "",
    "inNomeSocial": "",
    "inNomeAfetivo": "",
    "inDataNascimento": "",
    "inCorRaca": 0,
    "inSexo": "",
    "inBolsaFamilia": "",
    "inQuilombola": "",
    "inPossuiInternet": "",
    "inPossuiNotebookSmartphoneTablet": "",
    "inEmail": "",
    "inFlagSigilo": "",
    "inNacionalidade": "",
    "inNomeMunNascto": "",
    "inUFMunNascto": "",
    "inCodMunNasctoDNE": "",
    "inDataEntradaPais": "",
    "inCodPaisOrigem": "",
    "inPaisOrigem": "",
    "inTipoSanguineo": "",
    "inDoadorOrgaos": "",
    "inCodTipoIndigena": ""
  },
  "inDeficiencia": {
    "inMobilidadeReduzida": true,
    "inTipoMobilidadeReduzida": "",
    "inDataInicioMobilidadeReduzida": "",
    "inDataFimMobilidadeReduzida": "",
    "inCodigoNivelSuporte": "",
    "inCodNecessidade": "",
    "inProfissionalApoioEscolarVO": {
      "inProfissionalApoioEscolar": "",
      "inAtividadeDiaria": "",
      "inAtividadeEscolar": "",
      "inApoioHigiene": "",
      "inApoioLocomocao": "",
      "inApoioAlimentacao": "",
      "inApoioBanheiro": "",
      "inApoioMedicamento": "",
      "inDataInicioVigenciaAtividadeDiaria": "",
      "inDataFimVigenciaAtividadeDiaria": "",
      "inDataInicioVigenciaAtividadeEscolar": "",
      "inDataFimVigenciaAtividadeEscolar": ""
    },
    "inInvestigacaoDeficiencia": "",
    "inComprovanteInvestigacao": {
      "inDataReferencia": "",
      "inObservacoes": "",
      "inComprovanteURIBase64": ""
    }
  },
  "inRecursoAvaliacao": {
    "inNenhum": "",
    "inAuxilioLeitor": "",
    "inAuxilioTranscricao": "",
    "inGuiaInterprete": "",
    "inInterpreteLibras": "",
    "inLeituraLabial": "",
    "inProvaBraile": "",
    "inProvaAmpliada": "",
    "inFonteProva": "",
    "inFonteProva18": "",
    "inFonteProva20": "",
    "inProvaVideoLibras": "",
    "inCdAudioDefVisual": "",
    "inProvaLinguaPortuguesa": ""
  },
  "inDocumentos": {
    "inNumDoctoCivil": "",
    "inDigitoDoctoCivil": "",
    "inUFDoctoCivil": "",
    "inDataEmissaoDoctoCivil": "",
    "inNumNIS": "",
    "inCodigoINEP": "",
    "inCPF": "",
    "inJustificativaDocumentos": "",
    "inNumeroCNS": "",
    "inCIN": "",
    "inDataEmissaoCIN": ""
  },
  "inCertidaoAntiga": {
    "inNumCertidao": "",
    "inLivro": "",
    "inFolha": "",
    "inDistritoCertidao": "",
    "inMunicipioComarca": "",
    "inUFComarca": "",
    "inDataEmissaoCertidao": "",
    "inCodMunicComarcaDNE": ""
  },
  "inCertidaoNova": {
    "inCertMatr01": "",
    "inCertMatr02": "",
    "inCertMatr03": "",
    "inCertMatr04": "",
    "inCertMatr05": "",
    "inCertMatr06": "",
    "inCertMatr07": "",
    "inCertMatr08": "",
    "inCertMatr09": "",
    "inDataEmissaoCertidao": ""
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
    "inCodLocalizacaoDiferenciada": 0,
    "inCodMunicipioDNE": 0,
    "inLatitude": "",
    "inLongitude": ""
  },
  "inRastreio": {
    "inUsuarioRemoto": "",
    "inNomeUsuario": "",
    "inNumCPF": "",
    "inLocalPerfilAcesso": ""
  }
}
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outAluno | Alfanumerico | Grupo de dados identificador do aluno |
| outNumRA | Alfanumerico (12) | Numero do RA |
| outDigitoRA | Alfanumerico (2) | Digito do RA |
| outSiglaUFRA | Alfanumerico (2) | UF do RA |
| outSucesso | Alfanumerico (10) | Mensagem indicativa de sucesso no processamento da requisicao |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outAluno": {
        "outNumRA": "",
        "outDigitoRA": "",
        "outSiglaUFRA": ""
    },
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

## Tabelas de Codificacao

### 2.1.1 Cor / Raca

| Codigo | Descricao |
|---|---|
| 1 | Branca |
| 2 | Preta |
| 3 | Parda |
| 4 | Amarela |
| 5 | Indigena |
| 6 | Nao Declarada |

### 2.1.3 Localizacao Diferenciada

| Codigo | Descricao |
|---|---|
| 1 | Area de assentamento |
| 2 | Terra indigena |
| 3 | Area onde se localiza comunidade remanescente de quilombos |
| 7 | Nao esta em area de localizacao diferenciada |

Dados disponiveis em: `/api/DadosBasicos/TabelasDominio [outLocalizacaoDiferencada]`

### 2.1.4 Necessidades Especiais

| Codigo | Descricao |
|---|---|
| 1 | Multipla |
| 2 | Cegueira |
| 3 | Baixa Visao |
| 4 | Surdez Severa ou Profunda |
| 5 | Surdez Leve ou Moderada |
| 6 | Surdocegueira |
| 7 | Fisica - Paralisia Cerebral |
| 8 | Fisica - Cadeirante |
| 9 | Fisica - Outros |
| 10 | Sindrome de Down |
| 11 | Intelectual |
| 12 | Visao Monocular |
| 20 | Autista Infantil |
| 21 | Sindrome De Asperger |
| 22 | Sindrome De Rett |
| 23 | Transtorno Desintegrativo da Infancia |
| 30 | Altas Habilidades / Superdotacao |
| 201 | DISCALCULIA |
| 202 | DISGRAFIA |
| 203 | DISLALIA |
| 204 | DISLEXIA |
| 205 | TDAH |
| 206 | TPAC |

Dados disponiveis em: `/api/DadosBasicos/NecessidadesEspeciais`

Regras: Grupo de Deficiencias do Aluno (inDeficiencia) x Grupo dos Recursos necessarios para a participacao do aluno em avaliacoes (inRecursoAvaliacao) estao descritas no item 2.1.4.1 do documento de especificacao NCA017_SEESP_Integracao_Manutencao.

---

## Observacoes

- Este metodo utiliza o verbo HTTP POST (diferente dos demais que utilizam GET).
- O RA gerado no retorno deve ser utilizado nos demais processos do sistema (consultas, inscricoes, matriculas e movimentacoes).
- Os campos inNomeSocial e inNomeAfetivo nao podem ser preenchidos ao mesmo tempo. inNomeSocial e para autoidentificacao de identidade e genero; inNomeAfetivo e para casos de processo de adocao.
- Para informar/alterar o Tamanho da Fonte da Prova, informe uma unica opcao: inProvaAmpliada ou inFonteProva ou inFonteProva18 ou inFonteProva20.
- A tabela completa de paises (item 2.1.2) e a tabela de povos indigenas (item 2.1.6) estao disponiveis no documento original do PDF.
- Nome social: Decreto 55.588/10; Deliberacao CEE 125/14; Resolucao SE 45/2014; Parecer CNE/CP n. 14/2017.
- Nome afetivo: Lei N. 16.785/18.
