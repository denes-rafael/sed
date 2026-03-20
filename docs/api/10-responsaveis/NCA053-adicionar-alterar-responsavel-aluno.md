# NCA053 - Adicionar/Alterar Responsavel pelo Aluno

> Esse metodo tem como finalidade incluir/alterar dados do responsavel pelo aluno no sistema NCA a partir de informacoes basicas do responsavel pelo Aluno.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA053 |
| **Metodo HTTP** | POST |
| **URL** | `/Aluno/AdicionarAlterarResponsavelAluno` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

## Parametros de Entrada (Request)

Os parametros devem ser enviados via **BODY Parameters**.

### Grupo: inAluno

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inAluno | Alfanumerico | N/A | Dados do RA do Aluno |
| inNumRA | Alfanumerico (12) | Opcional | RA do Aluno |
| inDigitoRA | Alfanumerico (01) | Opcional. Obrigatorio quando inNumRA informado | Digito do RA do aluno |
| inSiglaUFRA | Alfanumerico (02) | Opcional. Obrigatorio quando inRA informado | UF do RA do Aluno |

### Grupo: inDocumentosAluno

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inDocumentosAluno | Alfanumerico | N/A | Documentos do aluno |
| inCPF | Alfanumerico (11) | Opcional | CPF do Aluno |
| inNRRG | Alfanumerico (15) | Opcional | RG do Aluno |
| inUFRG | Alfanumerico (02) | Opcional. Obrigatorio quando inNRRG informado | UF do RG do Aluno |

### Grupo: inResponsavel

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inResponsavel | Alfanumerico | N/A | Dados do Responsavel |
| inCPF | Alfanumerico (11) | Opcional | CPF do Responsavel |
| inNome | Alfanumerico (60) | Obrigatorio | Nome do Responsavel |
| inTipoOrigem | Alfanumerico (01) | Obrigatorio | 1 - Brasileiro, 2 - Estrangeiro, 3 - Bras. Nascido Exterior |
| inRNM | Alfanumerico (8) | Obrigatorio quando inTipoOrigem = estrangeiro | RNM do Responsavel |
| inNRRG | Alfanumerico (15) | Obrigatorio | RG do Responsavel |
| inDigitoRG | Alfanumerico (02) | Obrigatorio | Digito do RG do Responsavel |
| inUFRG | Alfanumerico (02) | Obrigatorio | UF do RG do Responsavel |
| inCodResponsabilidade | Alfanumerico (01) | Obrigatorio | 1 - Padrasto, 2 - Avo, 3 - Avo, 4 - Madrasta, 5 - Irma, 6 - Mae, 7 - Pai, 8 - Tio, 9 - Tia, 10 - Irmao, 11 - Conjuge, 12 - Guardiao |
| inCodSexo | Alfanumerico (10) | Obrigatorio | Sexo do Responsavel: "1" Masculino, "2" Feminino |
| inCodEstadoCivil | Alfanumerico (01) | Obrigatorio | 1 - Solteiro, 2 - Casado, 3 - Viuvo, 4 - Divorciado, 5 - Separado, 8 - Uniao Estavel |
| inEmailResponsavel | Alfanumerico (30) | Obrigatorio | E-mail do Responsavel |
| inDataNascimento | Alfanumerico (10) | Obrigatorio | Nascimento do Responsavel (DD/MM/AAAA) |
| inCidadeNascimento | Alfanumerico (30) | Obrigatorio | Cidade de nascimento do Responsavel |
| inUFNascimento | Alfanumerico (02) | Obrigatorio | UF de nascimento do Responsavel |
| inNomePaisNascimento | Alfanumerico (60) | Opcional | Nome do Pais de nascimento |
| inCodPaisNascimento | Alfanumerico | Opcional | Codigo do Pais de nascimento |

### Grupo: inEnderecoResidencial

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inEnderecoResidencial | Alfanumerico | N/A | Endereco Residencial |
| inLogradouro | Alfanumerico (60) | Obrigatorio | Logradouro do Responsavel |
| inNumero | Alfanumerico (10) | Obrigatorio | N. do logradouro do Responsavel |
| inBairro | Alfanumerico (60) | Obrigatorio | Bairro do logradouro do Responsavel |
| inNomeCidade | Alfanumerico (60) | Obrigatorio | Cidade do logradouro do Responsavel |
| inUFCidade | Alfanumerico (02) | Obrigatorio | UF da cidade do logradouro do Responsavel |
| inComplemento | Alfanumerico (60) | Opcional | Complemento do logradouro do Responsavel |
| inCep | Alfanumerico (08) | Obrigatorio | CEP do logradouro do Responsavel |
| inAreaLogradouro | Alfanumerico (01) | Obrigatorio | Area do logradouro do Responsavel: 0 - Urbana, 1 - Rural |
| inLatitude | Alfanumerico (30) | Obrigatorio | Latitude do logradouro do Responsavel |
| inLongitude | Alfanumerico (30) | Obrigatorio | Longitude do logradouro do Responsavel |

### Grupo: inLstTelefone

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inLstTelefone | Alfanumerico | N/A | Lista de Telefones |
| inTipoTelefone | Alfanumerico (01) | Obrigatorio | 1 - Residencial, 2 - Comercial, 3 - Celular, 4 - Recado, 5 - Celular Principal |
| inDDDNumero | Alfanumerico (03) | Obrigatorio | DDD do telefone do Responsavel |
| inNumero | Alfanumerico (15) | Obrigatorio | Telefone do Responsavel |
| inComplemento | Alfanumerico (30) | Opcional | Complemento do Telefone do Responsavel |

## Exemplo de Request

```json
{
  "inResponsavel": {
    "inCPF": "string",
    "inNome": "string",
    "inTipoOrigem": "string",
    "inRNM": "string",
    "inNRRG": "string",
    "inDigitoRG": "string",
    "inUFRG": "string",
    "inCodResponsabilidade": "string",
    "inCodSexo": "string",
    "inCodEstadoCivil": "string",
    "inEmailResponsavel": "string",
    "inDataNascimento": "string",
    "inCidadeNascimento": "string",
    "inUFNascimento": "string",
    "inNomePaisNascimento": "string",
    "inCodPaisNascimento": "string",
    "inEnderecoResidencial": {
      "inLogradouro": "string",
      "inNumero": "string",
      "inBairro": "string",
      "inNomeCidade": "string",
      "inUFCidade": "string",
      "inComplemento": "string",
      "inCep": "string",
      "inAreaLogradouro": "string",
      "inLatitude": "string",
      "inLongitude": "string"
    },
    "inLstTelefone": [
      {
        "inTipoTelefone": 0,
        "inDDDNumero": "string",
        "inNumero": "string",
        "inComplemento": "string"
      }
    ]
  },
  "inAluno": {
    "inNumRA": "string",
    "inDigitoRA": "string",
    "inSiglaUFRA": "string"
  },
  "inDocumentosAluno": {
    "inCPF": "string",
    "inNRRG": "string",
    "inUFRG": "string"
  }
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outSucesso | Alfanumerico (1000) | Retorno de sucesso da execucao do metodo |
| outRequestID | Alfanumerico | Identificador da requisicao processada |

## Exemplo de Response

```json
{
  "outSucesso": "string",
  "outErro": "string",
  "outRequestID": "string"
}
```

## Codigos de Erro

| Codigo | Mensagem | Descricao |
|--------|----------|-----------|
| 200 | OK | Requisicao processada com sucesso: Retorno de dados |
| 200 | Erro de negocio | Requisicao processada com sucesso: Erro de negocio, outErro preenchido |
| 401 | Unauthorized | Requisicao rejeitada: Token invalido ou expirado |
| 500 | Internal Server Error | Erro de infraestrutura: outErro preenchido |

## Observacoes

- O token de acesso e gerado pelo metodo **ValidarUsuario** e tem um tempo de expiracao de **30 minutos**
- O metodo permite tanto adicionar quanto alterar dados do responsavel
- A identificacao do aluno pode ser feita via RA/DG/UF ou RG/UF ou CPF
- O campo `inAreaLogradouro` aceita: 0 - Urbana, 1 - Rural
- O campo `inTipoTelefone` aceita: 1 - Residencial, 2 - Comercial, 3 - Celular, 4 - Recado, 5 - Celular Principal
- O campo `inCodEstadoCivil` aceita: 1 - Solteiro, 2 - Casado, 3 - Viuvo, 4 - Divorciado, 5 - Separado, 8 - Uniao Estavel
- O campo `inRNM` e obrigatorio quando `inTipoOrigem` = estrangeiro (2)
