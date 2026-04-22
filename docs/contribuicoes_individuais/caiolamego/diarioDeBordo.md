### Diário de Bordo – Caio Lamego
**Período da Sprint:** Sprint 0

#### Resumo da Sprint
Nesta sprint inicial, o foco principal foi estabelecer a comunicação com a comunidade KDE, compreender as políticas do projeto e superar a complexidade de configurar o ambiente local. Diferente de softwares tradicionais, o projeto escolhido (KDE Linux) é um sistema operacional imutável em desenvolvimento ativo ("cutting-edge immutable OS"). O esforço técnico principal concentrou-se na criação de uma Máquina Virtual no Linux hospedeiro e no mapeamento de melhorias (Issues) para as próximas etapas.

#### Atividades Realizadas
| Data | Atividade | Tipo | Status |
|---|---|---|---|
| 16/04/2026 | Abertura do repositório de documentação| Configuração | Concluído |
| 17/04/2026 | Leitura do Código de Conduta e políticas da comunidade | Estudo | Concluído |
| 17/04/2026 | Apresentação na comunidade (#new-contributors) no Matrix | Discussão | Concluído |
| 17/04/2026 | Busca no repositório (GitLab CI/CD) para baixar a imagem do SO | Estudo | Concluído |
| 18/04/2026 | Configuração de firmware e ambiente via `virt-manager` | Configuração | Concluído |
| 19/04/2026 | Mapeamento de tarefas (Filtro por Issues `Newcomer`) | Estudo | Concluído |

#### Maiores Avanços
* **Integração com a Comunidade:** Entendi que a comunidade KDE utiliza o Matrix para comunicação em tempo real e o ambiente Invent (GitLab) para o rastreamento do código e tarefas. Me apresentei formalmente na sala `#new-contributors:kde.org`.
![apresentação no Matrix](./assets/matrix.png)

* **Ambiente de Desenvolvimento de Pé:** Consegui configurar a máquina virtual no `virt-manager` utilizando os parâmetros exigidos (4 CPUs e 4096 MB de RAM). Importei o artefato de compilação da imagem e consegui instalar o KDE Linux no disco secundário formatado (`vdb - 20 GiB`). O sistema está rodando localmente de forma isolada!
![kdelinux](./assets/kdelinux.png)

#### Maiores Dificuldades
* **Mudança de Paradigma no Ambiente de Testes e Build:** Tive uma grande dificuldade inicial para compreender a arquitetura do ambiente local e como os meus testes de código seriam realizados na prática. Em projetos convencionais (como aplicações web abordadas em outros semestres), o padrão é clonar o código, instalar dependências e "subir" o ambiente compilando tudo no próprio terminal do hospedeiro (usando ferramentas como Docker, Node, etc.). No KDE Linux, por se tratar de um Sistema Operacional Imutável inteiro, o fluxo é radicalmente diferente. Demorei a entender que eu **não devo compilar o código localmente**. O ambiente de desenvolvimento em si é a Máquina Virtual rodando o arquivo `.raw`; as alterações que eu fizer no código do meu *fork* serão enviadas e construídas (*build*) pelos servidores do GitLab através de pipelines de CI/CD. A VM atua apenas como o laboratório final de testes, o que exigiu uma forte quebra de expectativa sobre o que significa "configurar o ambiente local" em projetos de sistemas operacionais.

#### Lições Aprendidas
* **Cultura de Contribuição:** Entendi a fundo os pilares do Código de Conduta do KDE, especialmente os de pragmatismo e colaboração mútua ("Be collaborative", "Be pragmatic"). Seguir as diretrizes oficiais e se comunicar ativamente é a chave.
* **Atenção Estrita à Documentação:** Seguir passo a passo a documentação oficial (quando existente) é crucial para evitar erros críticos de setup. Existem erros já previstos na documentação, e isso é importante para saber que tipo de problemas podem surgir e como resolvê-los, e entender que o build do ambiente não saiu do controle.
* **Curadoria de Tarefas:** Aprendi que ter a tag de bug não significa que a tarefa está pronta para desenvolvimento. É crucial evitar Issues marcadas como `Upstream issue` (ex: Issue #448 ou a #589 sobre Kernel Panic) pois estas dependem de alterações em repositórios de terceiros. Além disso conheci as tags `Newcomer` e `Good First Issue`, que são indicativos de tarefas mais acessíveis para novos contribuidores.

#### Mapeamento das Políticas de Contribuição e Qualidade
Diferente de repositórios comerciais no GitHub, o ecossistema do KDE possui uma estrutura descentralizada de ferramentas e políticas, gerida através de sua própria infraestrutura:

* **Gestão de Código e Revisão (KDE Invent):** O projeto não utiliza GitHub nem a nomenclatura de *Pull Requests (PRs)*. Todo o controle de versão, submissão de código e revisão *peer-to-peer* (desenvolvedor para desenvolvedor) ocorre no **KDE Invent**, uma instância do GitLab. As submissões de código são feitas através de **Merge Requests (MRs)**.
* **Separação de Issues e Bugs:** O rastreamento de problemas é categorizado. Tarefas de desenvolvimento, planejamento e *good-first-issues* (Newcomers) ficam no painel de *Work items* do GitLab. No entanto, relatos de falhas pelos usuários são gerenciados separadamente através do **KDE Bugzilla** (KDE Bugtracker).
* **Política de Nomenclatura e Pragmatismo:** Em vez de ditar regras estritas e burocráticas sobre prefixos de *branches* (como `feat/`, `bugfix/`), a política do KDE baseia-se no seu **Código de Conduta**, exigindo um desenvolvimento *pragmático* e *colaborativo*. A regra de ouro descrita na wiki oficial é a **transparência**: o contribuidor deve usar os canais de comunicação (Matrix ou comentários nas Issues do Invent) para discutir a implementação e avisar a comunidade antes de submeter um MR pesado.



#### Mapeamento de Issues
* Acessamos o painel de *Work Items* no Invent (GitLab) e utilizamos os filtros `Label is Newcomer` e `State is Open` para encontrar tarefas voltadas para novos desenvolvedores. ![issues](./assets/issues.png)
* Mapeamento das seguintes Issues com alto potencial para a nossa primeira contribuição:
  * **Issue #164:** Melhorar a descrição de atualização no aplicativo *Discover* (Atualmente exibe um texto muito genérico do KDE Linux).
  * **Issue #319:** Adicionar um *slideshow* de imagens no momento da instalação do sistema usando o Calamares.
  * **Issue #531:** Adicionar instruções na documentação sobre como usar o `mkosi` para criar imagens customizadas.

#### Plano Pessoal para a Próxima Sprint
* [ ] Escolher ativamente uma das Issues mapeadas acima e solicitar a atribuição (*assign*) no GitLab.
* [ ] Mapear a arquitetura e estudar o *codebase* específico da Issue escolhida no repositório.
* [ ] Realizar alterações no meu repositório (*fork*) e rodar testes na Máquina Virtual.
* [ ] Abrir o primeiro Pull Request / Merge Request.