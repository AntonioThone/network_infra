# Projeto de Infraestrutura de Redes - POWER ANGOLA, Lda (empresa fictícia)

## Sobre o Projeto
Este repositório documenta a implementação de uma infraestrutura de redes complexa e distribuída para a fictícia empresa de engenharia e desenvolvimento de softwares, **POWER ANGOLA, Lda**. O objetivo principal foi integrar as filiais de **Luanda** e **Cabinda**, garantindo que todos os colaboradores tivessem as mesmas condições de trabalho e acesso aos recursos da rede, independentemente de sua localização.

A solução foi projetada e implementada em um ambiente virtualizado, utilizando os sistemas operacionais **Windows Server 2016/2019 Enterprise Edition** e **máquinas clientes Windows 7, 8 e 10**.

## Ambiente de Desenvolvimento e Topologia de Rede
O ambiente foi simulado no **VMware Workstation Pro 17**, proporcionando um laboratório realista e flexível para testes. A comunicação entre os dois sites foi estabelecida através de um cabo crossover e interfaces de rede virtuais, simulando um enlace WAN real.

A topologia da rede consiste em dois sites interconectados:

* **SITE A (Luanda)**: IP: `144.188.5.0/24`
    * **luaw19vm1 (Domain Controller)**: `144.188.5.10`
    * **luaw16vm2 (File Server)**: `144.188.5.11`
* **SITE B (Cabinda)**: IP: `144.188.5.0/24`
    * **cabw19vm1 (Servidor)**: `144.188.5.20`
    * **cabw16vm2 (Servidor)**: `144.188.5.21`

Para uma visualização clara da arquitetura, consulte o diagrama abaixo:
---

## Tecnologias e Serviços Implementados
Este projeto demonstra domínio na configuração e gestão de uma variedade de serviços essenciais para uma rede corporativa moderna. O projeto incluiu:

* **Serviços de Diretório e Autenticação**: Active Directory Domain Services (AD DS).
* **Serviços de Rede**: DNS, DHCP e roteamento estático.
* **Gestão de Política e Segurança**: Group Policy Objects (GPO) para mapeamento de drives, restrições de logon e personalização do ambiente de utilizadores.
* **Gestão de Ficheiros**: DFS Namespaces, DFS Replication e File Server Resource Manager (FSRM) para gestão de quotas e compartilhamentos.
* **Armazenamento**: Configuração de **Storage Spaces com RAID-5 (Parity)** e discos **iSCSI**.
* **Alta Disponibilidade e Redundância**: NIC Teaming para agregação de links e **Failover Clustering**.
* **Serviços Web e de Ficheiros**: Internet Information Services (IIS) para o website da empresa (`www.style.com`) e um servidor FTP (`ftp.style.com`).
* **Automação e Scripting**: Utilização de **PowerShell** para consultas e validação das configurações.

## Fases da Implementação e Configuração

### Fase 1: Configuração Básica de Rede e Domínio
* Instalação e configuração inicial das VMs no VMware Workstation Pro 17.
* Configuração do endereçamento IP estático para os servidores.
* Promoção de `luaw19vm1` a Domain Controller do domínio `style.com`.
* Configuração dos serviços de DHCP e DNS para a rede de Luanda.

### Fase 2: Implementação de Serviços no `luaw16vm2`
* Instalação das roles de **File Server, Storage, Print Server, FTP, IIS, DFS** e **Failover Clustering**.
* Configuração de **BGInfo** para exibir informações do servidor no desktop.
* Criação de pools de armazenamento e volumes virtuais com **RAID-5 (Parity)** e discos **iSCSI**.
* Configuração de um DFS Namespace e dos compartilhamentos de rede com quotas de **1 GB por utilizador** (via FSRM).
* Criação do website da empresa no IIS e do servidor FTP.

### Fase 3: Configuração Avançada do Active Directory e GPOs
* Criação de uma estrutura de OUs para Luanda (`Luanda`, `Users`, `Computers`, etc.).
* Criação de grupos de segurança por departamento (`DG_Users`, `IT_Users`, etc.) e administradores.
* Criação de utilizadores com restrições de logon para contas contratadas.
* Configuração de GPOs para:
    * **Mapeamento automático de drives** (P: para `Users` e O: para `Dropbox`).
    * **Definição do wallpaper** padrão para os utilizadores.
    * **Execução automática de BGInfo** para os servidores.

### Fase 4: Integração de Clientes e Validação
* Configuração e ingresso do cliente **`luacliente1`** no domínio `style.com`.
* Validação de todos os serviços e políticas:
    * Testes de conectividade (`ping`, `nslookup`).
    * Confirmação de que as unidades de rede P: e O: foram mapeadas automaticamente.
    * Validação do acesso aos compartilhamentos de departamento.
    * Confirmação de que o wallpaper foi aplicado e que o site e o FTP da empresa estão acessíveis.

---

## Prova de Habilidade
Dado que este é um projeto de infraestrutura de redes, que não pode ser executado diretamente no GitHub, a documentação é a principal prova de minhas habilidades. As imagens abaixo servem como evidência visual da implementação e funcionalidade de cada etapa do projeto.

* **Estrutura de OUs no Active Directory**
* **Mapeamento de Drives via GPO**
* **Configurações do Storage Spaces**
* **Serviços Instalados no Server Manager**
* **Teste de Conectividade entre Sites**

---

## Licença
Este projeto está sob a licença MIT. Para mais detalhes, veja o arquivo `LICENSE`.