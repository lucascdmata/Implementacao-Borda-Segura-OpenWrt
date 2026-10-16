# Documentação Técnica: Simulação Filial Corporativa

* **Projeto:** Laboratório de Infraestrutura Corporativa: Borda Segura (OpenWrt), Active Directory e VPN
* **Autor:** Lucas Cavalcante
* **Contexto:** Projeto prático de infraestrutura voltado para consolidação de conceitos de redes e administração de sistemas.

---

## 1. Introdução e Cenário Fictício

* **O Cenário:** Uma filial corporativa precisa prover Wi-Fi para visitantes mantendo a rede interna protegida e isolada. Além disso, a infraestrutura exige um controle de acesso centralizado para estações de trabalho (Windows e Linux) e precisa permitir acesso seguro de funcionários em Home Office (via 4G/5G) aos recursos internos.
* **A Solução:** Utilização de um roteador de borda Cudy WR3000 v1.0 com firmware OpenWrt atuando como Gateway e Firewall (local do servidor VPN a definir na próxima versão), operando em conjunto com um servidor Windows Server 2022 (controlador de domínio) para gerenciar as credenciais e a resolução de nomes da rede corporativa.

---

## 2. Objetivos

* **Objetivo Geral:** Criar uma infraestrutura de rede segura que isole diferentes perfis de usuários na borda e permita o acesso remoto criptografado à rede corporativa.
* **Objetivos Específicos:**
  1. Implementar segmentação de rede lógica criando a LAN Corporativa (`172.16.x.x`) e a rede Guest/Visitantes (`192.168.x.x`). **(Concluído ✅)**
  2. Configurar regras de Firewall para bloquear totalmente o roteamento de tráfego entre a rede Guest e a LAN Corporativa. **(Concluído ✅)**
  3. Desenhar a topologia. **(Concluído ✅)**
  4. Implantar o Windows Server 2022 como Controlador de Domínio (AD DS), DNS e DHCP na LAN Corporativa. **(Concluído ✅)**
  5. Integrar clientes Linux (Debian 12) ao domínio Active Directory Microsoft. **(Pendente ⏳)**

---

## 3. Fases de Implementação e Documentação

### Fase 1: Infraestrutura de Borda e Segurança (OpenWrt) ✅
* Instalação e configuração inicial do OpenWrt no Cudy WR3000 v1.0.
*Criação e isolamento das interfaces de rede (Corporativa e Visitantes).
* Regras de Firewall e Zone Forwarding para bloqueio do segmento Visitante.

### Fase 2: Arquitetura e Desenho da Topologia ✅
* Mapeamento completo dos ativos, sub-redes e fluxos de comunicação.
* 👉 [**Acesse aqui a Documentação da Topologia Detalhada**](Topologia/LabDoMax_Topologia_Alvo_DOCUMENTACAO.md)

### Fase 3: Identidade e Gestão Centralizada (Windows Server 2022) 🔄
* Instalação do Windows Server 2022 no Oracle VM VirtualBox. **(Concluído ✅)**
* Configuração de IP estático e hostname no servidor. **(Concluído ✅)**
* Promoção a Controlador de Domínio (AD DS), DHCP e DNS. **(Concluído ✅)**
* Ingresso de estação Linux Debian no domínio corporativo. **(Pendente ⏳)**

[Clique aqui para ver o passo a passo de como instalar o Windows Server 2022 no VirtualBox](Implementacao_Windows_Server/01_Implementacao_Windows_Server_2022.md)

[Clique aqui para ver o passo a passo de como nomear o servidor](Implementacao_Windows_Server/02_Nome_do_Servidor.md)

### Fase 4: Acesso Remoto Seguro VPN  (Pendente ⏳).
  * Configuração inicial do servidor VPN WireGuard. (local do servidor VPN a definir na próxima versão)

---

## 4. Registro e Resolução de Incidentes

Todos os incidentes técnicos ocorridos durante a implementação são documentados com resumo, diagóstico e resolução e lições aprendidas:

| ID | Descrição | Status |
|----|-----------|---------|
| INC-001 | [Perda de Credenciais Administrativas](Incidentes/Incidente_001/Perda_de_Credenciais_Administrativas.md) | ✅ Concluído |
| INC-002 | [Gargalo de Rede e Lentidão no Espelho do Debian 12](Incidentes/Incidente_002/Gargalo_de_Rede_e_Lentidao_no_Espelho_do_Debian_12.md) | ✅ Concluído |
| INC-003 | [Bloqueio de Acesso ao Zabbix](Incidentes/Incidente_003/Bloqueio_de_Acesso_ao_Zabbix.md) | ✅ Concluído |
| INC-004 | [Recuperação de Unidade RAW e VMs via TestDisk](Incidentes/Incidente_004/Recuperacao_de_Unidade_RAW_e_VMs_via_TestDisk.md) | ✅ Concluído |

