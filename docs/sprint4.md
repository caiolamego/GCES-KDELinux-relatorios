# Relatório de Contribuição – Sprint 4

**Disciplina:** Gestão de Configuração e Evolução de Software  
**Equipe:** KDE Linux  
**Comunidade/Projeto de Software Livre:** KDE Linux  
**Período da Sprint:** 08/06/2026 - 22/06/2026

## 1. Objetivos da Sprint
* [x] Retomar issues bloqueadas por dependências de roadmap e avançar contribuições de código a nível de sistema operacional (kernel, hardware).
* [x] Buscar novas issues técnicas, mesmo sem a tag `Newcomer`, negociando o escopo diretamente com os mantenedores diante da escassez de tarefas simples.
* [x] Validar as implementações em ambiente isolado (VM/UEFI) antes da submissão dos Merge Requests.
* [x] Avaliar a viabilidade de contribuição contínua no KDE Linux e redirecionar esforços para o projeto individual alternativo da disciplina quando necessário.

## 2. Entregas Coletivas

| Integrante | Contribuições na Sprint 4 |
|------------|---------------------------|
| **Caio Lamego** | Retomou a **Issue #586** (banner em `/etc/motd` explicando a integração com o Kapsule), bloqueada desde a Sprint 2 por dependência de roadmap; iniciou a injeção do arquivo via `mkosi.extra` e o mapeamento da licença no `REUSE.toml` para atender às políticas de licenciamento do projeto. |
| **Diego Carlito** | Assumiu a **Issue #335**, propondo um mecanismo para impedir a migração do sistema quando a máquina estiver rodando exclusivamente na bateria; estudou a leitura da classe `power_supply` do kernel Linux e iniciou o desenvolvimento do script Python de validação. |
| **Felipe Amorim** | Selecionou a **Issue #547** (ferramenta de coleta automática de informações e logs para abertura de bugs), aprovada pelo mantenedor Nate Graham mesmo sem a tag `Newcomer`; implementou a primeira versão e abriu o **MR #558**. |
| **João Pedro** | Trabalhou em duas frentes de arquitetura: a **Issue #636** (conflito de dependências do kernel na geração da imagem UKI) e uma issue de limpeza arquitetural do **KDE Ark** (poluição do diretório `/etc`); avançou a implementação e os testes locais em ambos os repositórios. |
| **Victório Lázaro** | Diante da baixa disponibilidade de issues no KDE Linux e da ausência de retorno em Merge Requests anteriores, redirecionou o foco para o projeto individual alternativo da disciplina (pipeline de dados não estruturados do setor habitacional), implementando a camada de coleta automatizada via *web scraping*. |

## 3. Maiores Avanços
* **Contribuições a Nível de Sistema Operacional:** A equipe avançou de scripts de conveniência e documentação para intervenções diretas na arquitetura do sistema — leitura de hardware (bateria), geração de imagens de boot (UKI) e injeção de arquivos estáticos via `mkosi.extra`.
* **Negociação de Escopo Fora de Issues `Newcomer`:** Felipe conseguiu autorização direta de um mantenedor para trabalhar em uma issue de maior complexidade, mesmo sem a tag destinada a novatos, evidenciando maturidade na comunicação com a comunidade.
* **Contribuição em Repositórios do Ecossistema KDE:** João Pedro expandiu a atuação da equipe para além do `kde-linux`, propondo uma refatoração C++/CMake diretamente no repositório da aplicação KDE Ark.
* **Aplicação de Mentoria Recebida em Sprints Anteriores:** Caio colocou em prática a orientação recebida do mantenedor Hadi Chokr na Sprint 2 sobre o uso do `mkosi.extra` para injeção de arquivos no sistema base.
* **Decisão Estratégica de Redirecionamento:** Victório identificou precocemente os obstáculos de contribuição no KDE Linux e realocou seus esforços para uma entrega alternativa com maior potencial de conclusão dentro do prazo da disciplina.

## 4. Maiores Dificuldades
* **Escassez Persistente de Issues:** A quantidade reduzida de tarefas `Newcomer` disponíveis e a alta concorrência (interna e externa) continuaram limitando as opções de contribuição direta.
* **Ausência de Feedback em MRs Anteriores:** Merge Requests já aprovados no pipeline de CI (ex.: MR !101 do Caio) seguiram sem resposta dos mantenedores, dificultando o planejamento de novas entregas.
* **Complexidade Técnica Elevada:** As issues remanescentes exigiram conhecimento aprofundado de áreas específicas — leitura de dados de hardware via kernel, políticas de licenciamento REUSE/SPDX e refatoração C++/Qt em um segundo repositório do ecossistema.
* **Robustez em Ambientes Heterogêneos:** Garantir que o script de validação de energia não falhasse em ambientes sem bateria (desktops, hypervisors) exigiu cuidado extra na lógica de *fallback*.
* **Pressão de Prazo:** A proximidade do encerramento da disciplina intensificou a necessidade de concluir entregas técnicas em paralelo.

## 5. Lições Aprendidas
* **Injeção de Arquivos Estáticos via `mkosi.extra`:** Sistemas base imutáveis permitem a inclusão de arquivos de configuração sem a necessidade de scripts complexos de pós-instalação.
* **Licenciamento como Parte do CI/CD:** No KDE Linux, a pipeline falha caso qualquer arquivo não possua uma licença declarada (`REUSE.toml`), reforçando a importância de tratar conformidade de licenciamento como parte do processo de build.
* **Contribuição Além do Repositório Principal:** É possível e válido contribuir com repositórios upstream relacionados (como o KDE Ark) quando uma dívida técnica impacta diretamente a experiência do sistema operacional.
* **Tratar a Causa Raiz:** Preferir soluções que corrijam o comportamento padrão via código a manter *workarounds* baseados em arquivos de configuração forçados no sistema.
* **Saber Quando Pivotar:** Diante de bloqueios recorrentes de disponibilidade e retorno em um projeto Open Source, redirecionar esforços para uma entrega alternativa viável é uma decisão estratégica válida.

## 6. Planejamento para a Próxima Sprint
* [ ] Finalizar e submeter os Merge Requests em desenvolvimento (Issues #586, #335, UKI e KDE Ark).
* [ ] Responder às rodadas de *code review* dos mantenedores e aplicar os ajustes solicitados.
* [ ] Concluir a implementação do projeto individual alternativo (extração semântica, contrato semântico e API).
* [ ] Consolidar os aprendizados finais e preparar o encerramento da documentação da disciplina.
