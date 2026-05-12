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
| 14/04 | Leitura dos guias de envolvimento e contribuição na comunidade KDE        | Estudo                            | [Link](https://community.kde.org/Get_Involved)                                          | Concluído |
| 15/04 | Instalação do KDE Linux via VM (Virt-Manager)                             | Estudo                            | [Link](https://kde.org/linux/docs/install-vm/), [Captura de tela](./assets/kde_linux_vm_running.png) | Concluído |
| 16/04 | Avaliação da primeira Issue para trabalhar (Filtro *Newcomer*)            | Estudo                            | [Link](https://invent.kde.org/kde-linux/kde-linux/-/work_items?label_name[]=Newcomer)   | Concluído |
| 18/04 | Criação do fork                                                           | Código                            | [Link](https://invent.kde.org/diegocarlito/kde-linux)                                   | Concluído |
| 19/04 | Instalação e configuração da VM de Build (Virt-Manager, UEFI, 4GB RAM)    | Infra                             | -                                                                                       | Concluído |
| 20/04 | Configuração de sistema de arquivos compartilhado (VirtioFS) entre Host e VM| Infra                           | -                                                                                       | Concluído |
| 21/04 | Ajuste do Docker (BTRFS), expansão de disco e compilação da imagem        | Código                            | [Captura de tela](./assets/build_message.png)                                           | Concluído |
| 21/04 | Criação do relatório de contribuição individual                           | Doc                               | -                                                                                       | Concluído |

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

* [ ] Monitorar o processo de *Code Review* e aplicar eventuais revisões solicitadas pelos mantenedores.
* [ ] Iniciar o mapeamento de *issues* de código (C++/Bash) para a próxima etapa de contribuição.