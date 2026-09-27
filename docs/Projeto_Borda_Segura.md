# Documentação Técnica: Implementação de Borda Corporativa Segura

**Projeto:** Implementação de Borda Corporativa Segura: Segmentação de Redes (VLAN) e Acesso Remoto Zero-Trust utilizando OpenWrt  
**Autor:** Suporte de TI / Redes  
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
  5. Estabelecer políticas restritivas de acesso limitando o tráfego da VPN apenas aos recursos estritamente necessários da LAN.

---

## 3. Topologia e Recursos Utilizados

* **Gateway / Firewall de Borda:** Roteador Cudy WR300 rodando firmware OpenWrt. É o equipamento central que gerencia as redes, regras de firewall e o túnel VPN.
* **Servidor Corporativo (LAN):** Notebook conectado via Wi-Fi na rede privada local, simulando um recurso corporativo sensível (como um servidor de arquivos ou banco de dados interno).
* **Cliente Remoto (WAN / VPN):** Smartphone conectado via rede de dados móveis (4G). O celular atua como o cliente que estabelece o túnel criptografado para dentro da rede da filial.
* **Simulação de WAN:** O roteador Cudy recebe o link de internet de um modem principal da operadora local. Para contornar o cenário de Duplo NAT e permitir o tráfego de entrada da VPN, foi configurada uma DMZ no modem da operadora apontando para o IP WAN do OpenWrt.

> *(Nota: Insira aqui o diagrama de topologia gerado no Draw.io ou uma imagem representativa da estrutura).*

---

## 4. Fundamentação Técnica

* **VLAN (802.1Q):** A divisão lógica de domínios de broadcast em nível de enlace, aumentando a segurança e isolando o tráfego de diferentes departamentos ou visitantes no mesmo switch/roteador físico.
* **NAT e Port Forwarding:** Mecanismos de tradução de endereços de rede essenciais para a transição e mapeamento entre IPs públicos da WAN e endereços privados da rede interna.
* **Firewall Stateful:** Inspeção de pacotes com controle de estado, diferenciando conexões novas de pacotes pertencentes a sessões já estabelecidas, permitindo o tráfego de resposta de forma segura.
* **WireGuard / OpenVPN:** Protocolos modernos de VPN baseados em criptografia de ponta para a criação de túneis virtuais seguros sobre redes públicas (como a internet).

---

## 5. Plano de Implementação (Passo a Passo)

### Fase 1: Configuração das Redes Locais
* Criação de interfaces virtuais e físicas segregadas no OpenWrt.
* Definição das faixas de endereçamento IP (ex: `192.168.10.x` para LAN Corporativa e `192.168.20.x` para Guest).
* Configuração de múltiplos SSIDs no rádio Wi-Fi para separar os clientes corporativos dos visitantes.

### Fase 2: Políticas de Segurança (Firewall)
* Mapeamento e criação das zonas personalizadas no firewall do OpenWrt (`lan`, `guest`, `vpn` e `wan`).
* Aplicação de regras de encaminhamento (*Forwarding Rules*) para bloquear o tráfego inter-VLAN da zona `guest` para a zona `lan`.

### Fase 3: Túnel Criptografado
* Geração de chaves criptográficas para o servidor VPN.
* Configuração da interface virtual de acesso remoto e apontamento de DDNS/IP para conexões externas via 4G.

---

## 6. Testes de Validação

* **Teste 1 (Isolamento Guest):** Conectar um dispositivo no Wi-Fi "Guest" e tentar disparar um comando *ping* ou acessar o IP do Notebook corporativo. 
  * *Resultado esperado:* Falha de comunicação (*Request timed out*).
* **Teste 2 (Acesso Remoto VPN):** Conectar o smartphone na rede móvel 4G, ativar o cliente VPN e testar o acesso ao IP do Notebook corporativo.
  * *Resultado esperado:* Sucesso na comunicação (*Reply from...*).
* **Teste 3 (Segurança Administrativa):** Com a VPN ativa, tentar acessar a interface de administração do roteador de borda.
  * *Resultado esperado:* Bloqueio por regra de segurança pré-estabelecida.

---

## 7. Desafios Enfrentados e Soluções (Troubleshooting)

### Desafio 1: Perda de Conectividade e Atribuição de Endereço APIPA na Rede de Testes
* **Contexto do Problema:** Durante o processo de configuração das VLANs e da interface de visitantes no OpenWrt, foi criada uma rede Wi-Fi dedicada chamada "Teste" para isolar o ambiente de bancada da rede local principal. O notebook de configuração estava conectado a essa rede "Teste" enquanto alterava as configurações do roteador. Em determinado momento, o notebook perdeu a conectividade de forma repentina, enquanto um smartphone conectado à mesma rede "Teste" continuava operando normalmente.
* **Investigação Inicial:** 
  1. A execução do comando `ipconfig` no prompt de comando (CMD) revelou que o adaptador de rede havia recebido um endereço na faixa **APIPA (`169.254.x.x`)**, indicando falha na comunicação com o servidor DHCP do roteador, visto que o endereço esperado pertencia à faixa `10.0.x.x`.
  2. A interface gráfica do Windows indicava que o Wi-Fi "Teste" estava conectado e com status "seguro".
  3. A tentativa de executar o comando `ipconfig /release` retornou a mensagem de erro: *"no operation can be performed on Wireless Network Connection 2 while it has its media disconnected"*, evidenciando que o Windows havia perdido o enlace lógico com a placa de rede sem fio.
* **Resolução Aplicada:** 
  1. O acesso ao painel de conexões de rede foi realizado via comando `ncpa.cpl` (windows + r).
  2. Nas propriedades da placa de rede Wi-Fi, o protocolo IPv4 foi configurado manualmente com um **endereço IP estático** pertencente à mesma sub-rede do roteador.
  3. Essa intervenção restabeleceu imediatamente a rota e a estabilidade da comunicação com o gateway, permitindo a continuidade dos ajustes de configuração.

---

## 8. Conclusão
O projeto demonstrou com sucesso a aplicação prática de conceitos fundamentais de redes de computadores, permitindo consolidar o entendimento de roteamento, segmentação via VLAN, controle de tráfego por firewall stateful e segurança perimetral com túneis criptografados em ambientes de borda corporativa.
