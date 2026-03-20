# NCA043 - Atestado de Eliminação de Matérias

> Esse método tem como finalidade a emissão do atestado de eliminação de matérias para candidatos no formato base64.

## Informações Gerais

| Campo | Valor |
|-------|-------|
| **Código** | NCA043 |
| **Método HTTP** | GET |
| **URL** | `/Boletim/AtestadoEliminacaoMaterias` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticação** | Authorization: Bearer Token (gerado pelo método ValidarUsuario, expira em 30 minutos) |

## Parâmetros de Entrada (Request)

**Formato:** BODY ou QUERY Parameters (um dos parâmetros abaixo)

| Parâmetro | Tipo | Obrigatório | Descrição |
|-----------|------|-------------|-----------|
| inCPF | Alfanumérico (11) | Opcional | Número do CPF do candidato. Obrigatório quando RG/DT Nascimento não informado |
| inNumRG | Alfanumérico (14) | Opcional | Número do RG do candidato. Obrigatório quando CPF não informado |
| inDataNascimento | Alfanumérico (10) | Opcional | Formato: DD/MM/AAAA. Obrigatório quando informado RG |
| inTipoEnsino | Alfanumérico (3) | Opcional | Tipo de Ensino |

## Exemplo de Request

```
GET /Boletim/AtestadoEliminacaoMaterias?inCpf=&inNumRG=&inDataNascimento=&inTipoEnsino=
```

## Parâmetros de Saída (Response)

**Formato:** JSON

### Grupo: OutListaCandidatos (Array [1:N])

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| OutListaCandidatos | Alfanumérico | Grupo de Atestados ARRAY [1:N] |
| outArquivoPDF | Alfanumérico (10000) | Saída Base64 para geração do atestado |
| outQtdeDiscipEliminadas | Numérico | Total de disciplinas eliminadas |
| OutAreaConhecimento | Alfanumérico | Grupo de Atestados ARRAY [1:N] |
| outArquivoPDF104mm | Alfanumérico (10000) | Saída Base64 para geração do atestado (formato 104mm) |

### Outros parâmetros

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| idProcesso | Numérico | Número de Identificação do Processo |
| idService | Numérico | Indicador de status: 1=Não é possível emitir o documento, solicite seu Atestado. 2=Todas as matérias eliminadas, solicite o certificado de conclusão. 3=Todas as matérias eliminadas, solicite o histórico. 4=Todas as matérias eliminadas, solicite o histórico. |
| outSucesso | Alfanumérico (1000) | Parâmetro destinado para retorno de negócios |
| outErro | Alfanumérico (1000) | Parâmetro destinado para retorno de erros de negócios ou erros execução do método |
| outProcessoID | Numérico | Código identificador da requisição processada |

## Exemplo de Response

```json
{
  "outListaCandidatos": [
    {
      "outArquivoPDF": "",
      "outQtdeDiscipEliminadas": "",
      "outAreaConhecimento": [],
      "outArquivoPDF104mm": ""
    }
  ],
  "outSucesso": "",
  "idProcesso": "",
  "idService": "",
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
- O campo idService indica ações a tomar: 1=Não é possível emitir, solicite atestado. 2=Matérias eliminadas, solicite certificado de conclusão. 3 e 4=Matérias eliminadas, solicite o histórico.
- O campo outArquivoPDF104mm foi adicionado na versão 1.3 para impressão em totem Poupatempo
- A versão 1.5 adequou o documento à API vigente (sem alteração no código da API)
