# NCA101 - Diretorias

> **Versao:** 1.0 | **Ultima atualizacao:** 13/09/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | Diretorias |
| **Codigo** | NCA101 |
| **Descricao** | Retorno da relacao de diretorias de ensino estaduais existentes no sistema Cadastro de Alunos (NCA). |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/Diretorias` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/Diretorias` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

Nao ha parametros de entrada.

---

## Exemplo de Request

```
GET /DadosBasicos/Diretorias
```

Nao ha parametros de entrada.

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outDiretorias | Alfanumerico | Grupo de diretorias no formato ARRAY [1 : N] |
| outCodDiretoria | Alfanumerico (5) | Codigo identificador da diretoria |
| outDescNomeDiretoria | Alfanumerico (40) | Nome da diretoria de ensino |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outDiretorias": [
    {
      "outCodDiretoria": "",
      "outDescNomeDiretoria": ""
    }
  ],
  "outErro": "",
  "outProcessoID": ""
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
- O retorno e uma lista de todas as diretorias de ensino estaduais cadastradas no NCA.
