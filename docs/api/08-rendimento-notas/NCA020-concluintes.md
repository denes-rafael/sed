# NCA020 - Concluintes

> Esse método tem como finalidade extrair e retornar ao solicitante dados referentes à conclusão do ensino médio ou ensino técnico de um determinado aluno, apenas para alunos da rede estadual.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA020 |
| **Método HTTP** | GET |
| **URL** | `/Matricula/Concluintes` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token (gerado pelo método ValidarUsuario, expira em 30 minutos) |

## Parâmetros de Entrada (Request)

**Formato:** QUERY Parameters

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inNumRG | Alfanumérico (14) | Opcional | Número do RG do aluno, sem o dígito |
| inSiglaUFRG | Alfanumérico (2) | Opcional | Sigla da UF do RG do aluno |
| inNumRNE | Alfanumérico (8) | Opcional | Número do RNE do aluno, caso de nacionalidade estrangeira |
| inNumRA | Alfanumérico (12) | Opcional | Número do RA do aluno, sem o dígito |
| inNumVistoConfere | Alfanumérico (11) | Opcional | Identificação do ato de publicação |

## Exemplo de Request

```
GET /Matricula/Concluintes?inNumRG=&inSiglaUFRG=&inNumRNE=&inNumRA=&inNumVistoConfere=
```

## Parâmetros de Saída (Response)

**Formato:** JSON

### Grupo: outConsultaPublicaConcluinte (Array)

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outConsultaPublicaConcluinte | Alfanumérico | Grupo de dados concluinte |
| outNomeAluno | Alfanumérico (60) | Nome do aluno concluinte |
| outAnoLetivo | Alfanumérico (4) | Ano letivo |
| outNomeDiretoria | Alfanumérico (40) | Nome de diretoria de ensino |
| outNomeCompletoEscola | Alfanumérico (100) | Nome completa da escola |
| outNomeEscola | Alfanumérico (60) | Nome abreviado da escola |
| outDescricaoMunicipio | Alfanumérico (60) | Nome do município |
| outDescricaoArea | Alfanumérico (60) | Área do curso |
| outDescricaoModalidade | Alfanumérico (60) | Modalidade do curso |
| outNomeCursoProfissional | Alfanumérico (100) | Nome do curso profissionalizante |
| outAtoLegal | Alfanumérico (200) | Ato legal do curso |
| outAtoLegalEscola | Alfanumérico (200) | Ato legal da escola |
| outNomeSocial | Alfanumérico (60) | Nome social do aluno concluinte |
| outNumRG | Alfanumérico (15) | Número do RG do concluinte |
| outNumRNE | Alfanumérico (15) | Número do RNE do concluinte |
| outNumRA | Alfanumérico (12) | Número do RA do concluinte |
| outDigitoRGRNE | Alfanumérico (2) | Dígito do RG ou RNE |
| outSiglaUFRG | Alfanumérico (2) | Sigla UF do RG |
| outCodRedeEnsino | Alfanumérico (1) | Código identificador da rede de ensino |
| outNivelEnsinoPublico | Alfanumérico (60) | Nível de ensino |
| outNumeroAtoLegalEscola | Alfanumérico (200) | Número do ato legal da escola |
| outDataPublicacaoAtoLegalEscola | Alfanumérico (200) | Data de publicação do ato legal da escola |
| outNumVistoConfere | Alfanumérico (11) | Número do Visto Confere |
| outDataPublicacaoConcluinte | Alfanumérico (10) | Data de publicação |

### Grupo: outConsultaPublicaConcluinteCSU (Array)

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outConsultaPublicaConcluinteCSU | Alfanumérico | Grupo de dados Concluinte CSU |
| outNomeAluno | Alfanumérico (60) | Nome do aluno concluinte |
| outNumRG | Alfanumérico (15) | Número do RG do concluinte |
| ouDigitoRGRNE | Alfanumérico (2) | Dígito do RG ou RNE |
| outNumRNE | Alfanumérico (15) | Número do RNE do concluinte |
| outSiglaUFRG | Alfanumérico (2) | Sigla UF do RG |
| outAnoExpedicao | Alfanumérico (4) | Ano de expedição do certificado |
| outAnoConclusao | Alfanumérico (4) | Ano de conclusão |
| outNumVistoConfere | Alfanumérico (11) | Número do Visto Confere |
| outAtoLegal | Alfanumérico (4) | Ato legal |
| outOrgao | Alfanumérico (100) | Nome do órgão emissor |
| outGrau | Alfanumérico (10) | Nível de ensino |
| outSituacao | Alfanumérico (20) | Situação do certificado |
| Obs | Alfanumérico (100) | Informações adicionais |
| outDataPublicacao | Alfanumérico (10) | Data da publicação |
| SemEfeito | Boolean | Indica se a publicação está sem efeito |

### Outros parâmetros

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outArquivo | Alfanumérico (1000) | Saída Base64 para a geração do PDF |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outConsultaPublicaConcluinte": [
    {
      "outNomeAluno": "",
      "outAnoLetivo": "",
      "outNomeDiretoria": "",
      "outNomeCompletoEscola": "",
      "outNomeEscola": "",
      "outDescricaoMunicipio": "",
      "outDescricaoArea": "",
      "outDescricaoModalidade": "",
      "outNomeCursoProfissional": "",
      "outAtoLegal": "",
      "outAtoLegalEscola": "",
      "outNomeSocial": "",
      "outNumRG": "",
      "outNumRNE": "",
      "outNumRA": "",
      "outDigitoRGRNE": "",
      "outSiglaUFRG": "",
      "outCodRedeEnsino": "",
      "outNivelEnsinoPublico": "",
      "outNumeroAtoLegalEscola": "",
      "outDataPublicacaoAtoLegalEscola": "",
      "outNumVistoConfere": "",
      "outDataPublicacaoConcluinte": ""
    }
  ],
  "outConsultaPublicaCsuConcluinte": [
    {
      "outNomeAluno": "",
      "outNumRG": "",
      "ouDigitoRGRNE": "",
      "outNumRNE": "",
      "outSiglaUFRG": "",
      "outAnoExpedicao": "",
      "outAnoConclusao": "",
      "outNumVistoConfere": "",
      "outAnoLegal": "",
      "outOrgao": "",
      "outGrau": "",
      "outSituacao": "",
      "Obs": "",
      "outDataPublicacao": ""
    }
  ],
  "outArquivo": "",
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

- Apenas para alunos da rede estadual
- O campo SemEfeito (booleano) indica se a publicação está sem efeito (adicionado na versão 1.3)
- Os parâmetros de entrada são todos opcionais (query parameters)
- O campo outArquivo retorna o PDF em formato Base64
