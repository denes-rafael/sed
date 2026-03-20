# NCA041 - Certificado de Conclusão

> Esse método tem como finalidade a emissão de certificados de conclusão de candidatos no formato base64.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA041 |
| **Método HTTP** | GET |
| **URL** | `/Boletim/CertificadoConclusao` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token (gerado pelo método ValidarUsuario, expira em 30 minutos) |

## Parâmetros de Entrada (Request)

**Formato:** QUERY Parameters

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inCPF | Alfanumérico (11) | Opcional | Número do CPF do Candidato. Obrigatório quando RG/Nascimento não informado |
| inNumRG | Alfanumérico (14) | Opcional | Número do RG do Candidato. Obrigatório quando CPF não informado |
| inDataNascimento | Alfanumérico (10) | Opcional | Data de Nascimento do candidato (DD/MM/AAAA). Obrigatório quando RG informado |
| inTipoEnsino | Numérico (1) | Opcional | 1=Indicador de emissão de certificado de ensino fundamental (obrigatório quando indicador do ensino médio não informado). 2=Indicador de emissão de certificado de ensino médio (obrigatório quando indicador do ensino fundamental não informado) |

## Exemplo de Request

```
GET /Boletim/CertificadoConclusao?inCPF=&inNumRG=&inDataNascimento=&inFundamental=&inMedio=
```

## Parâmetros de Saída (Response)

**Formato:** JSON

### Grupo: outListaCandidatos (Array [1:N])

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outListaCandidatos | Alfanumérico | Grupo de certificados do candidato no formato ARRAY [1:N] |
| outArquivoPDF | Alfanumérico (10000) | Saída Base64 para a geração do certificado |
| outArquivoPDF104mm | Alfanumérico (10000) | Saída Base64 para a geração do certificado (formato 104mm) |

### Outros parâmetros

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outSucesso | Alfanumérico (100) | Parâmetro preenchido caso a inscrição seja efetivada |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outListaCandidatos": [
    {
      "outArquivoPDF": "",
      "outArquivoPDF204mm": ""
    }
  ],
  "outSucesso": "",
  "outErro": "",
  "outProcessoID": ""
}
```

## Códigos de Erro

| Código | Mensagem | Descrição |
|--------|----------|-----------|
| 200 | OK | Requisição processada com sucesso: Retorno de dados |
| 200 | outErro preenchido | Requisição processada com sucesso: Erro de negócio |
| 401 | Token inválido ou expirado | Requisição rejeitada |
| 500 | outErro preenchido | Erro de infraestrutura |

## Observações

- Identificação do candidato: pode ser feita por CPF ou por RG + Data de Nascimento (mutuamente exclusivos conforme versão 1.4)
- inTipoEnsino: 1=Ensino Fundamental, 2=Ensino Médio
- O campo outArquivoPDF104mm foi adicionado na versão 1.3 para impressão em totem Poupatempo
- A resposta é um array (outListaCandidatos) que pode conter múltiplos certificados
