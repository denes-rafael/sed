# NCA104 - Tabelas Dominio

> **Versao:** 1.4 | **Ultima atualizacao:** 18/04/2022 | **Autor:** Flavio J. Leamari

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | TabelasDominio |
| **Codigo** | NCA104 |
| **Descricao** | Retorno das tabelas de dominio do sistema Cadastro de Alunos (NCA). |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/TabelasDominio` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/TabelasDominio` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

Nao ha parametros de entrada.

---

## Exemplo de Request

```
GET /DadosBasicos/TabelasDominio
```

Nao ha parametros de entrada.

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| **outCorRaca** | Alfanumerico | Relacao de Cor/Raca no formato ARRAY [1 : N] |
| outCodCorRaca | Alfanumerico (1) | Identificador da cor ou raca |
| outDescCorRaca | Alfanumerico (20) | Descricao da cor ou raca |
| **outNacionalidade** | Alfanumerico | Relacao de Nacionalidades no formato ARRAY [1 : N] |
| outCodNacionalidade | Alfanumerico (1) | Identificador de nacionalidade |
| outDescNacionalidade | Alfanumerico (30) | Descricao da nacionalidade |
| **outLocalizacaoDiferencada** | Alfanumerico | Relacao de Localizacoes Diferenciadas no formato ARRAY [1 : N] |
| outCodLocalizacao | Alfanumerico (1) | Identificador do tipo da localizacao |
| outDescLocalizacao | Alfanumerico (100) | Descricao da localizacao |
| **outDeficiencia** | Alfanumerico | Tipos de deficiencia no formato ARRAY [1 : N] |
| outCodDeficiencia | Alfanumerico (1) | Identificador do tipo de deficiencia |
| outDescDeficiencia | Alfanumerico (15) | Descricao da deficiencia |
| **outJustificativaDoc** | Alfanumerico | Tipos de justificativa no formato ARRAY [1 : N] |
| outCodJustificativa | Alfanumerico (1) | Identificador do tipo da justificativa |
| outDescJustificativa | Alfanumerico (100) | Descricao da justificativa |
| **outSexo** | Alfanumerico | Tipos de sexo no formato ARRAY [1 : N] |
| outCodSexo | Alfanumerico (1) | Identificador do tipo de sexo |
| outDescSexo | Alfanumerico (20) | Descricao do sexo |
| ~~outTipoInscricao~~ | ~~Alfanumerico~~ | ~~Relacao de tipos de inscricao no formato ARRAY [1 : N]~~ (removido na v1.2) |
| ~~outCodTipoInscricao~~ | ~~Alfanumerico (1)~~ | ~~Identificador da inscricao~~ |
| ~~outDescTipoInscricao~~ | ~~Alfanumerico (20)~~ | ~~Descricao do tipo de inscricao~~ |
| **outFaseDefinicao** | Alfanumerico | Relacao de tipos de definicao no formato ARRAY [1 : N] |
| outCodTipoInscricao | Alfanumerico (1) | Identificador da inscricao |
| outDescTipoInscricao | Alfanumerico (20) | Descricao do tipo |
| **outFaseInscricao** | Alfanumerico | Relacao de tipos de inscricao no formato ARRAY [1 : N] |
| outCodTipoInscricao | Alfanumerico (1) | Identificador da inscricao |
| outDescTipoInscricao | Alfanumerico (20) | Descricao do tipo |
| **outFaseMovimentacao** | Alfanumerico | Relacao de tipos de movimentacao no formato ARRAY [1 : N] |
| outCodTipoInscricao | Alfanumerico (1) | Identificador da inscricao |
| outDescTipoInscricao | Alfanumerico (20) | Descricao do tipo |
| **outRedeEnsino** | Alfanumerico | Relacao de rede de ensino no formato ARRAY [1 : N] |
| outCodRedeEnsino | Alfanumerico (1) | Identificador da rede de ensino |
| outNomeRedeEnsino | Alfanumerico (20) | Nome da rede ensino |
| **outTurno** | Alfanumerico | Relacao de turnos no formato ARRAY [1 : N] |
| outCodTurno | Alfanumerico (1) | Identificador do turno |
| outDescricaoTurno | Alfanumerico (20) | Descricao do turno |
| **outMotivoTransferencia** | Alfanumerico | Relacao de motivo de transferencia no formato ARRAY [1 : N] |
| outCodMotivo | Alfanumerico (1) | Identificador do motivo |
| outDescMotivo | Alfanumerico (100) | Descricao do motivo |
| **outOpcaoNoturno** | Alfanumerico | Relacao de justificativa para optar pelo periodo noturno no formato ARRAY [1 : N] |
| outCodOpcao | Alfanumerico (1) | Identificador da opcao |
| outDescOpcao | Alfanumerico (30) | Descricao da opcao |
| **outTipoTelefone** | Alfanumerico | Relacao de tipos de telefones no formato ARRAY [1 : N] |
| outCodTipoTelefone | Alfanumerico (1) | Identificador do tipo |
| outDescTipoTelefone | Alfanumerico (20) | Descricao do tipo |
| **outProvaAmpliada** | Alfanumerico | Relacao de fontes para prova ampliada no formato ARRAY [1 : N] |
| outTamanhoFonte | Alfanumerico (2) | Tamanho de fontes disponiveis |
| **outAreaLogradouro** | Alfanumerico | Relacao de tipos de areas no formato ARRAY [1 : N] |
| outCodArea | Alfanumerico (1) | Identificador da area do logradouro |
| outDescArea | Alfanumerico (20) | Descricao da area do logradouro |
| **outTipoOrigem** | Alfanumerico | Relacao Tipo Origem ARRAY [1 : N] |
| outCodTipoOrigem | Alfanumerico (1) | Identificador da origem |
| outDescTipoOrigem | Alfanumerico (40) | Descricao da origem |
| **outResponsabilidade** | Alfanumerico | Relacao Tipo responsabilidade ARRAY [1 : N] |
| outCodResponsabilidade | Alfanumerico (2) | Identificador da responsabilidade |
| outDescResponsabilidade | Alfanumerico (20) | Descricao da responsabilidade |
| **outEstadoCivil** | Alfanumerico | Relacao estado civil ARRAY [1 : N] |
| outCodEstadoCivil | Alfanumerico (1) | Identificador do estado civil |
| outDescEstadoCivil | Alfanumerico (20) | Descricao do estado civil |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outCorRaca": [
    {
      "outCodCorRaca": "string",
      "outDescCorRaca": "string"
    }
  ],
  "outNacionalidade": [
    {
      "outCodNacionalidade": "string",
      "outDescNacionalidade": "string"
    }
  ],
  "outLocalizacaoDiferencada": [
    {
      "outCodLocalizacao": "string",
      "outDescLocalizacao": "string"
    }
  ],
  "outDeficiencia": [
    {
      "outCodDeficiencia": "string",
      "outDescDeficiencia": "string"
    }
  ],
  "outJustificativaDoc": [
    {
      "outCodJustificativa": "string",
      "outDescJustificativa": "string"
    }
  ],
  "outSexo": [
    {
      "outCodSexo": "string",
      "outDescSexo": "string"
    }
  ],
  "outFaseInscricao": [
    {
      "outCodTipoInscricao": "string",
      "outDescTipoInscricao": "string"
    }
  ],
  "outFaseDefinicao": [
    {
      "outCodTipoInscricao": "string",
      "outDescTipoInscricao": "string"
    }
  ],
  "outFaseMovimentacao": [
    {
      "outCodTipoInscricao": "string",
      "outDescTipoInscricao": "string"
    }
  ],
  "outRedeEnsino": [
    {
      "outCodRedeEnsino": "string",
      "outNomeRedeEnsino": "string"
    }
  ],
  "outTurno": [
    {
      "outCodTurno": "string",
      "outDescricaoTurno": "string"
    }
  ],
  "outMotivoTransferencia": [
    {
      "outCodMotivo": "string",
      "outDescMotivo": "string"
    }
  ],
  "outOpcaoNoturno": [
    {
      "outCodOpcao": "string",
      "outDescOpcao": "string"
    }
  ],
  "outTipoTelefone": [
    {
      "outCodTipoTelefone": "string",
      "outDescTipoTelefone": "string"
    }
  ],
  "outProvaAmpliada": [
    {
      "outTamanhoFonte": "string"
    }
  ],
  "outAreaLogradouro": [
    {
      "outCodArea": "string",
      "outDescArea": "string"
    }
  ],
  "outResponsabilidade": [
    {
      "outCodResponsabilidade": "string",
      "outDescResponsabilidade": "string"
    }
  ],
  "outEstadoCivil": [
    {
      "outCodEstadoCivil": "string",
      "outDescEstadoCivil": "string"
    }
  ],
  "outTipoOrigem": [
    {
      "outCodTipoOrigem": "string",
      "outDescTipoOrigem": "string"
    }
  ],
  "outProcessoID": "string"
}
```

---

## Codigos de Erro

| Codigo | Mensagem | Descricao |
|---|---|---|
| 200 | Sucesso | Requisicao processada com sucesso: Retorno de dados |
| 200 | Erro de negocio | Requisicao processada com sucesso: Erro de negocio, outErro preenchido |
| 401 | Token invalido ou expirado | Requisicao rejeitada: Token invalido ou expirado |
| 500 | Erro de infraestrutura | Erro de infraestrutura: outErro preenchido |

---

## Observacoes

- Nao ha parametros de entrada para este metodo.
- O parametro outTipoInscricao foi removido na versao 1.2.
- Na versao 1.1 foram incluidos os parametros outTipoTelefone e outProvaAmpliada.
- Na versao 1.2 foram incluidos os parametros outFaseInscricao, outFaseDefinicao e outFaseMovimentacao.
- Na versao 1.3 foi incluido o parametro outAreaLogradouro.
- Na versao 1.4 foram incluidos os campos outTipoOrigem, outResponsabilidade e outEstadoCivil.
