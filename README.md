# SED - Cadastro de Alunos REST API

Documentacao da API REST do Sistema de Cadastro de Alunos da Secretaria de Educacao do Estado de Sao Paulo (SEESP), organizada para consumo pelo **EducHub**.

## Ambientes

| Ambiente | URL Base |
|----------|----------|
| **Homologacao** | `https://homologacaointegracaosed.educacao.sp.gov.br/` |
| **Producao** | `https://integracaosed.educacao.sp.gov.br/` |

## Autenticacao

Todas as chamadas (exceto NCA001) requerem um token de autenticacao obtido via **Basic Auth** no endpoint [NCA001 - Validar Usuario](docs/api/01-autenticacao/NCA001-validar-usuario.md). O token tem validade de **30 minutos** e limite de **5 tokens simultaneos** por usuario.

O token deve ser enviado no header `Authorization` das requisicoes subsequentes.

## Documentacao Original

[Pagina de documentacao oficial (PDFs)](https://homologacaointegracaosed.educacao.sp.gov.br/documentacao/CadastrodeAlunos/REST/)

Os servicos NCA003, NCA016, NCA017, NCA020, NCA045, NCA046 e NCA048 desta copia foram conferidos com os PDFs oficiais em 29/10/2026.

---

## Indice de Endpoints

### 01 - Autenticacao
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA001](docs/api/01-autenticacao/NCA001-validar-usuario.md) | Validar Usuario | GET |

### 02 - Alunos - Consultas
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA002](docs/api/02-alunos-consultas/NCA002-listar-alunos.md) | Listar Alunos | GET |
| [NCA003](docs/api/02-alunos-consultas/NCA003-exibir-ficha-aluno.md) | Exibir Ficha Aluno | GET |
| [NCA016](docs/api/02-alunos-consultas/NCA016-ficha-aluno.md) | Ficha Aluno (Inclusao/Alteracao) | POST |
| [NCA018](docs/api/02-alunos-consultas/NCA018-consulta-ra.md) | Consulta RA | GET |
| [NCA019](docs/api/02-alunos-consultas/NCA019-consulta-publica.md) | Consulta Publica | GET |
| [NCA021](docs/api/02-alunos-consultas/NCA021-consulta-ra-impressao.md) | Consulta RA Impressao | GET |
| [NCA029](docs/api/02-alunos-consultas/NCA029-validar-ficha-aluno.md) | Validar Ficha Aluno | GET |

### 03 - Alunos - Matriculas
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA004](docs/api/03-alunos-matriculas/NCA004-listar-matriculas-ra.md) | Listar Matriculas RA | GET |
| [NCA005](docs/api/03-alunos-matriculas/NCA005-exibir-matricula-classe-ra.md) | Exibir Matricula Classe RA | GET |
| [NCA011](docs/api/03-alunos-matriculas/NCA011-matricular-aluno.md) | Matricular Aluno | POST |
| [NCA030](docs/api/03-alunos-matriculas/NCA030-remanejar-matricula.md) | Remanejar Matricula | POST |
| [NCA031](docs/api/03-alunos-matriculas/NCA031-reclassificar-matricula.md) | Reclassificar Matricula | POST |
| [NCA032](docs/api/03-alunos-matriculas/NCA032-trocar-aluno-entre-classes.md) | Trocar Aluno Entre Classes | POST |
| [NCA034](docs/api/03-alunos-matriculas/NCA034-excluir-matricula.md) | Excluir Matricula | POST |
| [NCA035](docs/api/03-alunos-matriculas/NCA035-baixar-matricula.md) | Baixar Matricula | POST |
| [NCA036](docs/api/03-alunos-matriculas/NCA036-estornar-baixa-matricula.md) | Estornar Baixa Matricula | POST |
| [NCA037](docs/api/03-alunos-matriculas/NCA037-classificar-nr-chamada.md) | Classificar Nr Chamada | POST |
| [NCA038](docs/api/03-alunos-matriculas/NCA038-alterar-nr-chamada.md) | Alterar Nr Chamada | POST |

### 04 - Alunos - Inscricoes
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA006](docs/api/04-alunos-inscricoes/NCA006-listar-inscricoes-aluno.md) | Listar Inscricoes Aluno | GET |
| [NCA007](docs/api/04-alunos-inscricoes/NCA007-listar-inscricoes-escola.md) | Listar Inscricoes Escola | GET |
| [NCA010](docs/api/04-alunos-inscricoes/NCA010-inscrever-aluno.md) | Inscrever Aluno | POST |
| [NCA015](docs/api/04-alunos-inscricoes/NCA015-cancelar-inscricao-definicao.md) | Cancelar Inscricao/Definicao | POST |

### 05 - Alunos - Transferencias
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA012](docs/api/05-alunos-transferencias/NCA012-transferencia.md) | Transferencia | POST |
| [NCA013](docs/api/05-alunos-transferencias/NCA013-definicao.md) | Definicao | POST |

### 06 - Alunos - Manutencao
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA017](docs/api/06-alunos-manutencao/NCA017-manutencao.md) | Manutencao Ficha Aluno | POST |
| [NCA025](docs/api/06-alunos-manutencao/NCA025-manutencao-complementar.md) | Manutencao Inscricoes | POST |
| [NCA027](docs/api/06-alunos-manutencao/NCA027-associar-irmao.md) | Associar Irmao | POST |
| [NCA028](docs/api/06-alunos-manutencao/NCA028-desassociar-irmao.md) | Desassociar Irmao | POST |
| [NCA033](docs/api/06-alunos-manutencao/NCA033-baixar-aluno-falecimento.md) | Baixar Aluno Falecimento | POST |

### 07 - Classes e Turmas
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA008](docs/api/07-classes-turmas/NCA008-relacao-classes.md) | Relacao de Classes | GET |
| [NCA009](docs/api/07-classes-turmas/NCA009-formacao-classe.md) | Formacao da Classe | GET |
| [NCA045](docs/api/07-classes-turmas/NCA045-incluir-turma-classe.md) | Incluir Turma Classe | POST |
| [NCA046](docs/api/07-classes-turmas/NCA046-manutencao-turma-classe.md) | Manutencao Turma Classe | POST |
| [NCA047](docs/api/07-classes-turmas/NCA047-excluir-turma-classe.md) | Excluir Turma Classe | POST |
| [NCA048](docs/api/07-classes-turmas/NCA048-consultar-turma-classe.md) | Consultar Turma Classe | GET |
| [NCA057](docs/api/07-classes-turmas/NCA057-tipo-classe.md) | Tipo Classe | GET |

### 08 - Rendimento e Notas
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA020](docs/api/08-rendimento-notas/NCA020-concluintes.md) | Concluintes | GET |
| [NCA026](docs/api/08-rendimento-notas/NCA026-consulta-boletim.md) | Consulta Boletim | GET |
| [NCA049](docs/api/08-rendimento-notas/NCA049-incluir-rendimento-aluno.md) | Incluir Rendimento Aluno | POST |
| [NCA050](docs/api/08-rendimento-notas/NCA050-manutencao-rendimento-aluno.md) | Manutencao Rendimento Aluno | POST |
| [NCA122](docs/api/08-rendimento-notas/NCA122-consultar-rendimento-classe.md) | Consultar Rendimento Classe | GET |

### 09 - Documentos
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA022](docs/api/09-documentos/NCA022-comprovante-inscricao.md) | Comprovante Inscricao | GET |
| [NCA023](docs/api/09-documentos/NCA023-comprovante-inscricao-transferencia.md) | Comprovante Inscricao Transferencia | GET |
| [NCA024](docs/api/09-documentos/NCA024-declaracao-matricula.md) | Declaracao Matricula | GET |
| [NCA041](docs/api/09-documentos/NCA041-certificado-conclusao.md) | Certificado Conclusao | GET |
| [NCA042](docs/api/09-documentos/NCA042-historico-candidato.md) | Historico Candidato | GET |
| [NCA043](docs/api/09-documentos/NCA043-atestado-eliminacao-materias.md) | Atestado Eliminacao Materias | GET |

### 10 - Responsaveis
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA051](docs/api/10-responsaveis/NCA051-consulta-responsavel-aluno.md) | Consulta Responsavel Aluno | GET |
| [NCA052](docs/api/10-responsaveis/NCA052-excluir-responsavel-aluno.md) | Excluir Responsavel Aluno | POST |
| [NCA053](docs/api/10-responsaveis/NCA053-adicionar-alterar-responsavel-aluno.md) | Adicionar/Alterar Responsavel Aluno | POST |

### 11 - Fotos e Carteirinha
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA054](docs/api/11-fotos-carteirinha/NCA054-gerar-carteirinha-aluno.md) | Gerar Carteirinha Aluno | POST |
| [NCA055](docs/api/11-fotos-carteirinha/NCA055-consultar-foto-aluno.md) | Consultar Foto Aluno | GET |
| [NCA056](docs/api/11-fotos-carteirinha/NCA056-cadastrar-foto-aluno.md) | Cadastrar Foto Aluno | POST |

### 12 - Dados Administrativos
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA101](docs/api/12-dados-administrativos/NCA101-diretorias.md) | Diretorias | GET |
| [NCA102](docs/api/12-dados-administrativos/NCA102-municipios-por-diretoria.md) | Municipios por Diretoria | GET |
| [NCA103](docs/api/12-dados-administrativos/NCA103-escolas-por-municipio.md) | Escolas por Municipio | GET |
| [NCA104](docs/api/12-dados-administrativos/NCA104-tabelas-dominio.md) | Tabelas de Dominio | GET |
| [NCA105](docs/api/12-dados-administrativos/NCA105-pais.md) | Paises | GET |
| [NCA106](docs/api/12-dados-administrativos/NCA106-necessidades-especiais.md) | Necessidades Especiais | GET |
| [NCA107](docs/api/12-dados-administrativos/NCA107-tipo-ensino.md) | Tipo Ensino | GET |
| [NCA108](docs/api/12-dados-administrativos/NCA108-eixo-novotec.md) | Eixo NovoTec | GET |
| [NCA109](docs/api/12-dados-administrativos/NCA109-municipios-sp.md) | Municipios SP | GET |
| [NCA110](docs/api/12-dados-administrativos/NCA110-escolas-ceeja.md) | Escolas CEEJA | GET |
| [NCA111](docs/api/12-dados-administrativos/NCA111-escolas.md) | Escolas | GET |
| [NCA112](docs/api/12-dados-administrativos/NCA112-uf.md) | UF | GET |
| [NCA113](docs/api/12-dados-administrativos/NCA113-municipios-por-uf.md) | Municipios por UF | GET |
| [NCA114](docs/api/12-dados-administrativos/NCA114-unidades-por-escola.md) | Unidades por Escola | GET |
| [NCA115](docs/api/12-dados-administrativos/NCA115-escola-proxima.md) | Escola Proxima | GET |
| [NCA116](docs/api/12-dados-administrativos/NCA116-consulta-escolas-proxima-novotec.md) | Escolas Proxima NovoTec | GET |
| [NCA117](docs/api/12-dados-administrativos/NCA117-consulta-escolas-proxima-cel.md) | Escolas Proxima CEL | GET |
| [NCA118](docs/api/12-dados-administrativos/NCA118-habilitacao-por-escola-novotec.md) | Habilitacao por Escola NovoTec | GET |
| [NCA119](docs/api/12-dados-administrativos/NCA119-habilitacao-por-escola-cel.md) | Habilitacao por Escola CEL | GET |

### 13 - Consultas Avancadas
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA123](docs/api/13-consultas-avancadas/NCA123-consultar-atividade-complementar.md) | Consultar Atividade Complementar | GET |
| [NCA124](docs/api/13-consultas-avancadas/NCA124-siau-consultar-legislacao.md) | SIAU - Consultar Legislacao | GET/POST |
| [NCA125](docs/api/13-consultas-avancadas/NCA125-siau-consultar-assunto.md) | SIAU - Consultar Assunto | GET |
| [NCA126](docs/api/13-consultas-avancadas/NCA126-consulta-quadro-resumo.md) | Consulta Quadro Resumo | GET |
| [NCA127](docs/api/13-consultas-avancadas/NCA127-consulta-escolas-nominais.md) | Consulta Escolas Nominais | GET |

### 14 - Povos Indigenas
| Codigo | Endpoint | Metodo |
|--------|----------|--------|
| [NCA143](docs/api/14-povos-indigenas/NCA143-povos-indigenas.md) | Povos Indigenas | GET |

---

**Total: 78 endpoints documentados em 14 categorias**
