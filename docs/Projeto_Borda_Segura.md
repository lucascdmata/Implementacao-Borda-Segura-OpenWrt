# Documentação Técnica: Implementação de Borda Corporativa Segura

**Projeto:** Implementação de Borda Corporativa Segura com OpenWrt e Active Directory
**Autor:** Lucas  
**Contexto:** Projeto prático de infraestrutura voltado para consolidação de conceitos de redes e certificação CCNA.

---

## 1. Introdução e Cenário Fictício

* **O Cenário:** Uma filial corporativa precisa prover Wi-Fi para visitantes mantendo a rede interna protegida e isolada. Além disso, a infraestrutura exige um controle de acesso centralizado para estações de trabalho (Windows e Linux) e precisa permitir acesso seguro de funcionários em Home Office (via 4G/5G) aos recursos internos.
* **A Solução:** Utilização de um roteador de borda Cudy WR300 com firmware OpenWrt atuando como Gateway, Firewall e Servidor VPN, operando em conjunto com um servidor Windows Server 2022 (controlador de domínio) para gerenciar as credenciais e a resolução de nomes da rede corporativa.

---

## 2. Objetivos

* **Objetivo Geral:** Criar uma infraestrutura de rede segura que isole diferentes perfis de usuários na borda e permita o acesso remoto criptografado à rede corporativa.
* **Objetivos Específicos:**
  1. Implementar segmentação de rede lógica criando uma LAN Corporativa e uma rede Guest (Visitantes).
  2. Configurar serviços de DHCP dedicados para cada segmento de rede. (Em desenvolvimento)
  3. Implementar regras de Firewall para bloquear totalmente o roteamento de tráfego entre a rede Guest e a LAN Corporativa. (Em desenvolvimento)
  4. Configurar um túnel VPN criptografado para acesso externo seguro. (Em desenvolvimento)
  5. Estabelecer políticas restritivas de acesso limitando o tráfego da VPN apenas aos recursos estritamente necessários da LAN (em andamento).
  6. Criar um servidor Windows (em andamento)
  
## 3. Fases de Implementação e Documentação

Abaixo estão os guias detalhados de cada etapa da construção desta infraestrutura, documentados passo a passo:

### Preparação do Ambiente Base (Windows Server 2022)
Nesta fase inicial, preparamos o servidor base que atuará na rede corporativa, configurando sua identidade e conectividade para que futuramente possa hospedar serviços essenciais.

* [Instalação do Servidor na Máquina Virtual](Implementacao_Windows_Server/01_Implementacao_Windows_Server_2022.md)
  
* Configuração de IP Estático na LAN (Em desenvolvimento)
  
* Padronização do Nome do Servidor Hostname (Em desenvolvimento)


### Fase 2: Configuração da Borda (OpenWrt)
*(Em desenvolvimento...)*

### Fase 3: Segmentação de Redes e Firewall
*(Em desenvolvimento...)*

