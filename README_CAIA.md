# CAIA — Prontuário Digital Interno

> **Status:** Planejamento e levantamento de requisitos  
> **Tipo:** Projeto acadêmico de extensão / proposta de sistema interno  
> **Instituição atendida:** CAIA  
> **Uso previsto:** Exclusivamente na rede interna autorizada da instituição

## Sobre o projeto

O **Prontuário Digital Interno do CAIA** é uma proposta de aplicação web local para apoiar o registro, a organização e a consulta de informações de acompanhamento dos assistidos pelos profissionais autorizados da instituição.

A iniciativa surgiu a partir de uma demanda registrada na ata de reunião de **28 de setembro de 2026**: determinadas informações não são inseridas no sistema da rede pública e permanecem em registros físicos. A proposta busca avaliar a digitalização desses registros, preservando o sigilo profissional e a proteção dos dados.

**Importante:** o projeto está em fase de estudo de viabilidade. As funcionalidades, tecnologias e infraestrutura descritas a seguir são sugestões iniciais e dependem de validação com o CAIA. Nenhum dado pessoal real deve ser inserido em protótipos ou ambientes de desenvolvimento.

## Objetivo

Desenvolver e avaliar um protótipo de prontuário digital interno que facilite o trabalho dos profissionais do CAIA, com acesso restrito, rastreabilidade e armazenamento local protegido.

### Objetivos específicos

- Levantar necessidades com psicólogos, assistentes sociais e responsáveis pela instituição.
- Mapear os fluxos atuais de registro, consulta e arquivamento.
- Definir perfis de acesso e regras de sigilo por categoria de informação.
- Projetar um sistema web acessível pela rede local, sem exposição à internet.
- Implementar e testar um MVP utilizando exclusivamente dados fictícios.
- Documentar requisitos, riscos, instalação, operação e procedimentos de recuperação.

## Escopo inicial proposto (MVP)

| Módulo | Descrição | Situação |
| --- | --- | --- |
| Autenticação | Acesso individual de usuários autorizados | Proposto |
| Gestão de assistidos | Cadastro e consulta de registros | Proposto |
| Registro de atendimentos | Inclusão e consulta de acompanhamentos | Proposto |
| Histórico | Linha do tempo de registros autorizados | Proposto |
| Controle de acesso | Permissões por função e necessidade de acesso | Proposto |
| Auditoria | Registro de acessos e alterações relevantes | Proposto |
| Administração | Gestão controlada de usuários e permissões | Proposto |
| Backup e restauração | Rotinas protegidas e testadas | A definir |

**Fora do escopo inicial:** aplicativo para celular, acesso remoto, integração automática com sistemas públicos e migração integral de prontuários físicos. Qualquer ampliação depende de aprovação específica.

## Arquitetura proposta

A solução deverá operar em **rede local cabeada e isolada**, sujeita à avaliação da infraestrutura existente no CAIA.

```text
[Computador — Psicologia] ---------┐
[Computador — Serviço Social] -----+---- [Switch de rede]
[Computador — Administração] ------┘           |
                                               |
                                     [Servidor local CAIA]
                                               |
                                  [Aplicação + Banco de dados]
```

- O acesso previsto será feito por navegador, nos computadores autorizados.
- A aplicação e o banco de dados ficarão em equipamento local protegido.
- Não haverá publicação de portas ou serviços na internet.
- A proposta inicial exclui conexões por Wi-Fi e Bluetooth, conforme a demanda registrada na reunião.
- O isolamento da rede, a proteção física e os mecanismos de recuperação deverão ser testados antes de qualquer uso institucional.

> Rede isolada **não elimina** riscos de acesso indevido, falhas de equipamento, malware ou perda de dados.

## Tecnologias consideradas

| Camada | Sugestão | Observação |
| --- | --- | --- |
| Interface | React, HTML e CSS | A confirmar após definição do escopo |
| API e regras de negócio | Python + Django | Inclui recursos de autenticação e administração |
| Banco de dados | PostgreSQL | Armazenamento relacional local |
| Servidor | Ubuntu Server | Equipamento mantido dentro da instituição |
| Rede | Ethernet + switch | Segmentação e isolamento a validar |

A escolha final dependerá das competências da equipe, dos equipamentos disponíveis e dos requisitos levantados.

## Privacidade e segurança

Como o sistema poderá envolver dados pessoais sensíveis de crianças e adolescentes, a segurança deve orientar todas as etapas do projeto.

Medidas previstas para avaliação e implementação:

- Contas individuais e senhas armazenadas com algoritmos adequados de hash.
- Princípio do menor privilégio e separação entre registros conforme o sigilo profissional.
- Proteção criptográfica dos dados em repouso e em trânsito na rede local.
- Auditoria de acessos e alterações, com proteção dos próprios registros de auditoria.
- Sessões autenticadas, expiração por inatividade e procedimentos de revogação de acesso.
- Backups criptografados, armazenamento seguro e testes de restauração.
- Atualizações e manutenção planejadas sem abrir acesso externo não autorizado.
- Definição institucional das regras de retenção, exclusão, responsabilidade e resposta a incidentes.
- Avaliação de conformidade com a **LGPD** e com normas de sigilo profissional aplicáveis.

**Acesso interno não significa acesso irrestrito:** anotações e documentos específicos poderão exigir permissões diferentes, a serem definidas com os profissionais e responsáveis competentes.

## Etapas previstas

| Semana | Atividade |
| --- | --- |
| 1 | Levantamento de requisitos e infraestrutura |
| 2 | Definição de escopo, perfis de acesso e modelagem inicial |
| 3 | Preparação do ambiente e estrutura do banco de dados |
| 4 | Implementação inicial do back-end e autenticação |
| 5 | Desenvolvimento das telas e integração |
| 6 | Implementação de registros, permissões e auditoria |
| 7 | Testes funcionais, de segurança e recuperação |
| 8 | Documentação, demonstração e avaliação de próximos passos |

Este cronograma é **estimativo** e considera a entrega de um protótipo, não a liberação de um sistema definitivo para dados reais.

## Informações pendentes do CAIA

- [ ] Quantidade de computadores e condições de uso.
- [ ] Existência de rede cabeada, switch e equipamentos de servidor.
- [ ] Número de profissionais e perfis de acesso necessários.
- [ ] Campos dos prontuários e fluxos atuais de trabalho.
- [ ] Categorias de registros sujeitas a sigilo específico.
- [ ] Responsáveis institucionais por autorizações e proteção de dados.
- [ ] Necessidades de backup, manutenção e continuidade operacional.
- [ ] Aprovação do escopo e critérios de aceite do protótipo.

## Como executar

**Ainda não disponível.** Os comandos de instalação, variáveis de ambiente, configuração do banco de dados e inicialização do sistema serão documentados quando a estrutura do código estiver definida.

## Diretrizes para desenvolvimento

- Utilizar somente **dados fictícios ou sintéticos** durante o desenvolvimento e os testes.
- Não publicar prontuários, credenciais, chaves, cópias de banco ou arquivos de configuração sensíveis no GitHub.
- Manter segredos fora do controle de versão e revisar o `.gitignore`.
- Submeter mudanças à revisão antes de integrá-las à branch principal.
- Documentar decisões técnicas, riscos conhecidos e resultados dos testes.

## Situação e próximos passos

O projeto encontra-se em **levantamento de informações e análise de viabilidade**. Após as visitas e entrevistas, a equipe deverá validar requisitos, priorizar o MVP, revisar a arquitetura e definir os critérios de aceitação.

## Aviso de confidencialidade

Este repositório deve conter somente código, documentação técnica e exemplos sem dados identificáveis. A existência de um protótipo não autoriza o tratamento de dados reais de assistidos. A eventual implantação dependerá de avaliação e aprovação institucional, técnica, jurídica e de segurança.

---

**Projeto CAIA — Proposta de Prontuário Digital Interno**  
*Documentação inicial sujeita a revisões.*
