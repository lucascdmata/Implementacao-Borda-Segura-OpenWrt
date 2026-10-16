# Documentação de Arquitetura e Topologia de Rede
Este documento detalha o planejamento, a segmentação e os fluxos de comunicação do laboratório corporativo de borda segura.

## Diagrama da Topologia

### Visão Geral da Arquitetura
A arquitetura foi projetada para simular um ambiente corporativo moderno, priorizando a segmentação de rede, controle centralizado de identidades e acesso remoto seguro.

[Clique aqui para ver a Topologia](LabDoMax_Topologia_Alvo.png)
#### Borda & Roteamento (Gateway)
- Dispositivo: Roteador Cudy WR3000 V1.0
- Sistema Operacional: OpenWrt
- Função Principal: Roteamento de borda, gerenciamento de SSIDs e aplicação de políticas de Firewall.
- Conexão WAN: Interface conectada à rede da operadora (Claro) para acesso à Internet.

## 🌐Segmentação de Rede (Interfaces & Wi-Fi)
A rede está dividida em duas zonas isoladas.

![Criação](Diagrama.drawio.png)

## 🛡️Políticas de Segurança & Firewall

- Isolamento Visitante: Regras estritas de Firewall configuradas no OpenWrt impedem que qualquer dispositivo na rede Visitantes (192.168.x.x) inicie tráfego para a rede Corporativa (172.16.x.x).
- DHCP Customizado: O serviço DHCP do OpenWrt é mantido desativado na interface Corporativa para permitir que o Active Directory gerencie a distribuição de IPs e opções de DNS.


## 🖥️Servidores e Serviços Core (Rede Corporativa)

### 1. Host de Virtualização

- Virtualizador: Oracle VM VirtualBox rodando no sistema host.
- Modo de Rede: Placas de rede virtuais em Modo Bridge, permitindo que as Máquinas Virtuais (VMs) obtenham endereçamentos diretos da sub-rede 172.16.x.x.

### 2. Controlador de Domínio (Windows Server 2022)

- Função: Active Directory Domain Services (AD DS), Servidor DNS e Servidor DHCP.
- Domínio: lab.do.max.local
- Escopo: Responsável por responder às requisições de nomes internos, autenticação corporativa e entrega de IP para a rede interna.


### 3. Servidor de Acesso Remoto (local do servidor VPN a definir na próxima versão)

- Função: VPN WireGuard
- 



## 📱Terminais e Dispositivos Clientes

- Estação de Trabalho Linux: Máquina Virtual Debian 12 integrada como membro ativo do Active Directory (Pendente ⏳).
- Terminal NOC / Monitoramento: Smartphone Samsung Galaxy J1 conectado via Wi-Fi Corporativa, utilizado como painel dedicado para monitoramento via HTTP dos serviços locais.  (Pendente ⏳).
- Smartphone (Acesso Visitante & Remoto) (Pendente ⏳): 
  - Quando conectado na rede local via Wi-Fi Visitantes, possui acesso apenas à Internet.
  - Quando fora do ambiente local (via 4G/5G), utiliza o cliente WireGuard para fechar um túnel criptografado com o Servidor VPN Debian, obtendo acesso seguro à rede Corporativa.


 
## 🔄Fluxo de Comunicação & VPN

1° Tráfego Interno (Corporativo): Dispositivos na sub-rede 172.16.x.x utilizam o Windows Server como DNS primário e o OpenWrt como Gateway padrão.

2° Tráfego Externo (VPN): (Pendente ⏳).

