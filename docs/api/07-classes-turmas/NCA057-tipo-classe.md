# NCA057 - Tipo Classe

> **Versao:** 1.0 | **Ultima atualizacao:** 09/05/2022 | **Autor:** Flavio J. Leamari

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | TipoClasse |
| **Codigo** | NCA057 |
| **Descricao** | Esse metodo tem como finalidade o retorno da relacao de tipos de Classe do sistema Cadastro de Alunos. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/TipoClasse` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/TipoClasse` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Nao ha parametros de entrada.**

---

## Exemplo de Request

```
GET /api/DadosBasicos/TipoClasse
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outTipoClasse | Alfanumerico | Relacao de tipos de classe no formato ARRAY [1 : N] |
| outCodTipoClasse | Alfanumerico (3) | Codigo identificador do tipo de classe |
| outDescTipoClasse | Alfanumerico (20) | Descricao do tipo de Classe |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outTipoClasse": [
    {
      "outCodTipoClasse": "",
      "outDescTipoClasse": ""
    }
  ],
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

- Este metodo retorna todos os tipos de classe cadastrados no sistema Cadastro de Alunos.
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
