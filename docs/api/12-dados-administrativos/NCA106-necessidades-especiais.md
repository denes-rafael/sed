# NCA106 - Necessidades Especiais

> **Versao:** 1.0 | **Ultima atualizacao:** 26/09/2019 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | NecessidadesEspeciais |
| **Codigo** | NCA106 |
| **Descricao** | Retorno da relacao de necessidades especiais cadastradas no sistema Cadastro de Alunos (NCA). |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/NecessidadesEspeciais` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/NecessidadesEspeciais` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

Nao ha parametros de entrada.

---

## Exemplo de Request

```
GET /DadosBasicos/NecessidadesEspeciais
```

Nao ha parametros de entrada.

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outNecessidadesEspeciais | Alfanumerico | Relacao de necessidades especiais no formato ARRAY [1 : N] |
| outCodNecesEspecial | Alfanumerico (3) | Identificador da necessidade |
| outNomeNecesEspecial | Alfanumerico (40) | Descricao da necessidade |
| outTipoNecesEspecial | Alfanumerico (1) | Identificador do tipo da necessidade: 1 - Deficiencias, 2 - Transtornos globais do desenvolvimento, 3 - Altas habilidades / superdotacao |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outNecessidadesEspeciais": [
    {
      "outCodNecesEspecial": "",
      "outNomeNecesEspecial": "",
      "outTipoNecesEspecial": ""
    }
  ],
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
- Tipos de necessidade especial: 1 - Deficiencias, 2 - Transtornos globais do desenvolvimento, 3 - Altas habilidades / superdotacao.
