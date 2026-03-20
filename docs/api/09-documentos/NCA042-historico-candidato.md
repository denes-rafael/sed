# NCA042 - Histórico do Candidato

> Esse método tem como finalidade a emissão do histórico de candidatos no formato base64.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA042 |
| **Método HTTP** | GET |
| **URL** | `/Boletim/HistoricoCandidato` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token (gerado pelo método ValidarUsuario, expira em 30 minutos) |

## Parâmetros de Entrada (Request)

**Formato:** QUERY Parameters

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inCPF | Alfanumérico (11) | Opcional | Número do CPF do Candidato. Obrigatório quando RG/Nascimento não informado |
| inNumRG | Alfanumérico (14) | Opcional | Número do RG do Candidato. Obrigatório quando CPF não informado |
| inDataNascimento | Alfanumérico (10) | Opcional | Data de Nascimento do candidato (DD/MM/AAAA). Obrigatório quando RG informado |
| inTipoEnsino | Numérico (1) | Opcional | 1=Ensino Fundamental, 2=Ensino Médio |

## Exemplo de Request

```
GET /Boletim/HistoricoCandidato?inCPF=&inNumRG=&inDataNascimento=&inTipoEnsino=
```

## Parâmetros de Saída (Response)

**Formato:** JSON

### Grupo: outCandidato

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outCandidato | Alfanumérico | Grupos de dados do candidato |
| outNomeMaeCandidato | Alfanumérico (100) | Nome da mãe do candidato |
| outNomeCandidato | Alfanumérico (100) | Nome do candidato |
| outCPF | Alfanumérico (11) | Número do CPF do candidato |
| outRG | Alfanumérico (14) | Número do RG do candidato |
| outNrDigitoRG | Alfanumérico (2) | Dígito do RG |
| outSiglaUFRG | Alfanumérico (2) | Sigla UF do RG |
| outDataNascimento | Alfanumérico (10) | Data de Nascimento do candidato (DD/MM/AAAA) |

### Grupo: outListaHistoricoEnsinoFundamental (Array [1:N])

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outListaHistoricoEnsinoFundamental | Alfanumérico | Grupo de concursos de ensino fundamental no formato ARRAY [1:N] |
| outCodigoConcurso | Alfanumérico (3) | Código do concurso |
| outDescricaoConcurso | Alfanumérico (200) | Descrição do concurso |

### Grupo: outListaAreaNota (Array [1:N]) - dentro de cada concurso

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outListaAreaNota | Alfanumérico | Relação de disciplinas e notas no formato ARRAY [1:N] |
| outDescricaoArea | Alfanumérico (200) | Nome da área de conhecimento |
| outCodigoArea | Alfanumérico (4) | Código da área de conhecimento |
| outdNota | Alfanumérico (7) | Nota da prova |
| outFlAprovado | Alfanumérico (20) | Resultado da prova |
| outDataProva | Alfanumérico (10) | Data de realização da prova (DD/MM/AAAA) |
| outAnoConclusao | Alfanumérico (4) | Ano de conclusão |
| outDescricaoOrgao | Alfanumérico (40) | Órgão responsável |
| outUF | Alfanumérico (2) | UF do órgão responsável |

### Grupo: outListaHistoricoEnsinoMedio (Array [1:N])

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outListaHistoricoEnsinoMedio | Alfanumérico | Grupo de concursos de ensino médio no formato ARRAY [1:N] |
| outCodigoConcurso | Alfanumérico (3) | Código do concurso |
| outDescricaoConcurso | Alfanumérico (200) | Descrição do concurso |
| outListaAreaNota | Alfanumérico | Relação de disciplinas e notas no formato ARRAY [1:N] (mesma estrutura do ensino fundamental) |

### Outros parâmetros

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outArquivoPDF | Alfanumérico (10000) | Saída Base64 para a geração do certificado |
| outArquivoPDF104mm | Alfanumérico (10000) | Saída Base64 para a geração do certificado (formato 104mm) |
| outSucesso | Alfanumérico (100) | Parâmetro preenchido caso a inscrição seja efetivada |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outCandidato": {
    "outNomeMaeCandidato": "NOME DA MAE DO CANDIDATO",
    "outNomeCandidato": "NOME DO CANDIDATO",
    "outCPF": "12345678901",
    "outRG": "12345678",
    "outNrDigitoRG": "9",
    "outSiglaUFRG": "SP",
    "outDataNascimento": "18/08/1995",
    "outListaHistoricoEnsinoFundamental": [
      {
        "outCodigoConcurso": 596,
        "outDescricaoConcurso": "ENCCEJA 2019 EF",
        "outListaAreaNota": [
          {
            "outDescricaoArea": "LINGUA PORTUGUESA...",
            "outCodigoArea": "1",
            "outdNota": "130,00 / 8,75",
            "outFlAprovado": "APROVADO",
            "outDataProva": "25/08/2019",
            "outAnoConclusao": "2019",
            "outDescricaoOrgao": "ENCCEJA",
            "outUF": "SP"
          }
        ]
      }
    ],
    "outListaHistoricoEnsinoMedio": [],
    "outArquivoPDF": "Texto do PDF...",
    "outArquivoPDF104mm": "Texto do PDF no formato 104mm..."
  },
  "outSucesso": "OK",
  "outProcessoID": "495245322"
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
- A resposta contém listas separadas para ensino fundamental e ensino médio
- Cada concurso contém uma lista de áreas/notas com resultado individual
