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

