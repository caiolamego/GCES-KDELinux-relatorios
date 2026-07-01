# Diário de Bordo – Diego Carlito Rodrigues de Souza

**Disciplina:** Gerência de Configuração e Evolução de Software
**Equipe**: KDE Linux
**Comunidade/Projeto de Software Livre:** KDE Linux

---

## Sprint 0 – 08/04/2026 – 22/04/2026

### Resumo da Sprint

Nesta sprint inicial, o foco foi estruturar um ambiente de desenvolvimento robusto e isolado, além de entender as diretrizes de contribuição da comunidade KDE. Configurei uma máquina virtual (VM) no Virt-Manager, implementei um sistema de arquivos compartilhado (VirtioFS) para integrar o código do *host* com a VM e ajustei o Docker nativo para BTRFS. Após superar gargalos críticos de espaço em disco e permissões de atributos no VirtioFS, finalizei com sucesso a compilação da imagem `.raw` do sistema e validei o resultado através de um teste de boot em uma VM secundária. Também realizei o mapeamento de *issues* introdutórias (*Newcomer*) para iniciar os trabalhos de código.

### Atividades Realizadas

| Data  | Atividade                                                                 | Tipo (Código/Doc/Discussão/Outro) | Link/Referência                                                                         | Status    |
| ----- | ------------------------------------------------------------------------- | --------------------------------- | --------------------------------------------------------------------------------------- | --------- |
| 14/04 | Leitura dos guias de envolvimento e contribuição na comunidade KDE        | Estudo                            | [Get Involved](https://community.kde.org/Get_Involved)                                          | Concluído |
| 15/04 | Instalação do KDE Linux via VM (Virt-Manager)                             | Estudo                            | [Guia para instalar o KDE Linux em uma VM](https://kde.org/linux/docs/install-vm/), [KDE Linux rodando na VM](./assets/kde_linux_vm_running.png) | Concluído |
| 16/04 | Avaliação da primeira Issue para trabalhar (Filtro *Newcomer*)            | Estudo                            | [Issues para novos contribuidores](https://invent.kde.org/kde-linux/kde-linux/-/work_items?label_name[]=Newcomer)   | Concluído |
| 18/04 | Criação do fork                                                           | Código                            | [Fork do KDE Linux](https://invent.kde.org/diegocarlito/kde-linux)                      | Concluído |
| 19/04 | Instalação e configuração da VM de Build (Virt-Manager, UEFI, 4GB RAM)    | Infra                             | [Guia de instalação pelo Virt-Manager](https://kde.org/linux/docs/install-vm/#virtual-machine-manager-virt-manager) | Concluído |
| 20/04 | Configuração de sistema de arquivos compartilhado (VirtioFS) entre Host e VM | Infra                          | [Arch Wiki - Libvirt: virtiofs](https://wiki.archlinux.org/title/Libvirt#virtiofs), [Doc oficial libvirt - virtiofs](https://libvirt.org/kbase/virtiofs.html) | Concluído |
| 21/04 | Ajuste do Docker (BTRFS), expansão de disco e compilação da imagem        | Código                            | [Guia para ajuste do build](https://kde.org/linux/docs/kde-linux-dev/), [Sucesso do build da imagem do KDE Linux](./assets/build_message.png) | Concluído |

### Maiores Avanços

* **Ciclo de Build Completo:** Sucesso na geração da imagem `.raw` customizada, validada através de boot funcional no QEMU/KVM.
* **Infraestrutura Escalável:** Implementação de disco virtual secundário (40GB) dedicado ao Docker e uso de *Bind Mounts* para contornar restrições de permissão e espaço.
* **Isolamento de Ambiente:** Estruturação de um ambiente de compilação seguro que preserva a integridade da máquina hospedeira enquanto permite o uso de ferramentas locais via VirtioFS.

### Maiores Dificuldades

* **Gargalos de Armazenamento:** Interrupção do build pelos erros `Partition /buildroot too full`, exigindo o redimensionamento estratégico do ambiente virtual.
* **Limitações do VirtioFS:** Erros de suporte a atributos (`Operation not supported`) ao tentar gerar a imagem diretamente na pasta compartilhada, resolvidos movendo o workspace para o disco nativo da VM.
* **Permissões de Diretórios:** Conflitos de acesso em pastas protegidas pelo Docker, solucionados através de mapeamentos de montagem específica (*mount --bind*).

### Aprendizados

* Domínio prático de manipulação de discos virtuais e configurações de BIOS/UEFI em ambientes virtualizados.
* Como isolar um ambiente de compilação complexo sem comprometer o sistema operacional hospedeiro.
* A importância de ler detalhadamente os *logs* de erro no terminal para diagnosticar gargalos de infraestrutura.

### Plano Pessoal para a Próxima Sprint

* [x] Solicitar o *assign* em uma das *issues* de nível *Newcomer* mapeadas.
* [x] Submeter o primeiro Merge Request (MR) seguindo os padrões de contribuição da comunidade.

---

## Sprint 1 – 22/04/2026 – 11/05/2026

### Resumo da Sprint

O foco desta sprint foi a contribuição direta para o projeto **KDE Linux Website**, visando sanar a falta de documentação sobre builds customizados. O trabalho compreendeu desde a negociação da *issue* com os mantenedores até a submissão formal do Merge Request. Implementei melhorias no guia de desenvolvimento, detalhando a injeção de pacotes via `mkosi` e o teste rápido de imagens `.raw` no Virt-Manager.

### Atividades Realizadas

| Data  | Atividade                                                                 | Tipo (Código/Doc/Discussão/Outro) | Link/Referência                                                                         | Status    |
| ----- | ------------------------------------------------------------------------- | --------------------------------- | --------------------------------------------------------------------------------------- | --------- |
| 03/05 | Escolha da Issue e solicitação de *assign*                                | Discussão                         | [Issue #531](https://invent.kde.org/kde-linux/kde-linux/-/work_items/531), [Solicitação de *assign*](https://invent.kde.org/kde-linux/kde-linux/-/work_items/531#note_1486369) | Concluído |
| 10/05 | Criação do Fork do KDE Linux Website                                      | Código                            | [Fork do KDE Linux Website](https://invent.kde.org/diegocarlito/linux-kde-org)          | Concluído |
| 10/05 | Elaboração da documentação                                                | Doc                               | [Arquivo modificado](https://invent.kde.org/diegocarlito/linux-kde-org/-/blob/docs/issue-531-mkosi-vm/content/docs/kde-linux-dev.md?ref_type=heads), [Commit](https://invent.kde.org/diegocarlito/linux-kde-org/-/commit/2689a11432752281199e564c47317b8809a274a2) | Concluído |
| 10/05 | Abertura do Merge Request (MR)                                            | Código                            | [MR](https://invent.kde.org/websites/linux-kde-org/-/merge_requests/4)                  | Concluído |
| 10/05 | Pedido de revisão do MR                                                   | Discussão                         | [Solicitação de revisão do MR](https://invent.kde.org/kde-linux/kde-linux/-/work_items/531#note_1492764) | Concluído |

### Maiores Avanços

* **Qualidade da Documentação:** Adição de um fluxo de trabalho otimizado para desenvolvedores, reduzindo o tempo de teste de imagens customizadas através do uso de discos existentes no Virt-Manager.
* **Padronização Profissional:** Uso de Conventional Commits e assinatura de autoria em conformidade com as políticas de auditoria da comunidade KDE.

### Maiores Dificuldades

* **Sintaxe Markdown/Hugo:** Ajuste da formatação de blocos de código e links relativos para garantir que o motor do site (Hugo) renderizasse o guia corretamente conforme o padrão visual da documentação oficial.

### Aprendizados

* Entendimento do fluxo de trabalho *upstream/origin* em projetos de larga escala e a importância de manter a branch de contribuição isolada.
* Comunicação técnica ao interagir diretamente com mantenedores de projetos de software livre.

### Plano Pessoal para a Próxima Sprint

* [x] Monitorar o processo de *Code Review* e aplicar eventuais revisões solicitadas pelos mantenedores.
* [x] Iniciar o mapeamento de *issues* de código (C++/Bash) para a próxima etapa de contribuição.

---

## Sprint 2 – 11/05/2026 – 25/05/2026

### Resumo da Sprint

O foco desta sprint foi a transição para contribuições de código e infraestrutura. Dediquei a primeira metade da sprint ao estudo do fluxo de CI/CD e à análise de Merge Requests fechados para entender a arquitetura do projeto. Em seguida, realizei a triagem de *issues*, filtrando problemas de *upstream* fora de escopo. Selecionei a **Issue #579** (automação de notificações de falha em *nightly builds* via CI/CD) e iniciei a discussão arquitetural sobre integração de webhooks e logs com os mantenedores.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| --- | --- | --- | --- | --- |
| 13/05 | Estudo do fluxo de *build* e infraestrutura de CI/CD do repositório | Estudo | [Arquivo `.gitlab-ci.yml` do projeto](https://invent.kde.org/diegocarlito/kde-linux/-/blob/master/.gitlab-ci.yml?ref_type=heads) | Concluído |
| 16/05 | Acompanhamento, aprovação e *merge* da contribuição da Sprint 1 | Discussão/Revisão | [Aprovação do MR #4](https://invent.kde.org/websites/linux-kde-org/-/merge_requests/4#note_1497212) | Concluído |
| 17/05 | Análise de MRs recentes para mapeamento de dependências e padrões de código | Estudo | [KDE Linux MRs](https://invent.kde.org/kde-linux/kde-linux/-/merge_requests/?sort=created_date&state=merged&first_page_size=100) | Concluído |
| 21/05 | Triagem e filtragem avançada de issues aplicáveis para a disciplina | Pesquisa | [Board de Issues](https://invent.kde.org/kde-linux/kde-linux/-/work_items?sort=created_date&state=opened&label_name%5B%5D=Enhancement&not%5Blabel_name%5D%5B%5D=Upstream%20issue&first_page_size=100) | Concluído |
| 24/05 | Escolha da Issue #579 e validação de requisitos de notificação | Discussão | [Issue #579](https://invent.kde.org/kde-linux/kde-linux/-/work_items/579), [Solicitação de *assign* e dúvidas](https://invent.kde.org/kde-linux/kde-linux/-/work_items/579#note_1504007) | Concluído |

### Maiores Avanços

* **Mapeamento Arquitetural:** Compreensão clara das diferenças entre bugs do ambiente KDE Linux, base Arch Linux e pacotes terceiros (*upstream*), otimizando a escolha de tarefas viáveis.
* **Modelagem de Solução:** Definição prévia da arquitetura da Issue #579, estruturando a necessidade de extração em bash (`tail`) e disparo de *payloads* via API.

### Maiores Dificuldades

* **Garimpo de Issues:** Dificuldade inicial para encontrar demandas de código factíveis em curto prazo que não exigissem alterações em dependências externas (*upstream repos*).
* **Escopo de Integração:** Ausência de documentação sobre a infraestrutura de comunicação interna do KDE (qual sala Matrix usar e quais variáveis de CI estão expostas para webhooks), exigindo o acionamento direto do mantenedor.

### Aprendizados

* Compreensão avançada das variáveis de ambiente e estágios do GitLab CI/CD.
* Otimização de tempo por meio da identificação e rejeição rápida de tarefas fora do escopo técnico possível para a duração da sprint.

### Plano Pessoal para a Próxima Sprint

* [x] Desenvolver o script em Shell/Bash para capturar as últimas linhas de erro do *log* do CI.
* [x] Configurar os gatilhos no arquivo `.gitlab-ci.yml` e o *payload* de envio para a API do Matrix.
* [x] Submeter o Merge Request final com a funcionalidade implementada.

---

## Sprint 3 – 25/05/2026 – 08/06/2026

### Resumo da Sprint

Esta sprint foi marcada pela execução prática e entrega de demandas críticas em múltiplas frentes. No escopo do KDE, aprofundei as interações com a comunidade adotando uma estratégia de colaboração e apoio mútuo com outros desenvolvedores e estudantes, como o [Caio Lamego](https://github.com/caiolamego), engajando nas *issues* dele para fortalecer nossa presença e inserção no projeto. 

O foco principal foi escrever e submeter o Merge Request da Issue #579 (script de notificação de falhas). Para resolver esse problema, desenvolvi um script em Bash acoplado ao CI/CD que captura automaticamente as últimas linhas dos logs de erro em caso de falha nas *nightly builds*. O meu MR acrescenta essa inteligência ao repositório configurando um gatilho que extrai o erro, formata o *payload* e o dispara via webhook diretamente para a sala Matrix dos desenvolvedores, acelerando significativamente a triagem e correção de problemas na infraestrutura. O código passou por duas rodadas de *code review* detalhado com os mantenedores. 

Paralelamente, dediquei forte esforço à finalização da infraestrutura do Trabalho Final de GCES, configurando pipelines e integração com SonarCloud, além de concluir e submeter o Projeto 4 (nota extra) para a disciplina de Tópicos Especiais em Engenharia de Software.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| --- | --- | --- | --- | --- |
| 05/06 | Apoio e discussão técnica na Issue #21 do KDE | Discussão | [Comentário Issue #21](https://invent.kde.org/kde-linux/kde-linux-packages/-/work_items/21#note_1514708) | Concluído |
| 05/06 | Início do desenvolvimento do Projeto 4 (Nota Extra) | Código | [Instruções do projeto](https://github.com/unb-Sistemas-de-Machine-learning/Projetos-Individuais-2026-1/blob/main/projeto-individual-4/README.md) | Concluído |
| 06/06 | Submissão do Merge Request com a automação de logs | Código | [MR #542](https://invent.kde.org/kde-linux/kde-linux/-/merge_requests/542) | Concluído |
| 06/06 | Análise de feedbacks | Revisão | [Feedback 1](https://invent.kde.org/kde-linux/kde-linux/-/merge_requests/542#note_1515147), <br> [Feedback 2](https://invent.kde.org/kde-linux/kde-linux/-/merge_requests/542#note_1515184) | Concluído |
| 06/06 | Início da configuração de infraestrutura do Trabalho Final de GCES (Pipeline CI/CD) | Código/Infra | [Instruções do Trabalho Final de GCES](https://gitlab.com/unb-esw/gces/gces2026-1/projetoindividual) | Concluído |
| 07/06 | Continuação do desenvolvimento de código do Projeto 4 | Código | [Branch do Projeto](https://github.com/DiegoCarlito/Projetos-Individuais-2026-1/tree/projeto-4-diego-souza/diego-carlito-rodrigues-de-souza/projeto-4) | Concluído |
| 08/06 | Conclusão do Trabalho Final de GCES | Infra | [SonarCloud](https://sonarcloud.io/project/overview?id=trabalho-final-gces-diego-souza), <br>  [Pipeline CI/CD do Trabalho Final de GCES](assets/projeto_individual_pipeline.png) | Concluído |
| 08/06 | Finalização do código do Projeto 4 | Código | [Branch do Projeto](https://github.com/DiegoCarlito/Projetos-Individuais-2026-1/tree/projeto-4-diego-souza/diego-carlito-rodrigues-de-souza/projeto-4) | Concluído |
| 08/06 | Submissão do Pull Request do Projeto 4 | Código | [PR #62](https://github.com/unb-Sistemas-de-Machine-learning/Projetos-Individuais-2026-1/pull/62) | Concluído |

### Maiores Avanços

* **Entrega de Código (*Upstream*):** Tradução do planejamento arquitetural da Issue #579 em código real, culminando na abertura do MR #542 no repositório do KDE Linux, estabelecendo a primeira grande entrega técnica na organização.
* **Maturidade em Infraestrutura:** Conclusão bem-sucedida do pipeline de CI/CD para o trabalho final, garantindo a exibição do *badge* do pipeline e consolidando a validação de qualidade de código através do SonarCloud.
* **Gestão de Múltiplas Entregas:** Capacidade de orquestrar e entregar simultaneamente contribuições Open Source, projetos complexos de infraestrutura e demandas analíticas.

### Maiores Dificuldades

* **Ciclo de Revisão Assíncrono:** Interpretar tecnicamente os apontamentos e restrições de arquitetura deixados pelo mantenedor no MR #542, entendendo o alto rigor de aceitação de código do ecossistema KDE.
* **Mudança Constante de Contexto:** Transitar rapidamente entre o desenvolvimento em Bash para automação de CI, o ambiente de orquestração e análise de qualidade e a stack voltada para Machine Learning no mesmo final de semana.

### Aprendizados

* Vivência prática na dinâmica de *code review* de projetos Open Source de grande porte, compreendendo como absorver críticas estruturais de mantenedores seniores e preparar iterações de código.
* Consolidação definitiva dos conceitos de integração contínua (CI) e inspeção contínua de código, fechando o ciclo de evolução do projeto de Gerência de Configuração.

### Plano Pessoal para a Próxima Sprint

* [x] Monitorar o processo de *Code Review* e aplicar eventuais revisões solicitadas pelos mantenedores.

---

## Sprint 4 – 08/06/2026 – 01/07/2026

### Resumo da Sprint

Esta sprint foi caracterizada pelo aprofundamento em integrações a nível de sistema operacional (OS). Inicialmente, dediquei esforços para o acompanhamento e aplicação das correções sugeridas no *code review* do [MR #542](https://invent.kde.org/kde-linux/kde-linux/-/merge_requests/542#note_1526031).

O foco central desta iteração, no entanto, foi o desenvolvimento de uma nova funcionalidade crítica de segurança focada em hardware: a [Issue #335](https://invent.kde.org/kde-linux/kde-linux/-/work_items/335). O objetivo era criar um mecanismo que impedisse o sistema de iniciar tarefas pesadas (como o processo de migração do sistema) caso a máquina estivesse rodando exclusivamente na bateria. Para solucionar isso, desenvolvi um script em Python focado na leitura da classe `power_supply` do Linux.

O script foi injetado diretamente na árvore do sistema operacional (*rootfs*) através da estrutura `mkosi.extra/`. A funcionalidade atua como um validador prévio: se o carregador estiver desconectado, o processo de migração é bloqueado, mitigando severamente os riscos de corrupção de dados por desligamento súbito. Para garantir a eficácia do código, realizei compilações locais gerando imagens customizadas do OS e validei o comportamento dinamicamente (simulando a presença e ausência de tomada) através de uma máquina virtual em modo UEFI no Virt-Manager.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| --- | --- | --- | --- | --- |
| 10/06 | *Feedbacks* para refinamento de código (*Code Review*) no MR de notificações Matrix | Revisão/Código | [MR #542](https://invent.kde.org/kde-linux/kde-linux/-/merge_requests/542#note_1526031) | Concluído |
| 14/06 | Estudo de viabilidade técnica e arquitetura para a Issue #335 (Validação de AC Power) | Doc/Discussão | [Issue #335](https://invent.kde.org/kde-linux/kde-linux/-/work_items/335), [Comentário da Issue #335](https://invent.kde.org/kde-linux/kde-linux/-/work_items/335#note_1535224) | Concluído |
| 30/06 | Desenvolvimento do script Python para leitura de *status* da bateria via OS | Código | [Branch 335-ac-power-check](https://invent.kde.org/diegocarlito/kde-linux/-/tree/335-ac-power-check?ref_type=heads) | Concluído |
| 30/06 | Integração do validador de energia ao processo de migração usando `mkosi.extra` | Código/Infra | [Commit](https://invent.kde.org/diegocarlito/kde-linux/-/commit/99d008ef8e13e6eac3f7dffcf39c2d22bc0dc342) | Concluído |
| 01/07 | Abertura do Merge Request com a funcionalidade de proteção de bateria | Código | [MR da Issue #335](https://invent.kde.org/kde-linux/kde-linux/-/merge_requests/569) | Concluído |

### Maiores Avanços

* **Desenvolvimento a Nível de SO:** Capacidade de escrever código que interage diretamente com o hardware virtual/físico (leitura de *power supply*), saindo da camada de automação web e indo para a base do sistema operacional.
* **Maturidade no Fluxo de Contribuição:** Tratamento eficiente do ciclo de *code review* da Sprint 3, aplicando as considerações dos mantenedores e garantindo que o PR caminhe para o *merge* final sem atritos.
* **Validação em Ambiente Isolado:** Geração e execução bem-sucedida de uma imagem *custom* completa do KDE Linux com o `mkosi` para provar o conceito de forma tátil em uma VM.

### Maiores Dificuldades

* **Lógica de Fallback de Hardware:** Garantir que o script de validação de bateria seja robusto o suficiente para não falhar ou bloquear o sistema indevidamente em ambientes que nativamente não possuem bateria (como *desktops* tradicionais ou certas configurações de *hypervisors*).
* **Injeção Correta de Dependências:** Compreender a hierarquia do `mkosi` para garantir que o script Python fosse parar no caminho correto dentro do *rootfs* do sistema operacional final para ser executado como esperado.

### Aprendizados

* Compreensão aprofundada de como o Kernel Linux expõe dados de hardware através de diretórios virtuais (como o comportamento do ACPI) e como acessá-los programaticamente via Python.
* Entendimento prático de como sistemas operacionais modernos imutáveis (ou baseados em imagens geradas) lidam com scripts customizados através da técnica de sobreposição de arquivos durante o *build*.