# NCA001 - Validar Usuario

> Esse metodo tem como finalidade a validacao de usuario no ambiente Secretaria Digital e a geracao de Token de acesso, utilizado pelos demais metodos do ambiente.

## Informacoes Gerais

| Campo | Valor |
|-------|-------|
| **Codigo** | NCA001 |
| **Metodo HTTP** | GET |
| **URL Base (Producao)** | `https://integracaosed.educacao.sp.gov.br/ncaapi/api` |
| **URL Base (Homologacao)** | `https://homologacaointegracaosed.educacao.sp.gov.br/ncaapi/api` |
| **Chamada** | `/Usuario/ValidarUsuario` |
| **Content-Type** | application/json; charset=UTF-8 |
| **Protocolo** | REST |
| **Autenticacao** | Authorization: Basic Auth (Usuario e Senha fornecidos pela equipe responsavel pelo ambiente Integracao) |

## Status de Resposta

| Status | Descricao |
|--------|-----------|
| **200** | Requisicao processada com sucesso: Retorno de dados |
| **200** | Requisicao processada com sucesso: Erro de negocio, outErro preenchido |
| **500** | Erro de infraestrutura: outErro preenchido |

## Parametros de Entrada (Request)

Nenhum parametro de entrada (VAZIO).

## Exemplo de Request

```json
{}
```

## Parametros de Saida (Response)

| Parametro | Tipo de Dado / Tamanho | Regras de Validacao | Descricao |
|-----------|------------------------|---------------------|-----------|
| outAutenticacao | Alfanumerico (5000) | Nao se aplica. | TOKEN de acesso. Valido por 30 (trinta) minutos e limitado a 05 (cinco) por usuario. |
| outUsuario | Alfanumerico (30) | Nao se aplica. | Nome do usuario validado |
| outErro | Alfanumerico (1000) | Nao se aplica. | Parametro destinado para retorno de erros de negocios ou erros execucao do metodo |
| outProcessoID | Numerico | Nao se aplica. | Codigo identificador da requisicao processada |

## Exemplo de Response

```json
{
    "outAutenticacao": "",
    "outUsuario": "",
    "outRequestID": ""
}
```

## Codigos de Erro

| Codigo | Mensagem | Descricao |
|--------|----------|-----------|
| Nao documentado | Nao documentado | Erros de negocio ou execucao sao retornados no campo `outErro`. Erros de infraestrutura retornam Status 500 com `outErro` preenchido. |

## Observacoes

- O Token de acesso gerado e valido por **30 minutos**.
- O limite de tokens ativos por usuario e de **05 (cinco)**.
- As credenciais de acesso (usuario e senha para Basic Auth) sao fornecidas pela equipe responsavel pelo ambiente de Integracao.
- O campo `outErro` e utilizado tanto para erros de negocio (Status 200) quanto para erros de infraestrutura (Status 500).
- O tipo de dado do servico e `ValidarUsuario`.
- Versao do documento: 1.1 (25/06/2019).
