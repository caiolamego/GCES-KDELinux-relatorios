# Relatório de Contribuição – Sprint 3

**Disciplina:** Gestão de Configuração e Evolução de Software  
**Equipe:** KDE Linux  
**Comunidade/Projeto de Software Livre:** KDE Linux  
**Período da Sprint:** 25/05/2026 - 08/06/2026

## 1. Objetivos da Sprint
* [x] Submeter os Merge Requests finais das contribuições de código e CI/CD iniciadas na Sprint 2.
* [x] Atender aos *Code Reviews* dos mantenedores, resolvendo conflitos e aplicando as RFCs solicitadas.
* [x] Coordenar contribuições entre repositórios (`kde-linux` e `kde-linux-packages`) mantendo a mesma arquitetura.
* [x] Consolidar a presença da equipe no projeto através de colaboração e apoio mútuo entre os membros.

## 2. Entregas Coletivas

| Integrante | Contribuições na Sprint 3 |
|------------|---------------------------|
| **Caio Lamego** | Retomou a **Issue #21** (`kde-linux-packages`); criou o script `notify_matrix.sh` (notificação de falha de build via webhook do Matrix), ajustou o `.gitlab-ci.yml` e o `bootstrap.sh` (dependência `jq`), validou com `shellcheck` e webhook local, e abriu o **MR !101**. Trabalho coordenado com Diego. |
| **Diego Carlito** | Escreveu e submeteu o **MR #542** (Issue #579) com a automação de captura de logs e disparo via webhook nas *nightly builds*; passou por duas rodadas de *code review* com os mantenedores. Apoiou tecnicamente a Issue #21 do Caio. |
| **Felipe Amorim** | Deu continuidade à Issue #219; ajustou o manifesto do Flatpak (correção do nome do thumbnailer no post-install), publicou a *release* `v0.2.0` e recebeu confirmação de testes e validação dos contribuidores do projeto, com novos ajustes mapeados. |
| **Victório Lázaro** | Resolveu conflitos e submeteu RFCs e documentação solicitadas pelos mantenedores nos seus dois MRs anteriores (Issues #164 e #581 / **MR #528**), absorvendo o ciclo de revisão assíncrono da comunidade. |
| **João Pedro** | Concluiu o *code review* da **Issue #82** com o mantenedor Harald Sitter (correção do script `live-setup`); ajustou as proteções da *branch* do fork para viabilizar o *rebase* e teve o **Merge Request oficialmente aceito e integrado (*merged*)** ao repositório do KDE Linux. |

## 3. Maiores Avanços
* **Código Integrado ao KDE Linux:** O Merge Request da Issue #82 (correção do `live-setup`) foi oficialmente aprovado e mesclado à branch principal do projeto — a primeira contribuição da equipe efetivamente integrada ao sistema operacional.
* **Entregas de Código *Upstream*:** Múltiplos Merge Requests de CI/CD submetidos ao KDE (MR #542 e MR !101), traduzindo o planejamento arquitetural da Sprint 2 em código real.
* **Colaboração entre Repositórios:** Caio e Diego desenvolveram de forma coordenada a mesma solução nos repositórios `kde-linux` e `kde-linux-packages`, mantendo padronização e reaproveitando arquitetura já revisada.
* **Tratamento Seguro de Segredos:** A URL do webhook do Matrix não foi versionada no código, sendo fornecida por variável protegida do GitLab CI/CD (`MATRIX_WEBHOOK_URL`).
* **Maturidade no Ciclo de Revisão:** Validação das contribuições (testes locais, `shellcheck`, resolução de conflitos) e participação ativa em rodadas de *code review* com mantenedores seniores.

## 4. Maiores Dificuldades
* **Ciclo de Revisão Assíncrono:** Interpretar e aplicar os apontamentos arquiteturais dos mantenedores exigiu lidar com o alto rigor de aceitação de código do ecossistema KDE.
* **Comportamento de Pipes no Shell:** Compreender que o uso de `tee` poderia mascarar a falha do build sem `pipefail`, e preservar corretamente os códigos de erro.
* **Validação do Ambiente de CI:** A imagem da infraestrutura do KDE não pôde ser executada localmente via Docker, exigindo soluções alternativas para garantir dependências como o `jq`.
* **Escassez de Novas Issues:** A falta de tarefas `Newcomer` disponíveis dificultou iniciar novas contribuições além das já em andamento.

## 5. Lições Aprendidas
* **CI/CD Exige o Mesmo Rigor:** Alterações em pipelines precisam ser testadas e revisadas com o mesmo cuidado de funcionalidades tradicionais.
* **Reuso de Arquitetura Revisada:** Reaproveitar uma solução já validada pelos mantenedores reduz divergências e facilita o trabalho de revisão entre repositórios.
* **Importância do Feedback:** Receber e aplicar feedbacks da comunidade é fundamental para alinhar a contribuição às expectativas e aumentar suas chances de integração.
* **Mascaramento de Erros em Pipelines:** Pipes de comandos podem esconder códigos de erro; é essencial preservar a falha para que o CI a reporte corretamente.
* **Named Branches e Rebase:** Submeter código em *branches* descritivas (em vez da `master`) e compreender o fluxo de *rebase/merge* mantém o histórico limpo e facilita a integração pelos mantenedores.

## 6. Planejamento para a Próxima Sprint
* [ ] Acompanhar as pipelines e os processos de revisão dos Merge Requests (!101, #542, #528).
* [ ] Responder aos comentários dos mantenedores e aplicar eventuais ajustes solicitados.
* [ ] Acompanhar a configuração da variável `MATRIX_WEBHOOK_URL` no projeto oficial.
* [ ] Registrar o resultado final dos Merge Requests, incluindo aprovação ou integração ao repositório.
