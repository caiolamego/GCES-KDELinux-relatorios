### Diário de Bordo – Caio Lamego

#### Sprint 0
##### Resumo da Sprint
Nesta sprint inicial, o foco principal foi estabelecer a comunicação com a comunidade KDE, compreender as políticas do projeto e superar a complexidade de configurar o ambiente local. Diferente de softwares tradicionais, o projeto escolhido (KDE Linux) é um sistema operacional imutável em desenvolvimento ativo ("cutting-edge immutable OS"). O esforço técnico principal concentrou-se na criação de uma Máquina Virtual no Linux hospedeiro e no mapeamento de melhorias (Issues) para as próximas etapas.

###### Atividades Realizadas
| Data | Atividade | Tipo | Status |
|---|---|---|---|
| 16/04/2026 | Abertura do repositório de documentação| Configuração | Concluído |
| 17/04/2026 | Leitura do Código de Conduta e políticas da comunidade | Estudo | Concluído |
| 17/04/2026 | Apresentação na comunidade (#new-contributors) no Matrix | Discussão | Concluído |
| 17/04/2026 | Busca no repositório (GitLab CI/CD) para baixar a imagem do SO | Estudo | Concluído |
| 18/04/2026 | Configuração de firmware e ambiente via `virt-manager` | Configuração | Concluído |
| 19/04/2026 | Mapeamento de tarefas (Filtro por Issues `Newcomer`) | Estudo | Concluído |

##### Maiores Avanços
* **Integração com a Comunidade:** Entendi que a comunidade KDE utiliza o Matrix para comunicação em tempo real e o ambiente Invent (GitLab) para o rastreamento do código e tarefas. Me apresentei formalmente na sala `#new-contributors:kde.org`.
![apresentação no Matrix](./assets/matrix.png)

* **Ambiente de Desenvolvimento de Pé:** Consegui configurar a máquina virtual no `virt-manager` utilizando os parâmetros exigidos (4 CPUs e 4096 MB de RAM). Importei o artefato de compilação da imagem e consegui instalar o KDE Linux no disco secundário formatado (`vdb - 20 GiB`). O sistema está rodando localmente de forma isolada!
![kdelinux](./assets/kdelinux.png)

##### Maiores Dificuldades
* **Mudança de Paradigma no Ambiente de Testes e Build:** Tive uma grande dificuldade inicial para compreender a arquitetura do ambiente local e como os meus testes de código seriam realizados na prática. Em projetos convencionais (como aplicações web abordadas em outros semestres), o padrão é clonar o código, instalar dependências e "subir" o ambiente compilando tudo no próprio terminal do hospedeiro (usando ferramentas como Docker, Node, etc.). No KDE Linux, por se tratar de um Sistema Operacional Imutável inteiro, o fluxo é radicalmente diferente. Demorei a entender que eu **não devo compilar o código localmente**. O ambiente de desenvolvimento em si é a Máquina Virtual rodando o arquivo `.raw`; as alterações que eu fizer no código do meu *fork* serão enviadas e construídas (*build*) pelos servidores do GitLab através de pipelines de CI/CD. A VM atua apenas como o laboratório final de testes, o que exigiu uma forte quebra de expectativa sobre o que significa "configurar o ambiente local" em projetos de sistemas operacionais.

##### Lições Aprendidas
* **Cultura de Contribuição:** Entendi a fundo os pilares do Código de Conduta do KDE, especialmente os de pragmatismo e colaboração mútua ("Be collaborative", "Be pragmatic"). Seguir as diretrizes oficiais e se comunicar ativamente é a chave.
* **Atenção Estrita à Documentação:** Seguir passo a passo a documentação oficial (quando existente) é crucial para evitar erros críticos de setup. Existem erros já previstos na documentação, e isso é importante para saber que tipo de problemas podem surgir e como resolvê-los, e entender que o build do ambiente não saiu do controle.
* **Curadoria de Tarefas:** Aprendi que ter a tag de bug não significa que a tarefa está pronta para desenvolvimento. É crucial evitar Issues marcadas como `Upstream issue` (ex: Issue #448 ou a #589 sobre Kernel Panic) pois estas dependem de alterações em repositórios de terceiros. Além disso conheci as tags `Newcomer` e `Good First Issue`, que são indicativos de tarefas mais acessíveis para novos contribuidores.

##### Mapeamento das Políticas de Contribuição e Qualidade
Diferente de repositórios comerciais no GitHub, o ecossistema do KDE possui uma estrutura descentralizada de ferramentas e políticas, gerida através de sua própria infraestrutura:

* **Gestão de Código e Revisão (KDE Invent):** O projeto não utiliza GitHub nem a nomenclatura de *Pull Requests (PRs)*. Todo o controle de versão, submissão de código e revisão *peer-to-peer* (desenvolvedor para desenvolvedor) ocorre no **KDE Invent**, uma instância do GitLab. As submissões de código são feitas através de **Merge Requests (MRs)**.
* **Separação de Issues e Bugs:** O rastreamento de problemas é categorizado. Tarefas de desenvolvimento, planejamento e *good-first-issues* (Newcomers) ficam no painel de *Work items* do GitLab. No entanto, relatos de falhas pelos usuários são gerenciados separadamente através do **KDE Bugzilla** (KDE Bugtracker).
* **Política de Nomenclatura e Pragmatismo:** Em vez de ditar regras estritas e burocráticas sobre prefixos de *branches* (como `feat/`, `bugfix/`), a política do KDE baseia-se no seu **Código de Conduta**, exigindo um desenvolvimento *pragmático* e *colaborativo*. A regra de ouro descrita na wiki oficial é a **transparência**: o contribuidor deve usar os canais de comunicação (Matrix ou comentários nas Issues do Invent) para discutir a implementação e avisar a comunidade antes de submeter um MR pesado.



##### Mapeamento de Issues
* Acessamos o painel de *Work Items* no Invent (GitLab) e utilizamos os filtros `Label is Newcomer` e `State is Open` para encontrar tarefas voltadas para novos desenvolvedores. ![issues](./assets/issues.png)
* Mapeamento das seguintes Issues com alto potencial para a nossa primeira contribuição:
  * **Issue #164:** Melhorar a descrição de atualização no aplicativo *Discover* (Atualmente exibe um texto muito genérico do KDE Linux).
  * **Issue #319:** Adicionar um *slideshow* de imagens no momento da instalação do sistema usando o Calamares.
  * **Issue #531:** Adicionar instruções na documentação sobre como usar o `mkosi` para criar imagens customizadas.

##### Plano Pessoal para a Próxima Sprint
* [ ] Escolher ativamente uma das Issues mapeadas acima e solicitar a atribuição (*assign*) no GitLab.
* [ ] Mapear a arquitetura e estudar o *codebase* específico da Issue escolhida no repositório.
* [x] Realizar alterações no meu repositório (*fork*) e rodar testes na Máquina Virtual.
* [x] Abrir o primeiro Pull Request / Merge Request.


#### Sprint 1 - 27/04/2026 - 04/05/2026

##### Resumo da Sprint
Nesta sprint, o foco absoluto foi realizar a primeira contribuição real para o repositório do projeto. No entanto, houve altíssima concorrência: as poucas issues ativas com a tag `Newcomer` já tinham sido escolhidas por outros membros da comunidade ou por colegas da nossa equipe (como a Issue #164, a #319, a #219 e a #531). Para não travar meu desenvolvimento, comparei a documentação oficial da Wiki e o `README.md` principal do repositório. Criei uma nova Issue apontando uma falta de informação sobre o onboarding e resolvi através de um *Merge Request*, respeitando as políticas da comunidade.

| Data | Atividade | Tipo (Código/Doc/Discussão) | Status |
|---|---|---|---|
| 03/05/2026 | Comunicação prévia com a comunidade no Matrix | Discussão | Concluído |
| 03/05/2026 | Criação de nova Issue no Invent sobre onboarding de VMs | Doc/Gestão | Concluído |
| 03/05/2026 | Inserção da seção "Test it in a Virtual Machine" no `README.md` | Código/Doc | Concluído |
| 03/05/2026 | Abertura do meu Primeiro Merge Request (MR) | Código | Concluído |
| 04/05/2026 | MR aceito e merge concluído | Código | Concluído |

##### Maiores Avanços
* **Etiqueta Open Source e Comunicação:** Antes de simplesmente abrir a Issue, apliquei os princípios de "Be collaborative" e "Be pragmatic" do Código de Conduta do KDE. Fui até o canal oficial no Matrix e avisei os mantenedores previamente sobre a minha intenção de alterar o `README.md`, respeitando o aviso do repositório que pede aos usuários para consultarem a comunidade antes de reportarem *issues*.
![aviso no Matrix](./assets/sprint1-matrix.png)
* **Senso Crítico e Auditoria (A identificação do gargalo):** Ao realizar uma revisão na Wiki oficial do KDE, notei que pudesse ser necessária uma Issue: *Quando um desenvolvedor entra no repositório de código do KDE Linux, a primeira coisa que ele vê é o arquivo `README.md`. Atualmente, ele não possui nenhum alerta sobre o UEFI e não guia o desenvolvedor de forma clara para ler a página da Wiki. O desenvolvedor acaba tentando montar a Máquina Virtual de forma intuitiva, usa o BIOS antigo por padrão, e o sistema quebra.*
![Issue Sprint1](./assets/issue-sp1.png)
* **Primeira Contribuição:** Contribuição para a comunidade solucionando essa falha apontada acima. Inseri a seção `Test it in a Virtual Machine` no `README.md` alertando sobre o UEFI e submeti meu primeiro *Merge Request*.
![MR Sprint1](./assets/mr-sp1.png)

* **MR aprovado:** O Merge Request foi aprovado pelos mantenedores do KDE e integrado ao código principal, dessa forma atualizando a documentação do projeto.
![MR Sprint1](./assets/merge.png)

##### Maiores Dificuldades
* **Concorrência Agressiva por Issues:** A maior dificuldade da sprint foi a alta de tarefas, por serem poucas de newcomers e por estarem sendo disputadas por diversos membros da comunidade. A maioria das Issues mais acessíveis já estavam atribuídas, o que me forçou a criar minha própria Issue.

##### Aprendizados
* **A Importância da Transparência:** Aprendi que, no Open Source, o processo de comunicação (avisar no Matrix, justificar a Issue) é tão importante quanto o código em si. Respeitar as regras de governança do repositório abre portas mais facilmente.
* **A Importância do README:** Compreendi que ter uma boa documentação na Wiki não basta se o arquivo raiz do repositório não conduzir ativamente os novos contribuidores até ela e não fizer alertas de infraestrutura para os ambientes locais de *build* e teste.

##### Plano Pessoal para a Próxima Sprint
* [x] Acompanhar a revisão (*Code Review*) do meu Merge Request pelos mantenedores do KDE.
* [ ] Começar a contribuir em novas Issues, além de Newcomer, para ganhar mais experiência com o código.
* [ ] Estudar o *codebase* com maior antecedência para a Sprint 2, buscando atuar ativamente em *issues* de código.


#### Sprint 2

##### Resumo da Sprint
Nesta sprint, o objetivo foi aprofundar a contribuição no ecossistema do KDE Linux, focando em tarefas de configuração, integração e infraestrutura. O processo foi marcado por intensa comunicação com os mantenedores oficiais, exigindo adaptações rápidas (pivôs) no plano de ação original devido à altíssima concorrência. Tentei assumir múltiplas tarefas (Issues #586, #578 e #21), vivenciando na prática os desafios de governança, concorrência interna da equipe, dependências de roadmap e alocação de tarefas distribuídas em um projeto Open Source em fase Beta.


##### Planejamento Inicial e Escolha da Issue #586
A primeira tarefa selecionada para a Sprint 2 foi a **Issue #586: "Add a /etc/motd on the base OS explaining that most stuff is in Kapsule"**. A tarefa consistia em adicionar um banner de terminal (Message of the Day) na imagem base do sistema operacional, instruindo novos usuários sobre a natureza imutável do SO e direcionando-os ao uso do contêiner Kapsule. 

Essa issue foi escolhida por ter um alto impacto na Experiência do Desenvolvedor (DevEx) e estar alinhada com o escopo de configuração de pacotes e infraestrutura.


###### Comunicação e Etiqueta Open Source (Matrix e GitLab)
Seguindo o Código de Conduta do KDE, antes de submeter qualquer código, iniciei o processo de comunicação.
Fui ao canal oficial do projeto no Matrix (`#kde-linux:kde.org`) para avisar a comunidade sobre a minha intenção de assumir a tarefa e pedi direcionamento técnico sobre onde os arquivos do `/etc/` eram populados durante o *build* (mkosi).

![Matrix Sp2](./assets/sprint2/matrix.png)

Em seguida, registrei formalmente o meu interesse comentando na própria Issue no GitLab.

---

###### Colaboração, Mentoria e Gerenciamento de Dependências
A resposta da comunidade foi extremamente rápida, resultando em duas interações cruciais com os mantenedores principais do KDE Linux:

**A. Mentoria Técnica:**
O desenvolvedor Hadi Chokr respondeu ao meu comentário quase imediatamente, indicando o caminho exato para a injeção de arquivos: *"They are defined in the mkosi.extra folder"*. Isso demonstrou a alta colaboração da comunidade.

![Issue Folder](./assets/sprint2/folder.png)

**B. Bloqueio por Dependência de Roadmap:**
Logo após eu iniciar a estruturação do código, o mantenedor líder (Nate Graham) interveio avisando que a Issue #586 era prematura. Ele explicou que a tarefa dependia da conclusão prévia da **Issue #584 (Full Kapsule integration)** [1] e que fazer o *Merge Request* agora direcionaria os usuários para um "canteiro de obras".

![Issue Cancelada](./assets/sprint2/issue-canceled.png)

**Ação Tomada:** Entendendo os princípios de evolução de software e dependências de *features*, concordei com o mantenedor, cancelei a alteração no código para evitar conflitos na base principal e me retirei da tarefa.

![Resposta](./assets/sprint2/answer.png)

##### Tentativas de novas issues e alta concorrência (Issues #578 e #21)
Com a paralisação da #586, iniciei uma busca por novas opções de contribuição, focando em CI/CD:
1. **Issue #578 ("On-demand CI job to delete the latest build"):** Escolhi esta tarefa por envolver a manipulação de jobs sob demanda no pipeline. Contudo, rapidamente descobri que ela já havia sido assumida por outro mantenedor, o que inviabilizou minha atuação.
2. **Issue #21 ("Loud notification on nightly build failure" - kde-linux-packages):** Encontrei esta issue com a tag `Newcomer`. Ao demonstrar interesse, o mantenedor Nate Graham me respondeu explicando que essa tarefa era a "outra metade" da Issue #579 (do repositório principal). Mais uma vez não foi possível realizar uma issue que teoricamente estava livre para desenvolver, mesmo com a tag de Newcomer.

![Issue Negada](./assets/sprint2/issue_negada.png)

---
##### Maiores Avanços
* **Gerenciamento de Dependências e Governança:** Consegui vivenciar o fluxo real de uma feature sendo bloqueada pelo roadmap do projeto. A Issue #586 exigia adicionar um aviso no `/etc/motd` sobre o Kapsule, mas o mantenedor Nate Graham interveio para informar que a integração do Kapsule (Issue #584) não estava pronta. 
* **Mentoria e Código de Conduta:** A comunicação no Matrix antes de codificar funcionou perfeitamente. O desenvolvedor Hadi Chokr me respondeu quase imediatamente no GitLab, orientando que a injeção de arquivos ocorria na pasta `mkosi.extra`, poupando horas de busca na arquitetura do sistema.

##### Maiores Dificuldades
* **Bloqueio de Tarefa no Meio da Execução:** A paralisação da Issue #586 logo após o início do trabalho me forçou a reorganizar a sprint de última hora e a justificar de forma profissional minha saída da tarefa.
* **Concorrência por Issues Newcomer:** A tentativa de pivotar para a Issue #579 (notificação de erro no pipeline) falhou pois a alta concorrência na comunidade e a escassez de issues com a label `Newcomer` fizeram com que ela já estivesse tomada.
* **Compreensão de Pipelines de CI:** Aprender a estrutura do `.gitlab-ci.yml` do projeto para injetar de forma segura um job `when: manual` sem quebrar o restante da integração contínua do repositório principal exigiu grande esforço investigativo.

##### Aprendizados
* **O Valor da Comunicação Prévia:** Salvei horas de trabalho. Se eu tivesse feito o Merge Request da #586 em silêncio, ele seria rejeitado por expor uma funcionalidade incompleta.
* **Ecossistema Mkosi:** Mesmo não finalizando a #586, ganhei um conhecimento técnico sobre a montagem de imagens de sistemas imutáveis usando `mkosi`, e como as customizações são injetadas no nível raiz através de arquivos de configuração, ao invés da compilação tradicional.