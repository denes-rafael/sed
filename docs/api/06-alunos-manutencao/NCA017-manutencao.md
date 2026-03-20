# NCA017 - Manutencao da Ficha do Aluno

> **Versao:** 2.18 | **Ultima atualizacao:** 25/08/2025 | **Autor:** Alexandre Mendes / Flavio J. Leamari / Italo Galetti

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | Manutencao |
| **Codigo** | NCA017 |
| **Descricao** | Efetuar manutencao/alteracao na ficha do aluno |
| **Metodo HTTP** | POST |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/Manutencao` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/Manutencao` |
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

### Grupo inDadosPessoais (dados pessoais do aluno)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDadosPessoais | Alfanumerico | Obrigatorio | Grupo de dados pessoais do aluno |
| inNomeAluno | Alfanumerico (100) | Obrigatorio | Nome completo do aluno |
| inNomeMae | Alfanumerico (100) | Opcional | Nome completo da Mae (Filiacao 01) |
| inNomePai | Alfanumerico (100) | Opcional | Nome completo do Pai (Filiacao 02) |
| inNomeSocial | Alfanumerico (100) | Opcional | Nome social do aluno (Item 2.1.6) |
| inNomeAfetivo | Alfanumerico (100) | Opcional | Nome afetivo do aluno (Item 2.1.6) |
| inDataNascimento | Alfanumerico (10) | Obrigatorio | Data de Nascimento do aluno (DD/MM/AAAA) |
| inCorRaca | Alfanumerico (2) | Obrigatorio | Codigo da cor ou raca do aluno (ver tabela 2.1.1) |
| inSexo | Alfanumerico (1) | Obrigatorio | Identificacao do sexo: 1 - Masculino, 2 - Feminino |
| inEmail | Alfanumerico (100) | Opcional | Endereco do e-mail do aluno ou do responsavel |
| inNacionalidade | Alfanumerico (1) | Obrigatorio | Codigo da nacionalidade: 1 - Brasileiro, 2 - Estrangeiro, 3 - Brasileiro Nascido no Exterior |
| inNomeMunNascto | Alfanumerico (60) | Opcional; obrigatorio se inNacionalidade = 1 | Municipio de nascimento do aluno |
| inUFMunNascto | Alfanumerico (2) | Opcional; obrigatorio se inNacionalidade = 1 | UF do municipio de nascimento |
| inCodPaisOrigem | Alfanumerico (3) | Opcional | Codigo do pais de origem (ver tabela 2.1.2). Se inNacionalidade = 1, informar: 76 |
| inPaisOrigem | Alfanumerico (60) | Opcional; obrigatorio se inNacionalidade = 2 | Nome do pais de origem. Se inNacionalidade = 1, informar: Brasil |
| inCodMunNasctoDNE | Alfanumerico (4) | Opcional | Codigo DNE (Correios) do municipio de nascimento |
| inDataEntradaPais | Alfanumerico (10) | Opcional; obrigatorio se inNacionalidade = 2 | Data de entrada no Brasil (DD/MM/AAAA) |
| inBolsaFamilia | Alfanumerico (1) | Opcional | Participa do programa Bolsa Familia: 0 - Nao, 1 - Sim |
| inQuilombola | Alfanumerico (1) | Opcional | Aluno quilombola: 0 - Nao, 1 - Sim |
| inPossuiInternet | Alfanumerico (1) | Obrigatorio | Possui internet: N - Nao, S - Sim |
| inPossuiNotebookSmartphoneTablet | Alfanumerico (1) | Obrigatorio | Possui Notebook/Smartphone/Tablet: N - Nao, S - Sim |
| inTipoSanguineo | Alfanumerico (3) | Opcional | Tipo sanguineo: A+, A-, B+, B-, AB+, AB-, O+, O- |
| inDoadorOrgaos | Alfanumerico (3) | Opcional | Doador de orgaos: SIM/NAO |
| inCodTipoIndigena | Alfanumerico (3) | Opcional; obrigatorio se inCorRaca = 5 | Identificacao dos povos indigenas (ver tabela 2.1.7) |

### Grupo inDocumentos (documentos do aluno)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDocumentos | Alfanumerico | Opcional | Grupo de documentos do aluno |
| inNumeroCNS | Alfanumerico (15) | Opcional | Numero da Carteira Nacional de Saude |
| inCodigoINEP | Alfanumerico (12) | Opcional | Codigo identificador do INEP/MEC |
| inCPF | Alfanumerico (11) | Opcional | Numero do CPF do aluno |
| inNumNIS | Alfanumerico (11) | Opcional | Numero de identificacao social |
| inNumDoctoCivil | Alfanumerico (14) | Opcional | Numero do documento civil do aluno (RG ou RNE) |
| inDigitoDoctoCivil | Alfanumerico (2) | Opcional; obrigatorio quando documento civil for RG >= 24.000.000 e inUFDoctoCivil = SP | Digito do documento civil |
| inUFDoctoCivil | Alfanumerico (2) | Opcional | UF de emissao do documento civil |
| inDataEmissaoDoctoCivil | Alfanumerico (10) | Opcional; obrigatorio quando inNumDoctoCivil informado | Data de emissao do documento civil (DD/MM/AAAA) |
| inJustificativaDocumentos | Alfanumerico (1) | Opcional; obrigatorio quando inCPF, inNumNIS e inCertidaoNova nao preenchidos | Justificativa para falta de documentos: 1 - Aluno nao possui documentos pessoais, 2 - Escola nao dispoe dos documentos |
| inCIN | Alfanumerico (1) | Opcional | CIN (Carteira de Identificacao Nacional): "S" Sim ou "N" Nao |
| inDataEmissaoCIN | Alfanumerico (10) | Obrigatorio se inCIN = "S" | Data de Emissao do CIN (DD/MM/AAAA) |

### Grupo inCertidaoNova (certidao de nascimento formato novo)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCertidaoNova | Alfanumerico | Opcional; quando informado, todos os campos sao obrigatorios | Grupo da certidao de nascimento no formato novo |
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

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inCertidaoAntiga | Alfanumerico | Opcional; quando informado, todos os campos sao obrigatorios | Grupo da certidao de nascimento no formato antigo |
| inNumCertidao | Alfanumerico (6) | Obrigatorio | Numero da Certidao de Nascimento (999999) |
| inLivro | Alfanumerico (4) | Obrigatorio | Numero do livro de registro (XXXX) |
| inFolha | Alfanumerico (6) | Obrigatorio | Folha do livro de registro (XXXX) |
| inMunicipioComarca | Alfanumerico (100) | Obrigatorio | Municipio comarca do cartorio de registro |
| inUFComarca | Alfanumerico (2) | Obrigatorio | UF do municipio comarca |
| inDistritoCertidao | Alfanumerico (60) | Obrigatorio | Distrito do cartorio de registro |
| inDataEmissaoCertidao | Alfanumerico (10) | Obrigatorio | Data de emissao da certidao de nascimento (DD/MM/AAAA) |

### Grupo inEnderecoResidencial (endereco residencial do aluno)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inEnderecoResidencial | Alfanumerico | Obrigatorio | Grupo do endereco residencial do aluno |
| inLogradouro | Alfanumerico (100) | Obrigatorio | Logradouro do endereco residencial |
| inNumero | Alfanumerico (10) | Obrigatorio | Numero da residencia |
| inAreaLogradouro | Alfanumerico (10) | Obrigatorio | Area do logradouro: 0 - Urbana, 1 - Rural |
| inComplemento | Alfanumerico (60) | Opcional | Complemento do endereco residencial |
| inBairro | Alfanumerico (60) | Obrigatorio | Nome do bairro da residencia |
| inCep | Alfanumerico (8) | Obrigatorio | CEP da residencia |
| inNomeCidade | Alfanumerico (60) | Obrigatorio | Nome da localidade da residencia |
| inUFCidade | Alfanumerico (2) | Obrigatorio | UF da localidade |
| inCodMunicipioDNE | Alfanumerico (4) | Obrigatorio | Codigo DNE (Correios) do municipio do endereco residencial |
| inLatitude | Alfanumerico (100) | Obrigatorio | Latitude do endereco residencial |
| inLongitude | Alfanumerico (100) | Obrigatorio | Longitude do endereco residencial |
| inCodLocalizacaoDiferenciada | Alfanumerico (1) | Opcional | Localizacao diferenciada do endereco (ver tabela 2.1.3) |

### Grupo inDeficiencia (deficiencias do aluno)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDeficiencia | Alfanumerico | Opcional | Grupo das deficiencias do aluno |
| inCodNecessidade | Alfanumerico (40) | Opcional; obrigatorio se inMobilidadeReduzida = 1 | Codigo de identificacao da necessidade (ver tabela 2.1.4). Informar uma ou mais necessidades separando codigos com ponto e virgula (ex: 1;8;10) |
| inMobilidadeReduzida | Numerico (1) | Opcional | Mobilidade reduzida: 0 - Nao, 1 - Sim |
| inTipoMobilidadeReduzida | Alfanumerico (1) | Opcional | Tipo: T - temporaria, P - permanente |
| inDataInicioMobilidadeReduzida | Alfanumerico (10) | Obrigatorio se Tipo Mobilidade = "T" ou "P" | Formato DD/MM/AAAA |
| inDataFimMobilidadeReduzida | Alfanumerico (10) | Obrigatorio se Tipo Mobilidade = "T" | Formato DD/MM/AAAA |
| inCodigoNivelSuporte | Alfanumerico (1) | Obrigatorio se informada alguma necessidade em inCodNecessidade | 1 - Nivel 1, 2 - Nivel 2, 3 - Nivel 3 (ver tabela 2.1.5) |
| inInvestigacaoDeficiencia | Alfanumerico (01) | Opcional | 0 ou Nulo - Deficiencia nao sendo investigada, 1 - Deficiencia sendo investigada |

### Subgrupo inProfissionalApoioEscolarVO (apoio escolar)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inProfissionalApoioEscolarVO | Alfanumerico | Nao se aplica | Grupo de Informacoes do Apoio Escolar |
| inProfissionalApoioEscolar | Alfanumerico (1) | Opcional | Profissional de Apoio Escolar: 0 - nao, 1 - sim. Se "1", obrigatorio informar inAtividadeDiaria ou inAtividadeEscolar |
| inAtividadeDiaria | Alfanumerico (1) | Opcional | Atividade Diaria: 0 - nao, 1 - sim. Se "1", obrigatorio informar ao menos um apoio (Higiene, Locomocao, Alimentacao, Banheiro ou Medicamento) |
| inAtividadeEscolar | Alfanumerico (1) | Opcional | Atividade Escolar: 0 - nao, 1 - sim |
| inApoioHigiene | Alfanumerico (1) | Opcional | Apoio Higiene: 0 - nao, 1 - sim |
| inApoioLocomocao | Alfanumerico (1) | Opcional | Apoio Locomocao: 0 - nao, 1 - sim |
| inApoioAlimentacao | Alfanumerico (1) | Opcional | Apoio Alimentacao: 0 - nao, 1 - sim |
| inApoioBanheiro | Alfanumerico (1) | Opcional | Apoio Banheiro: 0 - nao, 1 - sim |
| inApoioMedicamento | Alfanumerico (1) | Opcional | Apoio Medicacao: 0 - nao, 1 - sim |
| inDataInicioVigenciaAtividadeDiaria | Alfanumerico (10) | Obrigatorio se inAtividadeDiaria = 1 | Formato DD/MM/AAAA |
| inDataFimVigenciaAtividadeDiaria | Alfanumerico (10) | Obrigatorio se inAtividadeDiaria = 1 | Formato DD/MM/AAAA |
| inDataInicioVigenciaAtividadeEscolar | Alfanumerico (10) | Obrigatorio se inAtividadeEscolar = 1 | Formato DD/MM/AAAA |
| inDataFimVigenciaAtividadeEscolar | Alfanumerico (10) | Obrigatorio se inAtividadeEscolar = 1 | Formato DD/MM/AAAA |

### Subgrupo inComprovanteInvestigacao (comprovante de investigacao de deficiencia)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inComprovanteInvestigacao | Alfanumerico | Opcional | Grupo com informacoes do Comprovante de Investigacao |
| inDataReferencia | Alfanumerico (10) | Obrigatorio se inInvestigacaoDeficiencia = 1 | Data da referencia |
| inObservacoes | Alfanumerico | Opcional; so pode ser preenchido se inInvestigacaoDeficiencia = 1 | Informacoes adicionais pertinentes |
| inComprovanteURIBase64 | Alfanumerico | Obrigatorio se inInvestigacaoDeficiencia = 1 | Arquivo do Comprovante no formato URIBase64 (Tamanho Maximo 5MB) |

### Grupo inRecursoAvaliacao (recursos para avaliacao)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inRecursoAvaliacao | Alfanumerico | Opcional | Grupo dos Recursos necessarios para participacao em avaliacoes |
| inGuiaInterprete | Alfanumerico (1) | Opcional | Guia-Interprete: 0 - Nao, 1 - Sim |
| inInterpreteLibras | Alfanumerico (1) | Opcional | Interprete de Libras: 0 - Nao, 1 - Sim |
| inLeituraLabial | Alfanumerico (1) | Opcional | Leitura Labial: 0 - Nao, 1 - Sim |
| inNenhum | Alfanumerico (1) | Opcional | Nenhum recurso utilizado: 0 - Nao, 1 - Sim |
| inProvaAmpliada | Alfanumerico (1) | Opcional | 0 - Nao ativa recurso, 1 - Tamanho da fonte igual a 24 |
| inFonteProva | Alfanumerico (1) | Opcional | 0 - Nao ativa recurso, 1 - Tamanho da fonte igual a 16 |
| inFonteProva18 | Alfanumerico (1) | Opcional | 0 - Nao ativa recurso, 1 - Tamanho da fonte igual a 18 |
| inFonteProva20 | Alfanumerico (1) | Opcional | 0 - Nao ativa recurso, 1 - Tamanho da fonte igual a 20 |
| inProvaBraile | Alfanumerico (1) | Opcional | Prova em Braille: 0 - Nao, 1 - Sim |
| inAuxilioTranscricao | Alfanumerico (1) | Opcional | Auxilio transcricao: 0 - Nao, 1 - Sim |
| inAuxilioLeitor | Alfanumerico (1) | Opcional | Auxilio leitor: 0 - Nao, 1 - Sim |
| inProvaVideoLibras | Alfanumerico (1) | Opcional | Prova em Video em Libras: 0 - Nao, 1 - Sim |
| inProvaLinguaPortuguesa | Alfanumerico (1) | Opcional | Prova de Lingua Portuguesa como segunda lingua para surdos e deficientes auditivos: 0 - Nao, 1 - Sim |
| inCdAudioDefVisual | Alfanumerico (1) | Opcional | CD com audio para deficiente visual: 0 - Nao, 1 - Sim |

### Grupo inTelefone (telefones do aluno - ARRAY [1 : N])

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inTelefone | Alfanumerico | Opcional | Grupo de telefones do aluno. Os telefones informados substituirao todos os ja existentes na ficha do aluno |
| inDDDNumero | Alfanumerico (2) | Obrigatorio | DDD do telefone (99) |
| inNumero | Alfanumerico (9) | Obrigatorio | Numero do telefone (999999999) |
| inTipoTelefone | Alfanumerico (1) | Obrigatorio | Tipo do telefone: 1 - Residencial, 2 - Comercial, 3 - Celular, 4 - Recados, 5 - Celular Principal |
| inSMS | Alfanumerico (1) | Opcional; valido apenas para inTipoTelefone = 3 | Permissao para envio de SMS: 0 - Nao, 1 - Sim |
| inComplemento | Alfanumerico (30) | Opcional | Complemento do telefone |

### Grupo inRastreio (dados de rastreamento)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inRastreio | Alfanumerico | Nao documentado | Grupo de dados de rastreamento |
| inUsuarioRemoto | Alfanumerico | Nao documentado | Usuario remoto |
| inNomeUsuario | Alfanumerico | Nao documentado | Nome do usuario |
| inNumCPF | Alfanumerico | Nao documentado | Numero do CPF |
| inLocalPerfilAcesso | Alfanumerico | Nao documentado | Local do perfil de acesso |

---

## Exemplo de Request

```json
{
  "inAluno": {
    "inNumRA": "",
    "inDigitoRA": "",
    "inSiglaUFRA": ""
  },
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
  "inTelefone": [
    {
      "inTipoTelefone": 0,
      "inDDDNumero": "",
      "inNumero": "",
      "inComplemento": "",
      "inSMS": 0
    }
  ],
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
| outSucesso | Alfanumerico (10) | Mensagem indicativa de sucesso no processamento da requisicao |
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

### 2.1.1 - Cor / Raca

Dados disponiveis em: `/api/DadosBasicos/TabelasDominio` [outCorRaca]

| Codigo | Descricao |
|---|---|
| 1 | Branca |
| 2 | Preta |
| 3 | Parda |
| 4 | Amarela |
| 5 | Indigena |
| 6 | Nao Declarada |

### 2.1.2 - Paises

Dados disponiveis em: `/api/DadosBasicos/Pais`

Exemplos de codigos: 76 - Brasil, 32 - Argentina, 152 - Chile, 170 - Colombia, 218 - Equador, 600 - Paraguai, 604 - Peru, 858 - Uruguai, 862 - Venezuela, 840 - Estados Unidos da America, 620 - Portugal, 724 - Espanha, 380 - Italia, 392 - Japao, 156 - China

> Consultar a API `/api/DadosBasicos/Pais` para a lista completa de paises.

### 2.1.3 - Localizacao Diferenciada

Dados disponiveis em: `/api/DadosBasicos/TabelasDominio` [outLocalizacaoDiferencada]

| Codigo | Descricao |
|---|---|
| 1 | Area de assentamento |
| 2 | Terra indigena |
| 3 | Area onde se localiza comunidade remanescente de quilombos |
| 7 | Nao esta em area de localizacao diferenciada |

### 2.1.4 - Necessidades Especiais

Dados disponiveis em: `/api/DadosBasicos/NecessidadesEspeciais`

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

#### 2.1.4.1 - Regras de Deficiencia x Recurso de Avaliacao

- A deficiencia multipla deve ser ativada apenas quando houver duas deficiencias com codigos entre 2 e 11.
- Quando a deficiencia multipla esta marcada, "nenhum" nao pode estar marcado.
- As necessidades com codigos entre 20 e 23 sao transtornos; e permitido marcar apenas uma nessa categoria.
- **2 - CEGUEIRA:** Exige ao menos um recurso (nao permite: nenhum, Prova Lingua Portuguesa, Prova Video Libras).
- **3 - BAIXA VISAO:** Exige ao menos um recurso (permite "nenhum").
- **4 - SURDEZ SEVERA/PROFUNDA:** Exige ao menos um recurso (permite "nenhum", nao permite CD audio deficiente visual).
- **5 - SURDEZ LEVE/MODERADA:** Exige ao menos um recurso (permite "nenhum", nao permite CD audio deficiente visual).
- **6 - SURDOCEGUEIRA:** Exige ao menos um recurso (nao permite: nenhum, CD audio, Prova Lingua Portuguesa, Prova Video Libras).
- **7 a 12 - DEFICIENCIAS FISICAS, SINDROME DE DOWN, INTELECTUAL, VISAO MONOCULAR:** Exigem ao menos um recurso (permitem "nenhum").
- **20 a 23 - TRANSTORNOS:** Exigem ao menos um recurso (permitem "nenhum").
- **30 - ALTAS HABILIDADES:** Nao exige recurso. Nao pode ser combinado com Deficiencia Intelectual ou Sindrome de Down.

**Conflito entre auxilios:**
- Leitura Labial, Interprete Libras e Guia Interprete nao podem ser ativados todos juntos.
- Prova em Braille nao pode ser ativado junto com Prova Ampliada.

**Para informar/alterar o Tamanho da Fonte da Prova, informe uma unica opcao:** inProvaAmpliada ou inFonteProva ou inFonteProva18 ou inFonteProva20.

### 2.1.5 - Codigo de Nivel de Suporte

- **Nivel 1:** O estudante e capaz de realizar a maioria das atividades de forma autonoma, mas ocasionalmente necessita de apoio para amplificar sua comunicacao, participacao e integracao nas diversas demandas do cotidiano em ambiente escolar.
- **Nivel 2:** O estudante necessita de apoio moderado para participar das atividades escolares e sociais. Pode ter dificuldades significativas na comunicacao, interacao social e comportamento.
- **Nivel 3:** O estudante necessita de apoio substancial e continuo para participar das atividades escolares e de vida diaria. Apresenta limitacoes severas na comunicacao e interacao social.

### 2.1.7 - Tabela dos Povos Indigenas

Dados disponiveis em: `/api/DadosBasicos/TabelasDominio`

> Consultar a API para a lista completa de povos indigenas. O campo inCodTipoIndigena e obrigatorio quando inCorRaca = 5 (Indigena).

---

## Observacoes

- Este e o metodo principal de manutencao da ficha do aluno, com dezenas de campos distribuidos em grupos logicos.
- Os telefones informados no array inTelefone substituirao todos os telefones ja existentes na ficha do aluno.
- O campo inCodMunicipioDNE passou a ser obrigatorio a partir da versao 2.7.
- Campos incluidos na versao 2.14: inCIN e inDataEmissaoCIN.
- Campos incluidos na versao 2.16: inCodTipoIndigena e necessidades especiais 201-206 (Transtornos de Aprendizagem).
- Campos incluidos na versao 2.18: inInvestigacaoDeficiencia, inComprovanteInvestigacao (inDataReferencia, inObservacoes, inComprovanteURIBase64).
- O campo inCodLocalizacaoDiferenciada foi alterado na versao 2.11: "Nao esta em area de localizacao diferenciada" passou a ser tipo 7.
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
