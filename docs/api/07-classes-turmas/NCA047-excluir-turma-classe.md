# NCA047 - Excluir Turma Classe

> **Versao:** 1.1 | **Ultima atualizacao:** 02/12/2020 | **Autor:** Flavio L.

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | ExcluirTurmaClasse |
| **Codigo** | NCA047 |
| **Descricao** | Esse metodo tem como finalidade a exclusao de turmas (classes) seguindo as regras existentes no Sistema Cadastro de Alunos. |
| **Metodo HTTP** | POST |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/TurmaClasse/ExcluirTurmaClasse` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/TurmaClasse/ExcluirTurmaClasse` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** BODY

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inNrClasse | Alfanumerico (9) | Obrigatorio; comprimento maximo | Numero da classe a ser excluida |

---

## Exemplo de Request

```json
{
    "inNrClasse": ""
}
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outSucesso | Alfanumerico (9) | Sucesso |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outSucesso": "",
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

- A exclusao segue as regras existentes no Sistema Cadastro de Alunos.
- O campo inNumClasse foi alterado para inNrClasse na versao 1.1.
- O token de acesso tem validade de 30 minutos e deve ser obtido pelo metodo ValidarUsuario.
