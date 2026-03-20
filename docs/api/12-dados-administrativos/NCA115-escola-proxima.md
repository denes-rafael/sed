# NCA115 - Escola Proxima

> **Versao:** 1.0 | **Ultima atualizacao:** 13/03/2020 | **Autor:** Alexandre Mendes

## Informacoes Gerais

| Campo | Valor |
|---|---|
| **Nome da API** | EscolaProxima |
| **Codigo** | NCA115 |
| **Descricao** | Retorno do codigo da escola participante do processo de compatibilizacao que esteja mais proxima, em distancia linear, do endereco residencial do aluno. |
| **Metodo HTTP** | GET |
| **URL (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/EscolaProxima` |
| **URL (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api/DadosBasicos/EscolaProxima` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Autenticacao** | Authorization: Bearer Token (gerado pelo metodo ValidarUsuario, expira em 30 minutos) |

---

## Parametros de Entrada

**Formato:** QUERY Parameters

| Parametro | Tipo/Tamanho | Obrigatorio | Descricao |
|---|---|---|---|
| inLatitude | Alfanumerico (17) | Sim | Latitude do endereco residencial do aluno |
| inLongitude | Alfanumerico (17) | Sim | Longitude do endereco residencial do aluno |

---

## Exemplo de Request

**Query Parameters:**
```
GET /DadosBasicos/EscolaProxima?inLatitude=&inLongitude=
```

---

## Parametros de Saida (Response)

| Parametro | Tipo/Tamanho | Descricao |
|---|---|---|
| outCodEscola | Alfanumerico (7) | Codigo da CIE da escola mais proxima da residencia do aluno |
| outErro | Alfanumerico (1000) | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Codigo identificador da requisicao processada |

---

## Exemplo de Response

```json
{
  "outCodEscola": "",
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

- Retorna apenas a escola participante do processo de compatibilizacao mais proxima em distancia linear.
- A busca e baseada nas coordenadas geograficas (latitude/longitude) do endereco residencial do aluno.
