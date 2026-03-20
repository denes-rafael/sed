# NCA002 - Listar Alunos

> **Versao:** 1.2 | **Ultima atualizacao:** 17/06/2024 | **Autor:** Italo G.

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | ListarAlunos |
| **Codigo** | NCA002 |
| **Descricao** | Pesquisar e retornar dados de alunos cadastrados no sistema NCA. Permite pesquisas pelo nome do aluno (nome completo), pela filiacao e por tipos de documentos. O retorno sera uma lista com RA e dados pessoais do aluno (nomes do aluno, mae, pai e data de nascimento). |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/ListarAlunos` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/ListarAlunos` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY ou QUERY Parameters

### Grupo inFiltrosNomes (exclusivo para pesquisa por nomes)

> Combinacao de parametros e permitida para refinar o resultado. Combinacao de grupos nao e permitida.

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inFiltrosNomes | Alfanumerico | Opcional | Grupo exclusivo para pesquisa por nomes |
| inNomeAluno | Alfanumerico (100) | Opcional | Nome completo do aluno |
| inNomeSocial | Alfanumerico (100) | Opcional | Nome social do aluno |
| inNomeMae | Alfanumerico (100) | Opcional | Nome completo da mae do aluno (Filiacao 01) |
| inNomePai | Alfanumerico (100) | Opcional | Nome completo do pai do aluno (Filiacao 02) |

### Grupo inDocumentos (exclusivo para pesquisa por tipos de documentos)

> Combinacao de parametros e permitida apenas para documentos do mesmo tipo. Combinacao de grupos nao e permitida.

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDocumentos | Alfanumerico | Opcional | Grupo exclusivo para pesquisa por tipos de documentos |
| inNumRG | Alfanumerico (14) | Opcional | Numero do RG do aluno. Permitida combinacao com inDigitoRG e inUFRG |
| inDigitoRG | Alfanumerico (2) | Opcional | Digito do RG do aluno. Permitida combinacao com inNumRG e inUFRG |
| inUFRG | Alfanumerico (2) | Opcional | Sigla UF do RG do aluno. Permitida combinacao com inNumRG e inDigitoRG |
| inCPF | Alfanumerico (11) | Opcional | Numero do CPF do aluno. Combinacao com outros parametros nao e permitida |
| inNumNIS | Alfanumerico (11) | Opcional | Codigo NIS do aluno. Combinacao com outros parametros nao e permitida |
| inNumINEP | Alfanumerico (12) | Opcional | Codigo de identificacao do MEC. Combinacao com outros parametros nao e permitida |
| inNumCertidaoNova | Alfanumerico (32) | Opcional | Numero completo da certidao de nascimento (formato novo). Combinacao com outros parametros nao e permitida |

### Subgrupo CertidaoNasc (certidao de nascimento formato antigo)

> Combinacao de parametros e obrigatoria para execucao da pesquisa por esse tipo de documento.

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| CertidaoNasc | Alfanumerico | Opcional | Grupo exclusivo para pesquisa por certidao de nascimento (formato antigo) |
| inNumCertidaoNasc | Alfanumerico (6) | Opcional | Numero da certidao de nascimento |
| inLivro | Alfanumerico (4) | Opcional | Numero do livro de registro da certidao de nascimento |
| inFolha | Alfanumerico (4) | Opcional | Numero da folha |
| inDistritoCertidao | Alfanumerico (60) | Opcional | Distrito do cartorio |
| inMunicipioComarca | Alfanumerico (60) | Opcional | Municipio Comarca do cartorio |
| inUFComarca | Alfanumerico (2) | Opcional | Sigla UF do municipio comarca |
| inDataEmissaoCertidao | Alfanumerico (10) | Opcional | Data de emissao da certidao de nascimento |
| inCodMunicComarcaDNE | Alfanumerico (4) | Opcional | Cod. Munic. Comarca DNE |

### Outros Parametros

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inDataNascimento | Alfanumerico (10) | Opcional | Data de nascimento do aluno (DD/MM/AAAA). Quando informado, deve ser combinado com o grupo inFiltrosNomes para refinamento. Nao pertence ao grupo inDocumentos e subgrupo CertidaoNasc. |

---

## Exemplo de Request

**Body:**

```json
{
    "inFiltrosNomes": {
        "inNomeAluno": "",
        "inNomeSocial": "",
        "inNomeMae": "",
        "inNomePai": ""
    },
    "inDocumentos": {
        "inNumRG": "",
        "inDigitoRG": "",
        "inUFRG": "",
        "inCPF": "",
        "inNumNIS": "",
        "inNumINEP": "",
        "inNumCertidaoNova": "",
        "certidaoNasc": {
            "inNumCertidao": "",
            "inLivro": "",
            "inFolha": "",
            "inDistritoCertidao": "",
            "inMunicipioComarca": "",
            "inUFComarca": "",
            "inDataEmissaoCertidao": "",
            "inCodMunicComarcaDNE": ""
        }
    },
    "inDataNascimento": ""
}
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outListaMatriculas | Alfanumerico | Grupo de alunos no formato ARRAY [1 : N] |
| outNumRA | Alfanumerico (12) | Numero do RA |
| outDigitoRA | Alfanumerico (2) | Digito do RA |
| outSiglaUFRA | Alfanumerico (2) | UF do RA |
| outNomeAluno | Alfanumerico (100) | Nome completo do Aluno |
| outNomeMae | Alfanumerico (100) | Nome completo da Mae do Aluno (Filiacao 01) |
| outNomePai | Alfanumerico (100) | Nome completo do Pai do Aluno (Filiacao 02) |
| outNomeSocial | Alfanumerico (100) | Nome social do Aluno |
| outDataNascimento | Alfanumerico (10) | Data de Nascimento do Aluno (DD/MM/AAAA) |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outListaAlunos": [
        {
            "outNumRA": "",
            "outDigitoRA": "",
            "outSiglaUFRA": "",
            "outNomeAluno": "",
            "outNomeMae": "",
            "outNomePai": "",
            "outNomeSocial": "",
            "outDataNascimento": ""
        }
    ],
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

- Pesquisa por nomes (grupo `inFiltrosNomes`) e pesquisa por documentos (grupo `inDocumentos`) sao mutuamente exclusivas; nao e permitido combinar grupos.
- Dentro do grupo `inDocumentos`, a combinacao de parametros e permitida apenas para documentos do mesmo tipo (ex: RG com seus complementos).
- O parametro `inDataNascimento` somente pode ser combinado com o grupo `inFiltrosNomes`.
- A pesquisa por certidao de nascimento no formato antigo (subgrupo `CertidaoNasc`) exige o preenchimento de todos os parametros do subgrupo.
