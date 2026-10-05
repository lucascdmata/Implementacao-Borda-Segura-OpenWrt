# Documentação Técnica: Implementação de Borda Corporativa Segura

**Projeto:** Implementação de Borda Corporativa Segura: Segmentação de Redes (VLAN) e Acesso Remoto utilizando OpenWrt  
**Autor:** Lucas  
**Contexto:** Projeto prático de infraestrutura voltado para consolidação de conceitos de redes e certificação CCNA.

---

## 1. Introdução e Cenário Fictício

* **O Cenário:** Uma pequena filial corporativa necessita prover acesso Wi-Fi para visitantes (isolando-os completamente dos computadores e dados da empresa). Além disso, a infraestrutura deve permitir que um funcionário em regime de *Home Office* acesse um servidor interno de forma totalmente segura utilizando internet móvel (4G/5G).
* **A Solução:** Utilização de um equipamento de borda (Gateway/Roteador) executando o firmware **OpenWrt** para acumular as funções de Roteador, Firewall Stateful e Servidor VPN.

---

## 2. Objetivos

* **Objetivo Geral:** Criar uma infraestrutura de rede segura que isole diferentes perfis de usuários na borda e permita o acesso remoto criptografado à rede corporativa.
* **Objetivos Específicos:**
  1. Implementar segmentação de rede lógica criando uma LAN Corporativa e uma rede Guest (Visitantes).
  2. Configurar serviços de DHCP dedicados para cada segmento de rede.
  3. Implementar regras de Firewall para bloquear totalmente o roteamento de tráfego entre a rede Guest e a LAN Corporativa.
  4. Configurar um túnel VPN criptografado para acesso externo seguro.
  5. Estabelecer políticas restritivas de acesso limitando o tráfego da VPN apenas aos recursos estritamente necessários da LAN (em andamento).
  6. Criar um servidor (em andamento)
---


