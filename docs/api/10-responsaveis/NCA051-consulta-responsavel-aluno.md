# NCA051 - Consultar Responsavel pelo Aluno

> Esse metodo tem como finalidade o retorno dos dados do responsavel pelo aluno cadastrado no sistema NCA a partir de uma pesquisa pelo do RG/UF, CPF ou RA/DG/UF do Aluno.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA051 |
| **Metodo HTTP** | GET |
| **URL** | `/Aluno/ConsultarResponsavelAluno` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

## Parametros de Entrada (Request)

Os parametros podem ser enviados via **BODY** ou **QUERY Parameters** (um dos grupos abaixo).

### Grupo: InDocumentosAluno

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| InDocumentosAluno | Alfanumerico | N/A | Grupo de documentos do aluno |
| inNRRG | Alfanumerico (15) | Opcional | RG do Aluno |
| inUFRG | Alfanumerico (02) | Opcional. Obrigatorio quando inNRRG informado | UF do RG do Aluno |
| inCPF | Alfanumerico (11) | Opcional | CPF do Aluno |

### Grupo: inAluno

| Parametro | Tipo | Obrigatorio | Descricao |
|-----------|------|-------------|-----------|
| inAluno | Alfanumerico | N/A | Grupo de dados do aluno |
| inNumRA | Alfanumerico (12) | Opcional | RA do Aluno |
| inDigitoRa | Alfanumerico (01) | Opcional. Obrigatorio quando inNumRA informado | Digito do RA do aluno |
| inSiglaUFRa | Alfanumerico (02) | Opcional. Obrigatorio quando inRA informado | UF do RA do Aluno |

## Exemplo de Request

**Query Parameters:**

```
/Aluno/ConsultarResponsavelAluno?inNRRG=&inUFRG=&inCPF=&inNumRA=&inDigitoRa=&inSiglaUFRA=
```

**Body:**

```json
{
  "inAluno": {
    "inNumRA": "string",
    "inDigitoRA": "string",
    "inSiglaUFRA": "string"
  },
  "inDocumentos": {
    "inCPF": "string",
    "inNRRG": "string",
    "inUFRG": "string"
  }
}
```

## Parametros de Saida (Response)

| Parametro | Tipo | Descricao |
|-----------|------|-----------|
| outSucesso | Alfanumerico | Indica sucesso da operacao |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outRequestID | Alfanumerico | Identificador da requisicao |
| **outResponsaveis** | **Alfanumerico** | **Grupo de Dados dos Responsaveis** |
| outCPF | Alfanumerico (11) | CPF do Responsavel |
| outNome | Alfanumerico (60) | Nome do Responsavel |
| outTipoOrigem | Alfanumerico (02) | Codigo de Origem no Brasil |
| outRNM | Alfanumerico | RNM do Responsavel |
| outNRRG | Alfanumerico (12) | RG do Responsavel |
| outDigitoRG | Alfanumerico (02) | Digito do RG do Responsavel |
| outUFRG | Alfanumerico (02) | UF do RG do Responsavel |
| outCodResponsabilidade | Alfanumerico | 1 - Padrasto, 2 - Avo, 3 - Avo, 4 - Madrasta, 5 - Irma, 6 - Mae, 7 - Pai, 8 - Tio, 9 - Tia, 10 - Irmao, 11 - Conjuge, 12 - Guardiao |
| outResponsabilidade | Alfanumerico | Descricao da Responsabilidade |
| outLogin | Alfanumerico | Login do Responsavel |
| outCodSexo | Alfanumerico (01) | 1 - Masculino / 2 - Feminino |
| outCodEstadoCivil | Alfanumerico (01) | 1 - Solteiro, 2 - Casado, 3 - Viuvo, 4 - Divorciado, 5 - Separado, 8 - Uniao Estavel |
| outEmailResponsavel | Alfanumerico | E-mail do Responsavel |
| outDataNascimento | Alfanumerico (10) | Data de Nascimento do Responsavel |
| outCidadeNascimento | Alfanumerico (30) | Cidade de Nascimento do Responsavel |
| outUFNascimento | Alfanumerico (02) | UF de Nascimento do Responsavel |
| outNomePaisNascimento | Alfanumerico | Nome do Pais de Nascimento do Responsavel |
| outCodPaisNascimento | Alfanumerico | Codigo do Pais de Nascimento do Responsavel |
| **outEnderecoResidencial** | **Alfanumerico** | **Grupo de Enderecos** |
| outAreaLogradouro | Alfanumerico (10) | Area do logradouro Urbana / Rural |
| outLogradouro | Alfanumerico (60) | Logradouro responsavel |
| outNumero | Alfanumerico (10) | N. logradouro responsavel |
| outComplemento | Alfanumerico | Complemento logradouro responsavel |
| outBairro | Alfanumerico (30) | Bairro logradouro responsavel |
| outNomeCidade | Alfanumerico (60) | Cidade logradouro responsavel |
| outUFCidade | Alfanumerico (30) | UF logradouro responsavel |
| outLatitude | Alfanumerico (30) | Latitude logradouro responsavel |
| outLongitude | Alfanumerico (30) | Longitude logradouro responsavel |
| outCep | Alfanumerico (08) | CEP logradouro responsavel |
| **outLstTelefone** | **Alfanumerico** | **Grupo de Telefones do Responsavel** |
| outDDDNumero | Alfanumerico (03) | DDD telefone responsavel |
| outNumero | Alfanumerico (10) | Telefone responsavel |
| outTipoTelefone | Alfanumerico (01) | 1 - Residencial, 2 - Comercial, 3 - Celular, 4 - Recado, 5 - Celular Principal |
| OutDescTipoTelefone | Alfanumerico (20) | Descricao tipo telefone responsavel (Residencial / Comercial / Celular / Recado) |
| outComplemento | Alfanumerico | Complemento do telefone |
| OutDataAlteracao | Alfanumerico (19) | Data da alteracao. Formato: DD/MM/AAAA HH:MM:SS. Obs.: Esse campo nao pertence ao Grupo de Telefones do Responsavel |

## Exemplo de Response

```json
{
  "outSucesso": "string",
  "outErro": "string",
  "outRequestID": "string",
  "outResponsaveis": [
    {
      "outCPF": "string",
      "outNome": "string",
      "outTipoOrigem": "string",
      "outRNM": "string",
      "outNRRG": "string",
      "outDigitoRG": "string",
      "outUFRG": "string",
      "outCodResponsabilidade": "string",
      "outResponsabilidade": "string",
      "outLogin": "string",
      "outCodSexo": "string",
      "outCodEstadoCivil": "string",
      "outEmailResponsavel": "string",
      "outDataNascimento": "string",
      "outCidadeNascimento": "string",
      "outUFNascimento": "string",
      "outNomePaisNascimento": "string",
      "outCodPaisNascimento": "string",
      "outEnderecoResidencial": {
        "outAreaLogradouro": "string",
        "outLogradouro": "string",
        "outNumero": "string",
        "outComplemento": "string",
        "outBairro": "string",
        "outNomeCidade": "string",
        "outUFCidade": "string",
        "outLatitude": "string",
        "outLongitude": "string",
        "outCep": "string"
      },
      "outLstTelefone": [
        {
          "outDDDNumero": "string",
          "outNumero": "string",
          "outTipoTelefone": "string",
          "outDescTipoTelefone": "string",
          "outComplemento": "string"
        }
      ],
      "outDataAlteracao": "string"
    }
  ]
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
- A pesquisa pode ser feita por RG/UF, CPF ou RA/DG/UF do Aluno
- Os parametros podem ser enviados via BODY ou QUERY Parameters
- O campo `OutDataAlteracao` nao pertence ao Grupo de Telefones do Responsavel
- Formato da data de alteracao: DD/MM/AAAA HH:MM:SS
