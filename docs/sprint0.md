# Relatório de Contribuição – Sprint 0

**Disciplina:** Gestão de Configuração e Evolução de Software   
**Equipe:** KDE Linux
**Comunidade/Projeto de Software Livre:** KDE Linux  
**Período da Sprint:** 13/04/2026 - 19/04/2026

## 1. Objetivos da Sprint
* [x] Organização da equipe (repositório GitHub).
* [x] Mapeamento das políticas de GCES do projeto.
* [x] Configuração do ambiente local (Instalação do KDE Linux em VM) e documentação dos aprendizados.

## 2. Entregas Coletivas

| Integrante | Contribuições |
|------------|---------------|
| Caio Lamego | Criação do repositório da disciplina, mapeamento das políticas de contribuição no KDE Invent, mapeamento de Issues `Newcomer` e documentação de integração (Matrix) e VM. |
| João Capozzi | Configuração nativa de ambiente local no Linux (Manjaro) usando QEMU via `virt-manager`, configuração de firmware UEFI e boot direto via arquivo `.raw`. |
| João Pedro | Configuração de ambiente local no Windows utilizando VirtualBox, incluindo a conversão de formato de disco (`.raw` para `.vmdk`) via `VBoxManage` e ativação de EFI para o boot. |
| Victório Lázaro | Setup avançado de VM isolada (Ubuntu) com Virtual Machine Manager e VirtioFS para compartilhar o repositório local e buildar a imagem sem quebrar dependências do host (BTRFS). Pedido de atribuição em issue `Newcomer`. |
| Renan Lacerda | Preparar infraestrutura local isolada e segura para compilar o sistema operacional KDE Linux. Criação e particionamento manual de VM (QEMU/KVM) com Ubuntu Server e sistema de arquivos nativo Btrfs para realizar build local. |
| Diego Carlito | Setup de build local via Virt-Manager. Resolução de gargalos de espaço e BTRFS do Docker para gerar e validar a imagem customizada do sistema. |
| Felipe Amorim | Leitura dos guias de envolvimento e contribuição KDE, criação de conta no Matrix (salas `#new-contributors` e KDE Linux), instalação do KDE Linux via VirtualBox (conversão `.raw` → `.vmdk`), criação de conta no Invent KDE, fork do repositório e build local da imagem utilizando **Podman** com driver Btrfs isolado, sem impactar configurações globais do Docker. |

## 3. Maiores Avanços
* **Configuração de Ambiente Multiplataforma:** Toda a equipe obteve sucesso em subir o KDE Linux localmente de forma isolada, superando a barreira de virtualização do OS em diferentes ecossistemas: Windows via VirtualBox, Manjaro via QEMU e Ubuntu via Virtual Machine Manager.
* **Setup de Build Isolado (VirtioFS):** Criação de um ambiente de *build* por meio de uma VM com driver BTRFS nativo, interligada ao repositório do hospedeiro usando VirtioFS, viabilizando o uso do script `build_docker.sh` localmente.
* **Mapeamento de Ferramentas e Políticas:** A equipe conseguiu mapear com clareza o ecossistema descentralizado do projeto, compreendendo que as submissões de código ocorrem no *KDE Invent* (via Merge Requests), os bugs ficam no *Bugzilla* e as regras baseiam-se em pragmatismo e colaboração.
* **Integração com a Comunidade:** Início do contato com os desenvolvedores oficiais na sala `#new-contributors:kde.org` (Matrix).
* **Build containerizado via Podman com Btrfs isolado:** Configuração do driver de storage Btrfs exclusivamente no Podman (`/etc/containers/storage.conf`), permitindo o build da imagem sem afetar outros projetos Docker rodando no host. Utilização do `mkosi.local.conf` com espelhos americanos e downloads paralelos para otimizar o processo.

## 4. Maiores Dificuldades
* **Mudança de Paradigma na Arquitetura (Build):** O projeto difere drasticamente de aplicações web. Não é possível compilar o código diretamente no terminal do hospedeiro sem afetar os drivers globais (como a exigência de BTRFS para o Docker local). O fluxo delega o *build* pesado para os pipelines de CI/CD do GitLab, atuando a VM apenas como laboratório.
* **Complexidade de Boot e Formatos de Disco:** O sistema não distribui uma ISO tradicional. A equipe teve que lidar com a conversão de arquivos `.raw` para `.vmdk` no VirtualBox e com a montagem nativa no QEMU.
* **Escassez de Tarefas Iniciais e Upstream Issues:** A base do repositório conta com poucas *issues* adequadas para novatos (tag `Newcomer`). Além disso, muitas aparentes melhorias dependem de alterações em repositórios de terceiros (*Upstream issues*), exigindo extrema cautela na seleção.
* **Acesso ao homeserver Matrix do KDE:** Confusão inicial ao tentar autenticar diretamente no homeserver `kde.org` em vez do `matrix.org`, bloqueando a entrada nas salas da comunidade.
* **Instabilidade de conexão durante o build:** Perdas de conexão com `archive.archlinux.org` durante o processo de build exigiram múltiplas tentativas até a conclusão.

## 5. Lições Aprendidas
* **Cultura e Políticas do KDE:** Compreendemos os pilares fundamentais da comunidade (pragmatismo e *"Be collaborative"*). O projeto exige transparência nas interações e uso constante de *Merge Requests (MRs)* dentro de sua instância do GitLab.
* **Conceitos de Virtualização:** Adquirimos conhecimento valioso sobre o impacto do EFI/UEFI em sistemas Linux modernos e as diferenças de formatação e compatibilidade entre `.raw`, `.vmdk` e `.vdi`.
* **Artefatos do build de uma distro Linux moderna:** Compreensão do propósito de cada arquivo gerado pelo pipeline de build (`.raw` bootável, `.efi` UKI, `.erofs` rootfs comprimido, símbolos de debug `.tar.zst`), aprofundando o entendimento de como distribuições Linux modernas são construídas e distribuídas.
* **Podman como alternativa ao Docker:** Uso do Podman para containerização com escopo de configuração isolado por projeto, evitando conflito com o daemon Docker global ao configurar o driver Btrfs.

## 6. Planejamento para a Próxima Sprint
* [ ] Escolher e receber a atribuição definitiva (*assign*) de issues abertas com a tag `Newcomer`.
* [ ] Acompanhar ativamente discussões da comunidade na rede Matrix.
* [ ] Estudar o *codebase* específico de cada tarefa e executar as alterações no *fork* do repositório.
* [ ] Abrir os primeiros *Merge Requests* (MRs) no KDE Invent.
