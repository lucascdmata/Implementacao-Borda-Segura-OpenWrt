# 🛡️ Implementação de Borda Corporativa Segura com OpenWrt

Projeto de infraestrutura de redes focado em segmentação corporativa, isolamento de visitantes (Guest Wi-Fi) e acesso remoto seguro via VPN (Zero-Trust), aplicando conceitos práticos de redes e certificação CCNA.

## 📌 Cenário Fictício
* **Problema:** Uma filial corporativa precisa prover Wi-Fi para visitantes mantendo a rede interna protegida, além de permitir acesso seguro de funcionários em *Home Office* (via 4G/5G) a um servidor interno.
* **Solução:** Utilização de um roteador de borda **Cudy WR300** com firmware **OpenWrt** atuando como Gateway, Firewall e Servidor VPN.

## 🛠️ Tecnologias e Recursos
* **Hardware/Firmware:** Roteador Cudy WR300 (OpenWrt).
* **Protocolos e Conceitos:** 
  * VLANs (802.1Q) e múltiplos SSIDs.
  * Firewall Stateful e regras de zona (Zones & Forwarding Rules).
  * VPN Criptografada (WireGuard / OpenVPN).
  * NAT e gerenciamento de Duplo NAT.

## 📂 Estrutura do Repositório
* `/docs` -> Contém a documentação completa e detalhada do projeto (nos moldes de projeto técnico/acadêmico).
* `/topology` -> Diagrama lógico da rede.

---
*Desenvolvido como parte dos estudos práticos em Redes de Computadores e CCNA.*

## Atualizações

* Fase 1 Concluída ✅ - Introdução e Cenário Fictício
* Fase 2 parte 1 Concluída ✅ - Firewall e políticas de acesso
* Fase 2 parte 2 Em andamento 🔄 - VPN WireGuard

## Incidentes Registrados
 
| ID      | Descrição            | Status
|---------|------------|---------|
| INC-001 | Recuperação de       | Resolvido
