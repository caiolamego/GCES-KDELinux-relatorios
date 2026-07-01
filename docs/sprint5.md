# Relatório de Contribuição – Sprint 5

**Disciplina:** Gestão de Configuração e Evolução de Software  
**Equipe:** KDE Linux  
**Comunidade/Projeto de Software Livre:** KDE Linux  
**Período da Sprint:** 22/06/2026 - 01/07/2026

## 1. Objetivos da Sprint
* [x] Finalizar e submeter os Merge Requests em desenvolvimento desde a Sprint 4.
* [x] Responder às rodadas de *code review* dos mantenedores e aplicar os ajustes solicitados.
* [x] Concluir o projeto individual alternativo para quem redirecionou o foco de contribuição.
* [x] Consolidar os aprendizados e encerrar a documentação da disciplina.

## 2. Entregas Coletivas

| Integrante | Contribuições na Sprint 5 |
|------------|---------------------------|
| **Caio Lamego** | Concluiu a **Issue #586**, configurando a licença `CC0-1.0` no `REUSE.toml`, validando o *linting* de licenças e a compilação, e abriu o Merge Request final, que aguarda revisão da comunidade. |
| **Diego Carlito** | Finalizou o script Python de validação de energia da **Issue #335**, integrou-o ao processo de migração via `mkosi.extra`, validou o comportamento em VM UEFI (Virt-Manager) e abriu o **MR #569**. |
| **Felipe Amorim** | Conduziu múltiplas rodadas de *code review* com o mantenedor Nate Graham no **MR #558** (ajustes de mensagens, permissões, sanitização de dados sensíveis e renomeação do script para `kde-linux-collect-logs`); teve o Merge Request aprovado e **integrado ao projeto**, sendo mencionado no post oficial *"This Month in KDE Linux"* de junho. |
| **João Pedro** | Submeteu os Merge Requests das duas frentes iniciadas na Sprint 4: a correção do conflito de dependências do kernel na geração da imagem UKI (**MR #565**) e a refatoração do KDE Ark removendo o arquivo `/etc/arkrc` (**MR #335**, repositório `utilities/ark`). |
| **Victório Lázaro** | Concluiu o projeto individual alternativo, implementando a camada de extração semântica dos dados via LLMs, o contrato semântico, o mecanismo de idempotência e a API REST de consulta; submeteu o *pull request* final da entrega. |

## 3. Maiores Avanços
* **Reconhecimento Público da Comunidade:** A contribuição de Felipe (ferramenta de coleta de logs) foi mencionada no post oficial *"This Month in KDE Linux"* de junho, marcando um reconhecimento direto do trabalho da equipe pela comunidade.
* **Fechamento de Múltiplos Ciclos de Contribuição:** Submissão e/ou aprovação de vários Merge Requests que encerram o trabalho iniciado ao longo da disciplina (Issues #586, #335, UKI, KDE Ark e #547).
* **Entrega Completa de Pipeline Alternativo:** Conclusão bem-sucedida de um pipeline de dados ponta a ponta (coleta, extração semântica via LLM e disponibilização via API) como entrega do projeto individual.
* **Maturidade no Ciclo de Revisão Assíncrona:** Absorção de múltiplas rodadas de feedback técnico de mantenedores seniores, aplicando correções de nomenclatura, permissões e segurança sem comprometer o prazo final.

## 4. Maiores Dificuldades
* **Rodadas Extensas de Code Review:** Ajustes finos solicitados em múltiplas iterações (sanitização de dados sensíveis, permissões, convenções de nomenclatura) exigiram builds e testes locais repetidos sob pressão de prazo.
* **Ausência de Retorno em MRs Pendentes:** Merge Requests já aprovados pelo pipeline de CI (ex.: MR !101 do Caio) permaneceram sem resposta dos mantenedores até o encerramento da sprint.
* **Confiabilidade de Extração via LLM:** No projeto individual alternativo, foi necessário desenvolver contratos semânticos e mecanismos de validação para reduzir alucinações e inconsistências na extração de dados não estruturados.
* **Fechamento Simultâneo de Frentes Técnicas:** A necessidade de concluir e documentar diversas contribuições em paralelo, no encerramento da disciplina, exigiu priorização cuidadosa do tempo da equipe.

## 5. Lições Aprendidas
* **Iteração Rápida sobre Feedback:** Responder e aplicar rapidamente os apontamentos dos mantenedores é determinante para viabilizar a integração de uma contribuição ao repositório oficial.
* **Testes Locais como Pré-requisito de Revisão:** Validar localmente cada ajuste solicitado antes de uma nova submissão evita rodadas adicionais de revisão e acelera a aprovação.
* **Contratos Semânticos em Pipelines com LLM:** Definir e validar rigorosamente o formato esperado das respostas de modelos de linguagem é essencial para garantir consistência e rastreabilidade em pipelines de extração de dados.
* **Ciclo Completo de Contribuição Open Source:** Vivenciar da prospecção de uma issue até a integração (ou submissão final) do código consolidou, na prática, os conceitos de Gestão de Configuração e Evolução de Software trabalhados ao longo da disciplina.

## 6. Planejamento para o Encerramento da Disciplina
* [ ] Acompanhar a aprovação final dos Merge Requests ainda em revisão (Issue #586, MR #569, MR #565).
* [ ] Consolidar e revisar a formatação de todos os diários de bordo individuais.
* [ ] Preparar a apresentação final consolidando os aprendizados da equipe ao longo da disciplina.
