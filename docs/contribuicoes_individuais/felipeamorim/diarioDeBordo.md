# Diário de Bordo – Felipe Amorim de Araújo

**Disciplina:** Gerência de Configuração Evolução de Software

**Comunidade/Projeto de Software Livre:** KDE Linux

---

## Sprint 0 – 08/04 - 22/04

### Resumo da Sprint

Nesse Sprint, foquei em me familiarizar com a comunidade KDE, seus canais de comunicação e o processo de contribuição. Realizei a instalação do KDE Linux em uma máquina virtual para entender melhor o ambiente de desenvolvimento e os requisitos para contribuir com o projeto. Também criei minha conta no Invent KDE e configurei meu ambiente local para realizar o build da imagem do KDE Linux utilizando o Podman. 

### Atividades Realizadas

| Data  | Atividade                                   | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status    |
| ----- | ------------------------------------------- | --------------------------------- | --------------- | --------- |
| 11/04 | Primeira leitura dos guias de envolvimento e contribuição na comunidade KDE | Estudo | [Get Involved](https://community.kde.org/Get_Involved), [Wiki KDE Linux](https://community.kde.org/KDE_Linux), [Documentação KDE Linux](https://kde.org/linux/docs/) | Concluído |
| 11/04 | Criação da conta no Matrix e entrada nas salas do KDE New Contributors e KDE Linux | Discussão | [Perfil Matrix](./assets/matrix_account.png), [Salas do KDE](./assets/kde_rooms.png) | Concluído |
| 12/04 | Instalação do KDE Linux em uma máquina virtual | Código | [KDE Linux na VM](./assets/kde_linux_vm.png), [Tutorial](https://kde.org/linux/docs/install/), [Wiki](https://community.kde.org/KDE_Linux) | Concluído |
| 20/04  | Criação da minha conta no Invent KDE | Discussão | [Perfil](https://invent.kde.org/lipeaaraujo) | Concluído |
| 21/04 | Criação do fork do repositório principal do KDE Linux | Código | [Fork](https://invent.kde.org/lipeaaraujo/kde-linux) | Concluído |
| 21/04 | Configuração do ambiente de desenvolvimento e build da imagem do KDE Linux localmente | Código | [Mensagem de sucesso do build](./assets/build_message.png), [Arquivos gerados](./assets/generated_files.png), [Imagem buildada rodando na VM]()  | Concluído |

### Maiores Avanços

<!-- * \[Exemplo] Aprendi a rodar a aplicação localmente. -->
<!-- * \[Exemplo] Entendi melhor a organização do repositório. -->

### Maiores Dificuldades

<!-- * \[Exemplo] Ambiente demorou para configurar por falta de dependências. -->
* **Entrar nas rooms pelo Matrix**: Tive problemas para entrar nas salas do Matrix, pois não tinha entendido que era possível entrar diretamente pelo homeserver do Matrix sem precisar logar no homeserver do KDE. 

### Aprendizados

<!-- * Uso básico de GitHub Issues. -->
<!-- * Fluxo de contribuição do projeto. -->



### Criação da conta no Matrix e entrada nas salas do KDE

### Instalação do KDE Linux em uma máquina virtual

### Processo de build da imagem do KDE Linux

Tendo criado o fork do repositório e clonado em minha máquina local, existem 2 opções para realizar o build da imagem do KDE Linux:

1. Build da imagem via Docker ou Podman, utilizando o script `./build_docker.sh [--podman] [--country <country-code>] [--parallel <num>]`.
2. Buildar em um host com Arch Linux, seguindo o pipeline de build:
    - `bootstrap.sh`: configura o ambiente de build, incluindo a instalação de dependências e configuração de repositórios personalizados do KDE.
    - `./build.sh [--force] [--debug]`: Orquestra o processo completo de build, desde a compilação de ferramentas Rust, geração do rootfs com mkosi, montagem da imagem de disco e criação dos arquivos de saída.

Optei por seguir com a primeira opção, utilizando o Podman ao invés do Docker. Um dos requisitos para fazer o build containerizado é ter o driver de storage Btrfs configurado no Docker/Podman, para que o processo de build possa montar os arquivos de sistema de arquivos necessários para a construção da imagem do KDE Linux. Utilizando o Podman consegui isolar a configuração para não impactar outros containers e projetos que estou rodando com o Docker.

O processo se resumiu em instalar o Podman e configurar o driver de storage Btrfs alterando no arquivo `/etc/containers/storage.conf`:

```
driver = "btrfs"
```


Também seguindo as instruções do guia de desenvolvimento, criei um arquivo de configuração local `mkosi.local.conf` para acelerar o processo de build, com o seguinte conteúdo:

```
[Content]
Environment=LOCALE_GEN="C.UTF-8 UTF-8"
Environment=MIRRORS_COUNTRY=br
Environment=PARALLEL_DOWNLOADS=50
```

Após isso, executei o comando de build utilizando o Podman:

```
./build_docker.sh --podman
```

Tive rodar o comando algumas vezes por conta de perdas de conexão com os repositórios necessários para a instalação e sincronização dos pacotes e dependências (em especial o `archive.archlinux.org`), mas consegui completar o processo de build e gerar a imagem do KDE Linux localmente.

**Mensagem de sucesso do build**:
![mensagem-build](./assets/build_message.png)

**Arquivos gerados**:
![arquivos-gerados](./assets/generated_files.png)

Cada um dos arquivos gerados tem uma função específica no processo de boot e execução do KDE Linux, como descrito na tabela abaixo:

| Nome do arquivo | Descrição |
| ------------------------------------------- | -------------------------- |
| kde-linux_202604220029.raw                  | Imagem bootável    |
| kde-linux_202604220029.efi                  | Unified Kernel Image (UKI) |
| kde-linux_202604220029_erofs.addon.efi      | Erofs addon EFI            |
| kde-linux_202604220029_root-x86-64.erofs    | Rootfs comprimido          |
| kde-linux_202604220029_debug-x86-64.tar.zst | Arquivo de símbolos de debug      |
| kde-linux_202604220029/                     | Diretório do rootfs construído     |

Por fim, rodei a imagem do KDE Linux na máquina virtual utilizando o VirtualBox, e consegui iniciar o sistema operacional com sucesso, confirmando que o processo de build foi concluído corretamente.

**KDE Linux buildado rodando na VM**:
![kde-linux-vm](./assets/kde_linux_vm_running.png)

### Plano Pessoal para a Próxima Sprint

<!-- * [ ] Contribuir com pelo menos 1 PR. -->
<!-- * [ ] Participar da revisão de código de um colega. -->

---

