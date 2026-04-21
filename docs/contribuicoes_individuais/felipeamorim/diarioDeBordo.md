# Diário de Bordo – Felipe Amorim de Araújo

**Disciplina:** Gerência de Configuração Evolução de Software

**Comunidade/Projeto de Software Livre:** KDE Linux

---

## Sprint 0 – 08/04 - 22/04

### Resumo da Sprint

Breve descrição das atividades e reflexões.

### Atividades Realizadas

| Data  | Atividade                                   | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status    |
| ----- | ------------------------------------------- | --------------------------------- | --------------- | --------- |
| 11/04 | Primeira leitura dos guias de envolvimento e contribuição na comunidade KDE | Estudo | [Link](https://community.kde.org/Get_Involved) | Concluído |
| 11/04 | Criação da conta no Matrix e entrada nas salas do KDE New Contributors e KDE Linux | Discussão | [Perfil Matrix](./assets/matrix_account.png), [Salas do KDE](./assets/kde_rooms.png) | Concluído |
| 12/04 | Instalação do KDE Linux em uma máquina virtual | Código | [KDE Linux na VM](./assets/kde_linux_vm.png), [Tutorial](https://kde.org/linux/docs/install/), [Wiki](https://community.kde.org/KDE_Linux) | Concluído |
| 20/04  | Criação da minha conta no Invent KDE | Discussão | [Perfil](https://invent.kde.org/lipeaaraujo) | Concluído |
| 21/04 | Criação do fork do repositório principal do KDE Linux | Código | [Fork](https://invent.kde.org/lipeaaraujo/kde-linux) | Concluído |
| 21/04 | Configuração do ambiente de desenvolvimento e build da imagem do KDE Linux localmente | Código |  | Andamento |

### Maiores Avanços

<!-- * \[Exemplo] Aprendi a rodar a aplicação localmente. -->
<!-- * \[Exemplo] Entendi melhor a organização do repositório. -->

### Maiores Dificuldades

<!-- * \[Exemplo] Ambiente demorou para configurar por falta de dependências. -->
* **Entrar nas rooms pelo Matrix**: Tive problemas para entrar nas salas do Matrix, pois não tinha entendido que era possível entrar diretamente pelo homeserver do Matrix sem precisar logar no homeserver do KDE. 

### Aprendizados

<!-- * Uso básico de GitHub Issues. -->
<!-- * Fluxo de contribuição do projeto. -->

### Plano Pessoal para a Próxima Sprint

<!-- * [ ] Contribuir com pelo menos 1 PR. -->
<!-- * [ ] Participar da revisão de código de um colega. -->

### Processo de build da imagem do KDE Linux

Tendo criado o fork do repositório e clonado em minha máquina local, existiam 2 opções para realizar o build da imagem do KDE Linux:

1. Build da imagem via Docker ou Podman, utilizando o script `./build_docker.sh [--podman] [--country <country-code>] [--parallel <num>]`.
2. Buildar em um host com Arch Linux, seguindo o pipeline de build:
    - `bootstrap.sh`: configura o ambiente de build, incluindo a instalação de dependências e configuração de repositórios personalizados do KDE.
    - `./build.sh [--force] [--debug]`: Orquestra o processo completo de build, desde a compilação de ferramentas Rust, geração do rootfs com mkosi, montagem da imagem de disco e criação dos arquivos de saída.

---

