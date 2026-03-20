# NCA029 - Validar Ficha Aluno

> **Versao:** 1.0 | **Ultima atualizacao:** 18/11/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | ValidarFichaAluno |
| **Codigo** | NCA029 |
| **Descricao** | Analisar a ficha de um determinado aluno e retornar todas as inconsistencias nelas para um posterior ajuste. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/ValidarFichaAluno` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/Aluno/ValidarFichaAluno` |
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

---

## Exemplo de Request

**Query Parameters:**

```
/Aluno/ValidarFichaAluno?inNumRA=&inDigitoRA=&inSiglaUFRA=
```

---

## Parametros de Saida

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outSucesso | Alfanumerico (100) | Parametro preenchido caso a validacao seja efetivada com sucesso |
| outErro | Alfanumerico (1000) | Retorno de erros de negocios ou erros de execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
    "outSucesso": "",
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

- A pesquisa e realizada pelo RA do aluno (inNumRA e inSiglaUFRA obrigatorios).
- O metodo analisa a ficha do aluno e retorna inconsistencias encontradas no campo outErro.
- Se a ficha estiver consistente, o campo outSucesso sera preenchido.
- Utilizado para validacao previa antes de ajustes na ficha do aluno.
