# Documentação Técnica: Implementação de Borda Corporativa Segura

* **Projeto:** Implementação de Borda Corporativa Segura com OpenWrt e Active Directory
* **Autor:** Lucas Cavalcante
* **Contexto:** Projeto prático de infraestrutura voltado para consolidação de conceitos de redes, administração de sistemas e preparação para a certificação CCNA.

---

## 1. Introdução e Cenário Fictício

* **O Cenário:** Uma filial corporativa precisa prover Wi-Fi para visitantes mantendo a rede interna protegida e isolada. Além disso, a infraestrutura exige um controle de acesso centralizado para estações de trabalho (Windows e Linux) e precisa permitir acesso seguro de funcionários em Home Office (via 4G/5G) aos recursos internos.
* **A Solução:** Utilização de um roteador de borda Cudy WR300 com firmware OpenWrt atuando como Gateway, Firewall e Servidor VPN, operando em conjunto com um servidor Windows Server 2022 (controlador de domínio) para gerenciar as credenciais e a resolução de nomes da rede corporativa.

---

## 2. Objetivos

* **Objetivo Geral:** Criar uma infraestrutura de rede segura que isole diferentes perfis de usuários na borda e permita o acesso remoto criptografado à rede corporativa.
* **Objetivos Específicos:**
  1. Implementar segmentação de rede lógica criando a LAN Corporativa (`172.16.x.x`) e a rede Guest/Visitantes (`192.168.x.x`). **(Concluído ✅)**
  2. Configurar regras de Firewall para bloquear totalmente o roteamento de tráfego entre a rede Guest e a LAN Corporativa. **(Concluído ✅)**
  3. Mapear e desenhar a arquitetura de topologia alvo e fluxo de dados. **(Concluído ✅)**
  4. Implantar o Windows Server 2022 como Controlador de Domínio (AD DS), DNS e DHCP na LAN Corporativa. **(Em andamento 🔄)**
  5. Integrar clientes Linux (Debian 12) ao domínio Active Directory Microsoft. **(Pendente ⏳)**
  6. Configurar um túnel VPN criptografado (WireGuard) para acesso externo seguro em cenário de Duplo NAT. **(Em andamento 🔄)**

---

## 3. Fases de Implementação e Documentação

### Fase 1: Infraestrutura de Borda e Segurança (OpenWrt) ✅
* Instalação e configuração inicial do OpenWrt no Cudy WR300.
*Criação e isolamento das interfaces de rede (Corporativa e Visitantes).
* Regras de Firewall e Zone Forwarding para bloqueio do segmento Visitante.

### Fase 2: Arquitetura e Desenho da Topologia ✅
* Mapeamento completo dos ativos, sub-redes e fluxos de comunicação.
* 👉 [**Acesse aqui a Documentação da Topologia Detalhada**](docs/Topologia/LabDoMax_Topologia_Alvo_DOCUMENTACAO.md)

### Fase 3: Identidade e Gestão Centralizada (Windows Server 2022) 🔄
* Instalação do Windows Server 2022 no Oracle VM VirtualBox. **(Concluído ✅)**
* Configuração de IP estático e hostname no servidor. **(Concluído ✅)**
* Promoção a Controlador de Domínio (AD DS), configuração de escopo DHCP e zonas DNS. **(Pendente ⏳)**
* Ingresso de estação Linux Debian no domínio corporativo (`realmd`/`sssd`). **(Pendente ⏳)**

### Fase 4: Acesso Remoto Seguro e VPN (WireGuard) 🔄
* Instalação e provisionamento do servidor VPN Debian na rede corporativa.
* Configuração de rotas e mapeamento de portas para contorno de Duplo NAT.

---

## 4. Registro e Resolução de Incidentes

Todos os incidentes técnicos ocorridos durante a implementação são documentados com análise de causa raiz, passos de recuperação e lições aprendidas:

* [INC-001: Perda de Credenciais Administrativas no OpenWrt](docs/Incidentes/Incidente_001/Perda_de_Credenciais_Administrativas.md)

