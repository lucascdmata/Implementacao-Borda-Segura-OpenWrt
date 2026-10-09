# 🛡️ Implementação de Borda Corporativa Segura com OpenWrt e Active Directory (Em andamento)

Projeto de infraestrutura de redes focado em segmentação corporativa, isolamento de visitantes (Guest Wi-Fi), gerenciamento de identidade com Active Directory e acesso remoto seguro via VPN. Desenvolvido como parte dos estudos práticos em Redes de Computadores para consolidação de conhecimentos e preparação para a certificação CCNA.

## 📌 Cenário Fictício
**Problema:** Uma filial corporativa precisa prover Wi-Fi para visitantes mantendo a rede interna protegida e isolada. Além disso, a infraestrutura exige um controle de acesso centralizado para estações de trabalho (Windows e Linux) e precisa permitir acesso seguro de funcionários em Home Office (via 4G/5G) aos recursos internos.

**Solução:** Utilização de um roteador de borda Cudy WR300 com firmware OpenWrt atuando como Gateway, Firewall e Servidor VPN, operando em conjunto com um servidor Windows Server 2022 (controlador de domínio) para gerenciar as credenciais e a resolução de nomes da rede corporativa.

## Planejamento & Topologia Alvo


### Visão Geral da Arquitetura
* **Borda & Segmentação:** Roteador OpenWrt isolando as redes Corporativa (172.16.x.x) e Visitante (192.168.x.x).
* **Serviços de Domínio:** Windows Server 2022 atuando Controlador de Domínio (lab.do.max.local), DNS e DHCP.
* **Acesso Remoto & Linux:** Servidor Debian 12 integrado ao AD e executando serviço de VPN WireGuard.
* **Monitoramento NOC:** Samsung Galaxy J1 atuando como dashboard dedicado de status da rede.




## 🛠️ Tecnologias e Recursos
* **Rede e Borda:** Roteador Cudy WR300 V1.0 (OpenWrt).
* **Virtualização:** Oracle VM VirtualBox.
* **Sistemas Operacionais:** Windows Server 2022 e Linux Debian 12.
* **Protocolos e Conceitos:**
  * VLANs (802.1Q) e múltiplos SSIDs.
  * Firewall Stateful e regras de zona (Zones & Forwarding Rules).
  * Active Directory Domain Services (AD DS), DHCP e DNS.
  * Integração de cliente Linux em domínio Microsoft (`realmd`, `sssd`).
  * VPN Criptografada (WireGuard / OpenVPN).
  * NAT e gerenciamento de Duplo NAT.

## 📂 Estrutura do Repositório
* `/docs` -> Contém a documentação completa e detalhada do projeto, configurações e evidências (nos moldes de projeto técnico corporativo).
* `/topologia` -> Diagramas [Detalhes](docs/Topologia/Imagem.md)
* 

## 🚀 Atualizações do Projeto

**Fase 1: Infraestrutura de Borda e Segurança (Concluída ✅)**
* Criação das interfaces corporativa (172.16.x.x) e visitantes (192.168.x.x).
* Configuração de redes Wi-Fi e SSIDs vinculados às respectivas interfaces.
* Implementação de políticas de Firewall para bloqueio de tráfego da rede Visitante para a rede Corporativa.

**Fase 2: Identidade e Gestão Centralizada (Em andamento 🔄)**
* Instalação do Windows Server 2022 no VirtualBox (Iniciada em 04/10/2026) ✅.
* Configuração de endereçamento IP estático do Servidor na rede Corporativa (172.16.x.x) ✅.
* Promoção do servidor a Controlador de Domínio (AD DS) e configuração de DNS (Pendente ⏳).
* Instalação de máquina virtual Linux Debian e ingresso no domínio corporativo via Wi-Fi (Pendente ⏳).

**Fase 3: Acesso Remoto Seguro VPN (Em andamento 🔄)**
* Configuração inicial do servidor VPN WireGuard.
* Mapeamento e contorno de barreiras de infraestrutura (Cenário de Duplo NAT com o modem da operadora).
---
## Registro de Incidentes

| ID | Descrição | Status |
|----|-----------|---------|
| INC-001 | docs/Incidentes/Incidente 001/Perda de Credenciais Administrativas.md | ✅ Concluído |
