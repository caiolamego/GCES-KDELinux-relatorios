# Diário de Bordo – Diego Carlito Rodrigues de Souza

**Disciplina:** Gerência de Configuração e Evolução de Software
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

* [ ] Solicitar o *assign* em uma das *issues* de nível *Newcomer* mapeadas.
* [ ] Submeter o primeiro Merge Request (MR) seguindo os padrões de contribuição da comunidade.