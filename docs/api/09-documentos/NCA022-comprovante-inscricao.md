# NCA022 - Comprovante de Inscrição

> Esse método tem como finalidade a geração do comprovante de inscrição no ensino fundamental ou médio (no formato base64) para alunos que estejam fora da rede pública.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA022 |
| **Método HTTP** | GET |
| **URL** | `/Inscricao/ComprovanteInscricao` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token (gerado pelo método ValidarUsuario, expira em 30 minutos) |

## Parâmetros de Entrada (Request)

**Formato:** QUERY Parameters

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inAluno | Alfanumérico | Sim | Grupo de dados identificador do aluno |
| inNumRA | Alfanumérico (12) | Sim | Número do RA |
| inDigitoRA | Alfanumérico (2) | Não | Dígito do RA |
| inSiglaUFRA | Alfanumérico (2) | Sim | UF do RA |
| inAnoLetivo | Alfanumérico (4) | Sim | Ano letivo da inscrição |
| inTipoInscricao | Alfanumérico (1) | Sim | Tipo de inscrições: 4=Inscrição de Aluno Fora da Rede Pública (Ensino Fundamental), 7=Inscrição de Aluno Fora da Rede Pública (Ensino Médio) |

## Exemplo de Request

```
GET /Inscricao/ComprovanteInscricao?inNumAluno=&inDigitoRA=&inSiglaUFRA=&inAnoLetivo=&inTipoInscricao=
```

## Parâmetros de Saída (Response)

**Formato:** JSON

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| outArquivo | Alfanumérico (5000) | Saída Base64 para a geração do PDF |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
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

- Apenas para alunos fora da rede pública
- Tipos de inscrição: 4=Ensino Fundamental, 7=Ensino Médio
- O campo outArquivo retorna o comprovante em formato Base64 para geração do PDF
