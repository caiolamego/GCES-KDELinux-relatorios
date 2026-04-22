# Diário de Bordo – Renan Lacerda

## Sprint 0 - 14/04/2026 - 22/04/2026

### Resumo da Sprint

Esta sprint inicial foi focada no setup do ambiente de desenvolvimento e na compreensão da arquitetura do ecossistema KDE e Linux. O objetivo principal foi preparar uma infraestrutura local isolada e segura para compilar o sistema operacional KDE Linux a partir do código-fonte, utilizando Docker e Btrfs, além de resolver as questões de acesso à comunidade. A sprint foi finalizada com uma tentativa de build que revelou uma instabilidade nos servidores do KDE.

### Atividades Realizadas
| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 14/04 | Estudo da documentação e arquitetura | Doc / Discussão | [KDE-Linux](https://invent.kde.org/kde-linux/kde-linux) | Concluído |
| 14/04 | Baixar imagem .raw do KDE Linux | Setup | [Installing in a Virtual Machine](https://kde.org/linux/docs/install-vm/) | Concluído |
| 14/04 | Instalar KDE Linux em uma vm QEMU/KVM utilizando o virt-manager | Setup | [Installing in a Virtual Machine](https://kde.org/linux/docs/install-vm/) | Concluído |
| 21/04 | Criar conta no KDE indentity e Invent | Setup | [KDE-Identity](https://identity.kde.org/) | Concluído |
| 21/04 | Criar fork do repositório oficial do KDE Linux | Setup | [KDE-Linux-LacerdaRenan](https://invent.kde.org/lacerdarenan/kde-linux) | Concluído |
| 22/04 | Criação e particionamento manual de VM (QEMU/KVM) com Ubuntu Server e sistema de arquivos nativo Btrfs | Setup | - | Concluído |
| 22/04 | Build local do KDE-Linux | Setup | [KDE-Linux-dev](https://kde.org/linux/docs/kde-linux-dev/) | Concluído |

### Maiores Avanços

* Sucesso na montagem de um ambiente de build isolado, utilizando uma vm com ubuntu-server configurado para usar o btrfs.

* Sucesso para instalar o KDE-Linux na vm, todo o processo foi feito seguindo a documentação disponível em [Installing in a Virtual Machine](https://kde.org/linux/docs/install-vm/).

### Maiores Dificuldades

* Configuração do ambiente para buildar a imagem do KDE-Linux, pois é necessário que o docker utilize o filesystem btrfs. 

* Durante o build, a pipeline de compilação falhou ao tentar realizar o download do arquivo (build_date.txt). O log de erro retornou um código de status 404 NoSuchKey.

### Aprendizados

* Dinâmica sobre contribuições em projetos Open Source.

* Orquestração de Build de Baixo Nível.

### Plano Pessoal para a Próxima Sprint

* [] Encontrar uma issue disponível para novos contribuidores.
* [] Resolver issue.


