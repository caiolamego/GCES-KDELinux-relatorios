# Relatório de Contribuição – Sprint 2

**Disciplina:** Gestão de Configuração e Evolução de Software  
**Equipe:** KDE Linux  
**Comunidade/Projeto de Software Livre:** KDE Linux  
**Período da Sprint:** 11/05/2026 - 25/05/2026

## 1. Objetivos da Sprint
* [x] Avançar das tarefas de documentação para contribuições de código e infraestrutura.
* [x] Finalizar as contribuições iniciadas na Sprint 1 e submeter novos Merge Requests.
* [x] Estudar o fluxo de CI/CD do projeto (`.gitlab-ci.yml`, `mkosi`) e a arquitetura de build.
* [x] Manter comunicação ativa com os mantenedores antes de codificar, respeitando o Código de Conduta do KDE.

## 2. Entregas Coletivas

| Integrante | Contribuições na Sprint 2 |
|------------|---------------------------|
| **Caio Lamego** | Assumiu a Issue #586 (banner `/etc/motd` sobre o Kapsule); após mentoria de Hadi Chokr (`mkosi.extra`) e intervenção de Nate Graham, a tarefa foi bloqueada por depender do roadmap (Issue #584). Pivotou para as Issues #578 e #21 (CI/CD), vivenciando a concorrência por tarefas `Newcomer`. |
| **Diego Carlito** | Estudou o fluxo de CI/CD e analisou MRs fechados; realizou triagem avançada de issues (filtrando *upstream*); selecionou a **Issue #579** (notificação de falha em *nightly builds*) e iniciou a discussão arquitetural com os mantenedores. Teve o **MR #4** (Sprint 1) aprovado e integrado. |
| **Felipe Amorim** | Realizou o empacotamento Flatpak do thumbnailer `stl2thumbnail` (Issue #219); criou repositório público no GitHub com o manifesto, gerou a *release* `v0.1.0` e submeteu os links na issue para revisão dos mantenedores. |
| **Victório Lázaro** | Trabalhou na **Issue #581** (CI/CD); submeteu o **MR #528** adicionando um job no GitLab que manipula *secrets* (chaves GPG) via `secure_files` para deleção controlada de builds. |
| **João Pedro** | Recebeu atribuição da **Issue #82**; corrigiu o bug no script `live-setup` (passou a usar `/dev/gpt-auto-root` em vez de `by-label`), buildou a imagem e abriu o **Merge Request** oficial, relatando uma falha *upstream* na pipeline. |

## 3. Maiores Avanços
* **Transição para Código e Infraestrutura:** A equipe migrou da documentação para contribuições reais de código, atuando diretamente em pipelines de CI/CD, scripts Shell e empacotamento Flatpak.
* **Governança e Dependências de Roadmap:** Vivência prática do bloqueio de uma feature pelo roadmap (Issue #586 dependente da #584), reforçando o valor da comunicação prévia antes de submeter código.
* **Manipulação Segura de Segredos:** Criação de jobs de CI que tratam credenciais sensíveis (chaves GPG) via `secure_files`, sem expô-las em logs ou histórico.
* **Mentoria da Comunidade:** Respostas rápidas dos mantenedores (Hadi Chokr, Nate Graham) orientando a arquitetura e poupando horas de investigação.

## 4. Maiores Dificuldades
* **Concorrência por Issues `Newcomer`:** A escassez de tarefas acessíveis e a alta concorrência interna e externa inviabilizaram várias issues (#578, #21, #579) já assumidas.
* **Bloqueio de Tarefas no Meio da Execução:** Features paralisadas por dependências de roadmap forçaram replanejamento da sprint de última hora.
* **Complexidade do CI/CD:** Compreender a estrutura do `.gitlab-ci.yml` e as variáveis de ambiente do projeto exigiu grande esforço investigativo.
* **Gargalos de Ambiente de Build:** Falta de espaço em disco, configuração de Docker em BTRFS e instabilidades de rede atrasaram a compilação local.

## 5. Lições Aprendidas
* **O Valor da Comunicação Prévia:** Avisar no Matrix e nas issues antes de codificar evita retrabalho e rejeição de MRs que expõem funcionalidades incompletas.
* **Ecossistema `mkosi` e CI/CD:** Aprofundamento em como customizações são injetadas em sistemas imutáveis e como os pipelines de build são estruturados.
* **Manutenção de Código Legado:** A importância de preservar o comportamento existente ao estender funções (ex.: passar `nil` para novos parâmetros) e de validar entradas em múltiplos pontos.
* **Curadoria de Tarefas:** Identificar e rejeitar rapidamente tarefas *upstream* ou fora de escopo otimiza o tempo da sprint.

## 6. Planejamento para a Próxima Sprint
* [ ] Acompanhar os *Code Reviews* dos Merge Requests abertos (#528, #4) e aplicar as revisões solicitadas.
* [ ] Implementar e submeter o script de notificação de falhas no CI (Issues #579 e #21).
* [ ] Dar continuidade ao empacotamento do thumbnailer STL conforme o feedback dos mantenedores.
* [ ] Resolver conflitos e atender às RFCs solicitadas pela comunidade nos MRs em andamento.
