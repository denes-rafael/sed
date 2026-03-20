# NCA127 - Consulta Escolas Nominais

> Esse método tem como finalidade o retorno da relação de escolas ativa na rede pública, utilizando um ou vários parâmetros combinados como filtro.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA127 |
| **Método HTTP** | GET |
| **URL** | `/DadosBasicos/ConsultaEscolasNominais` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token |

## Parâmetros de Entrada (Request)

> Pelo menos um dos parâmetros de entrada abaixo é obrigatório.

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inNomeEscola | Alfanumérico (72) | Não (mínimo 5 caracteres) | Nome da escola |
| inBairro | Alfanumérico (40) | Não (mínimo 5 caracteres) | Bairro do endereço da escola |
| inEndereco | Alfanumérico (100) | Não (mínimo 5 caracteres) | Endereço da escola |
| inMunicipio | Alfanumérico (60) | Não (mínimo 5 caracteres) | Município da escola |

## Exemplo de Request

```
GET /DadosBasicos/ConsultaEscolasNominais?inNomeEscola={inNomeEscola}&inBairro={inBairro}&inEndereco={inEndereco}&inMunicipio={inMunicipio}
```

## Parâmetros de Saída (Response)

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outEscolas | Alfanumérico | Grupo de unidades da escola no formato ARRAY [1 : N] |
| outEscolas.outCodEscola | Alfanumérico (4) | Código CIE da escola |
| outEscolas.outDescNomeEscola | Alfanumérico (60) | Nome completo da escola |
| outEscolas.outCodDiretoria | Alfanumérico (5) | Código identificador da diretoria |
| outEscolas.outDescNomeDiretoria | Alfanumérico (40) | Nome da diretoria de ensino |
| outEscolas.outTipoLogradouro | Alfanumérico (100) | Tipo do logradouro do endereço da escola |
| outEscolas.outDescEndereco | Alfanumérico (100) | Endereço da escola |
| outEscolas.outNumero | Alfanumérico (100) | Número da escola |
| outEscolas.outDescBairro | Alfanumérico (72) | Bairro do endereço da escola |
| outEscolas.outDescComplemento | Alfanumérico (40) | Complemento do endereço |
| outEscolas.outCodMunicipio | Alfanumérico (4) | Código DNE do município (código identificador padrão dos Correios) |
| outEscolas.outDescMunicipio | Alfanumérico (72) | Nome do município |
| outEscolas.outLatitude | Alfanumérico (100) | Latitude do endereço da escola |
| outEscolas.outLongitude | Alfanumérico (100) | Longitude do endereço da escola |
| outEscolas.outCodRedeEnsino | Alfanumérico (1) | Identificador da rede de ensino |
| outEscolas.outNomeRedeEnsino | Alfanumérico (20) | Nome da rede ensino |
| outEscolas.outCodDistrito | Alfanumérico | Código do Distrito |
| outEscolas.outNomeDistrito | Alfanumérico (60) | Nome do Distrito |
| outEscolas.outCEP | Alfanumérico (8) | Código de Endereçamento Postal |
| outSucesso | Alfanumérico (100) | Parâmetro destinado para retorno de sucesso |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outProcessID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outEscolas": [
    {
      "outCodEscola": "",
      "outDescNomeEscola": "",
      "outCodDiretoria": "",
      "outDescNomeDiretoria": "",
      "outTipoLogradouro": "",
      "outDescEndereco": "",
      "outNumero": "",
      "outDescBairro": "",
      "outDescComplemento": "",
      "outCodMunicipio": "",
      "outDescMunicipio": "",
      "outLatitude": "",
      "outLongitude": "",
      "outCodRedeEnsino": "",
      "outNomeRedeEnsino": "",
      "outCodDistrito": "",
      "outCEP": "",
      "outNomeDistrito": ""
    }
  ],
  "outSucesso": "string",
  "outErro": "string",
  "outProcessID": "string"
}
```

## Códigos de Erro

| Código | Mensagem | Descrição |
|--------|----------|-----------|
| 200 | OK | Requisição processada com sucesso: Retorno de dados |
| 200 | Erro de negócio | Requisição processada com sucesso: Erro de negócio, outErro preenchido |
| 401 | Unauthorized | Requisição rejeitada: Token inválido ou expirado |
| 500 | Internal Server Error | Erro de infraestrutura: outErro preenchido |

## Observações

- Token de acesso gerado pelo método ValidarUsuario com tempo de expiração de 30 minutos.
- Tipo de dado: ConsultaEscolasNominais
- Pelo menos um dos parâmetros de entrada é obrigatório.
- Todos os parâmetros de entrada requerem no mínimo 5 caracteres para efetuar a pesquisa.
- Parâmetros de entrada no formato QUERY Parameters.
