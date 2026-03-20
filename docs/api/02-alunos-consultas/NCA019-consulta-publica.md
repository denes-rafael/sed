# NCA019 - Consulta Publica

> **Versao:** 1.3 | **Ultima atualizacao:** 05/04/2021 | **Autor:** Flavio J. Leamari

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | ConsultaPublica |
| **Codigo** | NCA019 |
| **Descricao** | Extrair e retornar ao solicitante as ultimas 05 matriculas na rede estadual, independentemente da situacao, de um determinado aluno utilizando como base da pesquisa o RA e a data de nascimento do mesmo. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Matricula/ConsultaPublica` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Matricula/ConsultaPublica` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** QUERY Parameters

### Grupo inAluno (identificador do aluno)

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inAluno | Alfanumerico | Obrigatorio | Grupo de dados identificador do aluno |
| inNumRA | Alfanumerico (12) | Obrigatorio | Numero do RA |
| inDigitoRA | Alfanumerico (2) | Opcional | Digito do RA |
| inSiglaUFRA | Alfanumerico (2) | Obrigatorio | UF do RA |
| inDataNascimento | Alfanumerico (10) | Obrigatorio | Data de nascimento do aluno (DD/MM/AAAA) |

---

## Exemplo de Request

**Query Parameters:**

```
/Matricula/ConsultaPublica?inNumRA=&inDigitoRA=&inSiglaUFRA=&inDataNascimento=
```

---

## Parametros de Saida

### Grupo outAluno

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outAluno | Alfanumerico | Grupo de dados pessoais do aluno |
| outNumRA | Alfanumerico (12) | Numero do RA |
| outDigitoRA | Alfanumerico (2) | Digito do RA |
| outSiglaUFRA | Alfanumerico (2) | UF do RA |

### Grupo outMatriculas (ARRAY [1 : N])

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outMatriculas | Alfanumerico | Grupo de matriculas do aluno no formato ARRAY [1 : N]. Matriculas em ordem decrescente de ano letivo |
| outCodEscola | Alfanumerico (7) | Codigo CIE da escola de matricula |
| outDescNomeAbrevEscola | Alfanumerico (60) | Nome abreviado da escola da matricula |
| outDescTipoEnsino | Alfanumerico (100) | Descricao do tipo de ensino da classe de matricula |
| outDescTurma | Alfanumerico (100) | Descricao da turma |
| outDescSitTranspEscolar | Alfanumerico (100) | Descricao da situacao do transporte escolar utilizado pelo aluno |
| outEnderecoEscola | Alfanumerico (100) | Endereco da escola de matricula |
| outTelefoneEscola | Alfanumerico (100) | Telefone da escola de matricula |

### Outros parametros de saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outArquivo | Alfanumerico (5000) | Saida Base64 para a geracao do PDF |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outConsultaPublica": [
        {
            "outAluno": {
                "outNomeAluno": "",
                "outDataNascimento": "",
                "outNomeSocial": ""
            },
            "outMatriculas": [
                {
                    "outAnoLetivo": "",
                    "outCodEscola": "",
                    "outDescNomeAbrevEscola": "",
                    "outDescTipoEnsino": "",
                    "outDescTurma": "",
                    "outDescSitTranspEscolar": "",
                    "outEnderecoEscola": "",
                    "outTelefoneEscola": ""
                }
            ]
        }
    ],
    "outArquivo": "",
    "outErro": "",
    "outProcessoID": ""
}
```

---

## Codigos de Erro

| Status | Descricao |
|---|---|
| 200 | Requisicao processada com sucesso: Retorno de dados |
| 200 | Requisicao processada com sucesso: Erro de negocio, outErro preenchido |
| 401 | Requisicao rejeitada: Token invalido ou expirado |
| 500 | Erro de infraestrutura: outErro preenchido |

---

## Observacoes

- Retorna as ultimas 05 matriculas na rede estadual, independentemente da situacao.
- A pesquisa e realizada pelo RA (inNumRA e inSiglaUFRA obrigatorios) e data de nascimento (inDataNascimento obrigatorio).
- O campo outArquivo contem a saida em Base64 para geracao de PDF.
- As matriculas sao retornadas em ordem decrescente de ano letivo.
