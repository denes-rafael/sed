# NCA003 - Exibir Ficha Aluno

> **Versao:** 2.8 | **Ultima atualizacao:** 28/10/2025 | **Autor:** Italo G.

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | ExibirFichaAluno |
| **Codigo** | NCA003 |
| **Descricao** | Extrair e retornar ao solicitante dados da ficha do aluno cadastrados no sistema NCA de um determinado aluno utilizando como base para pesquisa o RA do mesmo. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/ExibirFichaAluno` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/ExibirFichaAluno` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY ou QUERY Parameters

### Grupo inAluno (identificador do aluno)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inAluno | Alfanumerico | Obrigatorio | Grupo de dados identificador do aluno |
| inNumRA | Alfanumerico (12) | Obrigatorio | Numero do RA |
| inDigitoRA | Alfanumerico (2) | Opcional | Digito do RA |
| inSiglaUFRA | Alfanumerico (2) | Obrigatorio | UF do RA |

---

## Exemplo de Request

**Query Parameters:**

```
/Aluno/ExibirFichaAluno?inNumRA=&inDigitoRA=&inSiglaUFRA=
```

**Body:**

```json
{
    "inAluno": {
        "inNumRA": "",
        "inDigitoRA": "",
        "inSiglaUFRA": ""
    }
}
```

---

## Parametros de Saida

### Dados Gerais

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outDataAlteracaoFicha | Alfanumerico (10) | Data de efetivacao da ultima alteracao da ficha do aluno (DD/MM/AAAA) |
| outOperador | Alfanumerico (20) | Nome do usuario responsavel pela ultima alteracao da ficha do aluno |

### Grupo outDadosPessoais

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outDadosPessoais | Alfanumerico | Grupo de dados pessoais do aluno |
| outNumRA | Alfanumerico (12) | Numero do RA |
| outDigitoRA | Alfanumerico (2) | Digito do RA |
| outSiglaUFRA | Alfanumerico (2) | UF do RA |
| outNomeAluno | Alfanumerico (100) | Nome completo do aluno |
| outNomeMae | Alfanumerico (100) | Nome completo da Mae (Filiacao 01) |
| outNomePai | Alfanumerico (100) | Nome completo do Pai (Filiacao 02) |
| outNomeSocial | Alfanumerico (100) | Nome social do aluno |
| outNomeAfetivo | Alfanumerico (100) | Nome Afetivo do aluno |
| outDataNascimento | Alfanumerico (10) | Data de Nascimento do aluno (DD/MM/AAAA) |
| outCorRaca | Alfanumerico (2) | Codigo da cor ou raca do aluno |
| outDescCorRaca | Alfanumerico (20) | Descricao da cor ou raca do aluno |
| outCodSexo | Alfanumerico (1) | Codigo identificador do sexo do aluno (1 - Masculino / 2 - Feminino) |
| outSexo | Alfanumerico (20) | Descricao do sexo do aluno (1 - Masculino / 2 - Feminino) |
| outEmail | Alfanumerico (100) | E-mail do aluno |
| outNacionalidade | Alfanumerico (1) | Codigo identificador da nacionalidade do aluno: 1 - Brasileiro, 2 - Estrangeiro, 3 - Brasileiro Nascido no Exterior |
| outDescNacionalidade | Alfanumerico (30) | Descricao da nacionalidade do aluno |
| outCodPaisOrigem | Alfanumerico (3) | Codigo do pais de origem do aluno |
| outNomePaisOrigem | Alfanumerico (100) | Nome do pais de origem do aluno |
| outDataEntradaPais | Alfanumerico (10) | Data de entrada no Brasil, caso o aluno seja estrangeiro |
| outCodBolsaFamilia | Alfanumerico (1) | Indicador de participacao no programa bolsa familia (0 - NAO / 1 - SIM) |
| outPossuiInternet | Alfanumerico (3) | SIM ou NAO |
| outPossuiNotebookSmartphoneTablet | Alfanumerico (3) | SIM ou NAO |
| outBolsaFamilia | Alfanumerico (60) | Mensagem indicando que o aluno participa ou nao do programa federal Bolsa Familia |
| outQuilombola | Alfanumerico (3) | Indica se o aluno e quilombola (Sim / Nao) |
| outTipoSanguineo | Alfanumerico (3) | A+, A-, B+, B-, AB+, AB-, O+, O- |
| outDoadorOrgaos | Alfanumerico (3) | SIM/NAO |
| outNomeMunNascto | Alfanumerico (100) | Municipio de nascimento do aluno, caso ele seja brasileiro |
| outUFMunNascto | Alfanumerico (2) | UF do municipio de nascimento do aluno |
| outCodMunNasctoDNE | Alfanumerico (4) | Codigo DNE (codigo identificador dos Correios) do municipio de nascimento |
| outAlunoFalecido | Alfanumerico (4) | Identifica se a ficha do aluno esta desativada devido falecimento: SIM ou NAO |
| outDataFalecimento | Alfanumerico (10) | Data do falecimento do aluno |

### Grupo outIrmaos (ARRAY [1 : N])

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outIrmaos | Alfanumerico | Grupo de irmaos do aluno no formato ARRAY [1 : N] |
| outNomeAluno | Alfanumerico (100) | Nome completo do irmao do aluno |
| outDataNascimento | Alfanumerico (10) | Data de nascimento do irmao (DD/MM/AAAA) |
| outNumRA | Alfanumerico (10) | Numero do RA do irmao |
| outDigitoRA | Alfanumerico (2) | Digito do RA do irmao |
| outSiglaUFRA | Alfanumerico (2) | UF do RA |
| outGemeo | Alfanumerico (3) | Indicador de irmao gemeo: SIM / NAO |

### Grupo outDocumentos

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outDocumentos | Alfanumerico | Grupo de documentos do aluno |
| outCodINEP | Alfanumerico (12) | Codigo identificador do INEP/MEC |
| outCPF | Alfanumerico (11) | Numero do CPF do aluno |
| outNumNIS | Alfanumerico (11) | Numero de identificacao social |
| outNumDoctoCivil | Alfanumerico (14) | Numero do documento civil do aluno (RG ou RNE) |
| outDigitoDoctoCivil | Alfanumerico (2) | Digito do documento civil |
| outUFDoctoCivil | Alfanumerico (2) | UF de emissao do documento civil |
| outDataEmissaoDoctoCivil | Alfanumerico (10) | Data de emissao do documento civil (DD/MM/AAAA) |
| outDataEmissaoCertidao | Alfanumerico (10) | Data de emissao da certidao de nascimento (DD/MM/AAAA) |
| outCodJustificativa | Alfanumerico (1) | Codigo identificador da justificativa da falta de documentos |
| outJustificativaDocumento | Alfanumerico (100) | Justificativa para a falta de documentos (Certidao Nova, CPF e NIS) |
| outNumeroCNS | Alfanumerico (15) | N. Carteira Nacional de Saude |
| outCIN | Alfanumerico (1) | Identificador da Carteira de Identificacao Nacional (CIN) |
| outDataEmissaoCIN | Alfanumerico (10) | Data de Emissao do CIN (DD/MM/AAAA) |

### Grupo outCertidaoNova (certidao de nascimento formato novo)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outCertidaoNova | Alfanumerico | Grupo da certidao de nascimento no formato novo |
| outCertMatr01 | Alfanumerico (6) | Codigo do cartorio (999999) |
| outCertMatr02 | Alfanumerico (2) | Codigo do acervo (99) |
| outCertMatr03 | Alfanumerico (2) | Servico de registro civil das pessoas naturais (99) |
| outCertMatr04 | Alfanumerico (4) | Ano do registro (9999) |
| outCertMatr05 | Alfanumerico (1) | Tipo do Livro (9) |
| outCertMatr06 | Alfanumerico (5) | Numero do Livro (99999) |
| outCertMatr07 | Alfanumerico (3) | Numero da Folha (999) |
| outCertMatr08 | Alfanumerico (7) | Numero do Termo (9999999) |
| outCertMatr09 | Alfanumerico (2) | Digito de Controle (99) |

### Grupo outCertidaoAntiga (certidao de nascimento formato antigo)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outCertidaoAntiga | Alfanumerico | Grupo da certidao de nascimento no formato antigo |
| outNumCertidao | Alfanumerico (6) | Numero da Certidao de Nascimento (999999) |
| outNumLivroReg | Alfanumerico (4) | Numero do livro de registro (XXXX) |
| outFolhaRegNum | Alfanumerico (6) | Folha do livro de registro (XXXX) |
| outNomeMunComarca | Alfanumerico (100) | Municipio comarca do cartorio de registro |
| outUFComarca | Alfanumerico (2) | UF do municipio comarca |
| outDistritoNasc | Alfanumerico (60) | Distrito do cartorio de registro |

### Grupo outEnderecoResidencial

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outEnderecoResidencial | Alfanumerico | Grupo do endereco residencial do aluno |
| outLogradouro | Alfanumerico (100) | Logradouro do endereco residencial |
| outNumero | Alfanumerico (10) | Numero da residencia |
| outCodArea | Alfanumerico (1) | Codigo identificador da area do logradouro |
| outAreaLogradouro | Alfanumerico (10) | Area do logradouro: Urbana / Rural |
| outComplemento | Alfanumerico (60) | Complemento do endereco residencial |
| outBairro | Alfanumerico (60) | Nome do bairro da residencia |
| outCep | Alfanumerico (8) | CEP da residencia |
| outNomeCidade | Alfanumerico (60) | Nome da localidade da residencia |
| outUFCidade | Alfanumerico (2) | UF da localidade |
| outCodMunicipioDNE | Alfanumerico (4) | Codigo DNE (codigo identificador dos Correios) do municipio de residencia |
| outLatitude | Alfanumerico (100) | Latitude do endereco residencial |
| outLongitude | Alfanumerico (100) | Longitude do endereco residencial |
| outCodLocalizacao | Alfanumerico (2) | Codigo identificador da localizacao |
| outLocalizacaoDiferenciada | Alfanumerico (100) | Localizacao diferenciada do endereco do aluno |

### Grupo outEnderecoIndicativo

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outEnderecoIndicativo | Alfanumerico | Grupo do endereco indicativo do aluno |
| outCep | Alfanumerico (8) | CEP do endereco indicativo |
| outLogradouro | Alfanumerico (100) | Logradouro do endereco indicativo |
| outNumero | Alfanumerico (10) | Numero do endereco indicativo |
| outBairro | Alfanumerico (30) | Bairro do endereco indicativo |
| outNomeCidade | Alfanumerico (60) | Nome da localidade do endereco indicativo |
| outUFCidade | Alfanumerico (60) | UF da localidade do endereco indicativo |
| outLatitude | Alfanumerico (100) | Latitude do endereco indicativo |
| outLongitude | Alfanumerico (100) | Longitude do endereco indicativo |

### Grupo outTelefones (ARRAY [1 : N])

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outTelefones | Alfanumerico | Grupo de telefones do aluno no formato ARRAY [1 : N] |
| outDDDNumero | Alfanumerico (2) | DDD do telefone (99) |
| outNumero | Alfanumerico (9) | Numero do telefone (999999999) |
| outTipoTelefone | Alfanumerico (1) | Tipo do telefone: 1 - Residencial, 2 - Comercial, 3 - Celular, 4 - Recados |
| outDescTipoTelefone | Alfanumerico (20) | Descricao do tipo do telefone |
| outComplemento | Alfanumerico (30) | Complemento do telefone |
| outSMS | Alfanumerico (3) | Indica permissao para recebimento de SMS em telefone do tipo 3 - Celular |

### Grupo outIndigena

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outIndigena | Alfanumerico | Identificacao de Povo Indigena |
| outCodigoTipoIndigena | Alfanumerico (3) | Codigo de Identificacao dos povos indigenas |
| outDescricaoTipoIndigena | Alfanumerico (50) | Descricao dos povos indigenas |

### Grupo outDeficiencia

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outDeficiencia | Alfanumerico | Deficiencias |
| outMobilidadeReduzida | Alfanumerico (3) | Indica se aluno possui mobilidade reduzida: SIM / NAO (parametro vazio) |
| outTipoMobilidadeReduzida | Alfanumerico (1) | Tipo da mobilidade reduzida: T - temporaria / P - permanente |
| outDataInicioMobilidadeReduzida | Alfanumerico (10) | DD/MM/AAAA |
| outDataFimMobilidadeReduzida | Alfanumerico (10) | DD/MM/AAAA |
| outCodigoNivelSuporte | Alfanumerico (1) | 0 - Nao possui / 1 - Nivel 1 / 2 - Nivel 2 / 3 - Nivel 3 |

### Subgrupo outProfissionalApoioEscolarResponse

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outProfissionalApoioEscolarResponse | Alfanumerico | Apoio Escolar |
| outProfissionalApoioEscolar | Alfanumerico (1) | Profissional de Apoio Escolar: 0 - Nao necessita / 1 - Necessita |
| outAtividadeDiaria | Alfanumerico (1) | Atividade Diaria: 0 - Nao / 1 - Sim |
| outAtividadeEscolar | Alfanumerico (1) | Atividade Escolar: 0 - Nao / 1 - Sim |
| outApoioHigiene | Alfanumerico (1) | Higiene: 0 - Nao / 1 - Sim |
| outApoioLocomocao | Alfanumerico (1) | Locomocao: 0 - Nao / 1 - Sim |
| outApoioAlimentacao | Alfanumerico (1) | Alimentacao: 0 - Nao / 1 - Sim |
| outApoioBanheiro | Alfanumerico (1) | Banheiro: 0 - Nao / 1 - Sim |
| outApoioMedicamento | Alfanumerico (1) | Medicamento: 0 - Nao / 1 - Sim |
| outDataInicioVigenciaAtividadeDiaria | Alfanumerico (10) | DD/MM/AAAA |
| outDataFimVigenciaAtividadeDiaria | Alfanumerico (10) | DD/MM/AAAA |
| outDataInicioVigenciaAtividadeEscolar | Alfanumerico (10) | DD/MM/AAAA |
| outDataFimVigenciaAtividadeEscolar | Alfanumerico (10) | DD/MM/AAAA |
| outFlTranstornoAprendizagem | Alfanumerico (1) | S - Sim / N - Nao |
| outFlInvestigacaoDeficiencia | Alfanumerico (1) | S - Sim / N - Nao |

### Subgrupo outListaComprovantePNE (ARRAY)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outListaComprovantePNE | Alfanumerico | Lista dos Comprovantes |
| outDescricaoTipoInformacao | Alfanumerico | Descricao do Tipo da Informacao |
| outDataReferencia | Alfanumerico (10) | Formato: DDMMAAAA |
| outObservacoes | Alfanumerico | Observacoes |

### Grupo outListaNecessidadesEspeciais (ARRAY [1 : N])

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outListaNecessidadesEspeciais | Alfanumerico | Lista das necessidades especiais do aluno no formato ARRAY [1 : N] |
| outCodNecesEspecial | Alfanumerico (2) | Codigo identificador da necessidade especial |
| outNomeNecesEspecial | Alfanumerico (100) | Descricao da necessidade especial |

### Grupo outRecursoAvaliacao

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outRecursoAvaliacao | Alfanumerico | Grupo dos Recursos necessarios para a participacao do aluno em avaliacoes |
| outGuiaInterprete | Alfanumerico (3) | Guia-Interprete |
| outInterpreteLibras | Alfanumerico (3) | Interprete de Libras |
| outLeituraLabial | Alfanumerico (3) | Leitura Labial |
| outNenhum | Alfanumerico (3) | Indicador de nenhum recurso utilizado |
| outProvaAmpliada | Alfanumerico (3) | Prova Ampliada |
| outTamanhoFonte | Alfanumerico (2) | Tamanho da fonte da prova ampliada: 16 / 18 / 20 / 24 |
| outProvaBraile | Alfanumerico (3) | Prova em Braille |
| outAuxilioTranscricao | Alfanumerico (3) | Auxilio transcricao |
| outAuxilioLeitor | Alfanumerico (3) | Auxilio leitor |
| outProvaVideoLibras | Alfanumerico (3) | Prova em Video em Libras |
| outCdAudioDefVisual | Alfanumerico (3) | CD com audio para deficiente visual |
| outProvaLinguaPortuguesa | Alfanumerico (3) | Prova de Lingua Portuguesa como segunda lingua para surdos e deficientes auditivos |

### Outros parametros de saida

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
  "outRequestID": "",
  "outDataAlteracaoFicha": "",
  "outOperador": "",
  "outDadosPessoais": {
    "outNumRA": "",
    "outDigitoRA": "",
    "outSiglaUFRA": "",
    "outNomeAluno": "",
    "outDataNascimento": "",
    "outCorRaca": "",
    "outDescCorRaca": "",
    "outCodSexo": "",
    "outSexo": "",
    "outNomeMae": "",
    "outNomePai": "",
    "outNomeSocial": "",
    "outNomeAfetivo": "",
    "outFiliacao3": "",
    "outEmail": "",
    "outEmailGoogle": "",
    "outEmailMicrosoft": "",
    "outNacionalidade": "",
    "outDescNacionalidade": "",
    "outCodPaisOrigem": "",
    "outNomePaisOrigem": "",
    "outDataEntradaPais": "",
    "outBolsaFamilia": "",
    "outQuilombola": "",
    "outPossuiInternet": "",
    "outPossuiNotebookSmartphoneTablet": "",
    "outGemeo": "",
    "outNomeMunNascto": "",
    "outUFMunNascto": "",
    "outAlunoFalecido": "",
    "outDataFalecimento": "",
    "outCodMunNasctoDNE": "",
    "outCodBolsaFamilia": "",
    "outDoadorOrgaos": "",
    "outTipoSanguineo": ""
  },
  "outIrmaos": [
    {
      "outNomeAluno": "",
      "outDataNascimento": "",
      "outNumRA": "",
      "outDigitoRA": "",
      "outSiglaUFRA": "",
      "outGemeo": ""
    }
  ],
  "outDocumentos": {
    "outCodINEP": "",
    "outCPF": "",
    "outNumDoctoCivil": "",
    "outDigitoDoctoCivil": "",
    "outUFDoctoCivil": "",
    "outDataEmissaoDoctoCivil": "",
    "outNumNIS": "",
    "outDataEmissaoCertidao": "",
    "outNumeroCNS": "",
    "outCIN": "",
    "outDataEmissaoCIN": ""
  },
  "outJustificativaDocumentos": "",
  "outCertidaoNova": {
    "outCertMatr01": "",
    "outCertMatr02": "",
    "outCertMatr03": "",
    "outCertMatr04": "",
    "outCertMatr05": "",
    "outCertMatr06": "",
    "outCertMatr07": "",
    "outCertMatr08": "",
    "outCertMatr09": ""
  },
  "outCertidaoAntiga": {
    "outNumCertidao": "",
    "outNumLivroReg": "",
    "outFolhaRegNum": "",
    "outNomeMunComarca": "",
    "outUFComarca": "",
    "outDistritoNasc": ""
  },
  "outEnderecoResidencial": {
    "outLogradouro": "",
    "outNumero": "",
    "outAreaLogradouro": "",
    "outComplemento": "",
    "outBairro": "",
    "outNomeCidade": "",
    "outUFCidade": "",
    "outLatitude": "",
    "outLongitude": "",
    "outCep": "",
    "outCodMunicipioDNE": "",
    "outCodArea": "",
    "outCodLocalizacao": "",
    "outLocalizacaoDiferenciada": ""
  },
  "outEnderecoIndicativo": {
    "outLogradouro": "",
    "outNumero": "",
    "outBairro": "",
    "outNomeCidade": "",
    "outUFCidade": "",
    "outLatitude": "",
    "outLongitude": "",
    "outCep": ""
  },
  "outTelefones": [
    {
      "outDDDNumero": "",
      "outNumero": "",
      "outTipoTelefone": "",
      "outDescTipoTelefone": "",
      "outComplemento": "",
      "outSMS": ""
    }
  ],
  "outIndigena": {
    "outCodigoTipoIndigena": "",
    "outDescricaoTipoIndigena": ""
  },
  "outDeficiencia": {
    "outFlDeficiencia": "",
    "outMobilidadeReduzida": "",
    "outTipoMobilidadeReduzida": "",
    "outDataInicioMobilidadeReduzida": "",
    "outDataFimMobilidadeReduzida": "",
    "outCodigoNivelSuporte": "",
    "outProfissionalApoioEscolarResponse": {
      "outProfissionalApoioEscolar": "",
      "outAtividadeDiaria": "",
      "outAtividadeEscolar": "",
      "outApoioHigiene": "",
      "outApoioLocomocao": "",
      "outApoioAlimentacao": "",
      "outApoioBanheiro": "",
      "outApoioMedicamento": "",
      "outDataInicioVigenciaAtividadeDiaria": "",
      "outDataFimVigenciaAtividadeDiaria": "",
      "outDataInicioVigenciaAtividadeEscolar": "",
      "outDataFimVigenciaAtividadeEscolar": ""
    },
    "outFlTranstornoAprendizagem": "",
    "outFlInvestigacaoDeficiencia": "",
    "outListaComprovantePNE": [
      {
        "outDescricaoTipoInformacao": "",
        "outDataReferencia": "",
        "outObservacoes": ""
      }
    ]
  },
  "outListaNecessidadesEspeciais": [
    {
      "outCodNecesEspecial": "",
      "outNomeNecesEspecial": ""
    }
  ],
  "outRecursoAvaliacao": {
    "outGuiaInterprete": "",
    "outInterpreteLibras": "",
    "outLeituraLabial": "",
    "outNenhum": "",
    "outProvaAmpliada": "",
    "outTamanhoFonte": "",
    "outProvaBraile": "",
    "outAuxilioTranscricao": "",
    "outAuxilioLeitor": "",
    "outProvaVideoLibras": "",
    "outCdAudioDefVisual": "",
    "outProvaLinguaPortuguesa": ""
  }
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

- A pesquisa e realizada exclusivamente pelo RA do aluno (inNumRA e inSiglaUFRA obrigatorios).
- O retorno inclui dados pessoais, documentos, certidoes (nova e antiga), endereco residencial e indicativo, telefones, informacoes de deficiencia, necessidades especiais e recursos de avaliacao.
- O campo outIrmaos retorna uma lista de irmaos do aluno com seus respectivos RAs.
- Os campos outFlTranstornoAprendizagem e outFlInvestigacaoDeficiencia utilizam valores "S" (Sim) e "N" (Nao).
