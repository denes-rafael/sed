# NCA024 - Declaração de Matrícula

> Esse método tem como finalidade a geração da declaração de matrícula para alunos da rede estadual de ensino no ano-letivo corrente.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA024 |
| **Método HTTP** | GET |
| **URL** | `/Matricula/DeclaracaoMatricula` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token (gerado pelo método ValidarUsuario, expira em 30 minutos) |

## Parâmetros de Entrada (Request)

**Formato:** QUERY Parameters

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inNumRA | Alfanumérico (12) | Sim | Número do RA do aluno |
| inDigitoRA | Alfanumérico (2) | Não | Dígito do RA do aluno |
| inSiglaUFRA | Alfanumérico (2) | Sim | Sigla da UF do RA do aluno |
| inDataNascimento | Alfanumérico (10) | Sim | Data de nascimento do aluno |

## Exemplo de Request

```
GET /Matricula/DeclaracaoMatricula?inNumRA=&inDigitoRA=&inSiglaUFRA=&inDataNascimento=
```

## Parâmetros de Saída (Response)

**Formato:** JSON

### Dados do aluno

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outNumRA | Alfanumérico (12) | Número do RA |
| outDigitoRA | Alfanumérico (2) | Dígito do RA |
| outSiglaUFRA | Alfanumérico (2) | UF do RA |
| outDataNascimento | Alfanumérico (10) | Data de Nascimento do aluno (DD/MM/AAAA) |
| outNomeAluno | Alfanumérico (100) | Nome do aluno |
| outNumRG | Alfanumérico (14) | Número do RG |
| outDigitoRG | Alfanumérico (2) | Dígito do RG |
| outSiglaUFRG | Alfanumérico (2) | UF de emissão do RG |
| outNumRNE | Alfanumérico (15) | Número do RNE do aluno |

### Dados da matrícula

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outAnoLetivo | Alfanumérico (4) | Ano letivo |
| outNomeDiretoria | Alfanumérico (40) | Nome de diretoria de ensino |
| outNomeEscola | Alfanumérico (60) | Nome da escola |
| outNomeMunicipio | Alfanumérico (60) | Nome do município |
| outDescricaoTurno | Alfanumérico (30) | Descrição do turno da classe (turma) |
| outHoraInicial | Alfanumérico (5) | Horário do início da aula na classe (HH:MM) |
| outHoraFinal | Alfanumérico (5) | Horário do final da aula na classe (HH:MM) |
| outDescTipoEnsino | Alfanumérico (100) | Descrição do tipo de ensino da classe de matrícula |
| outTurma | Alfanumérico (100) | Descrição da turma |
| outCodSerieAno | Alfanumérico (2) | Código identificador da série ou ano da classe |
| outSituacaoAluno | Alfanumérico (20) | Situação do aluno |
| outTexto | Alfanumérico (200) | Diretriz da declaração compilando os campos dados pessoais do aluno e dados da matrícula |
| outDataInicioMatricula | Alfanumérico (10) | Data de início da matrícula do aluno na classe (DD/MM/AAAA) |
| outDataFimMatricula | Alfanumérico (10) | Data de encerramento da matrícula do aluno na classe (DD/MM/AAAA) |

### Dados do documento

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outArquivoPDF | Alfanumérico (10000) | Saída Base64 para a geração do PDF |
| outUrlArquivo | Alfanumérico (200) | URL do arquivo PDF para download |
| outImagemBrasaoSP | Alfanumérico (10000) | Saída Base64 para a geração da imagem do brasão do estado de SP |
| outImagemQrCode | Alfanumérico (10000) | Saída Base64 para a geração da imagem do QRCode e código de validação |
| outImagemAssinatura | Alfanumérico (10000) | Saída Base64 para a geração da imagem da assinatura do responsável pela matrícula |
| outNomeResponsavelPelaAssinatura | Alfanumérico (100) | Nome do responsável pela matrícula |
| outRgResponsavelPelaAssinatura | Alfanumérico (25) | RG do responsável pela matrícula |

### Outros parâmetros

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outNumRA": "",
  "outDigitoRA": "",
  "outSiglaUFRA": "",
  "outNumRG": "",
  "outDigitoRG": "",
  "outSiglaUFRG": "",
  "outNumRNE": "",
  "outDataNascimento": "",
  "outNomeAluno": "",
  "outAnoLetivo": "",
  "outNomeDiretoria": "",
  "outCodEscola": "",
  "outNomeEscola": "",
  "outNomeMunicipio": "",
  "outDescricaoTurno": "",
  "outHoraInicial": "",
  "outHoraFinal": "",
  "outDescTipoEnsino": "",
  "outTurma": "",
  "outCodSerieAno": "",
  "outSituacaoAluno": "",
  "outTexto": "",
  "outDataInicioMatricula": "",
  "outDataFimMatricula": "",
  "outUrlArquivo": "",
  "outImagemBrasaoSP": "",
  "outImagemQrCode": "",
  "outImagemAssinatura": "",
  "outNomeResponsavelPelaAssinatura": "",
  "outRgResponsavelPelaAssinatura": "",
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

- Apenas para alunos da rede estadual de ensino no ano-letivo corrente
- Retorna dados completos do aluno, da matrícula e imagens para composição do documento
- O campo outArquivoPDF retorna o PDF em formato Base64
- O campo outUrlArquivo fornece uma URL para download direto do PDF
- Inclui imagens em Base64: brasão do estado de SP, QRCode de validação e assinatura do responsável
