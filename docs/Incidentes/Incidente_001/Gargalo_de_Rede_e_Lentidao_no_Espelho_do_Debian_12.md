# Relatório de Incidente: Gargalo de Rede e Lentidão no Espelho NetInst do Debian 12

Data do Incidente: 11/10/2026   
Autor: Max (Suporte TI)   
Ambiente: VirtualBox (Máquina Virtual Debian 12 NetInst, Modo Bridged)   
Status: Resolvido

## 1. Resumo Executivo
   
Durante o processo de provisionamento da estação de trabalho Linux (Debian 12) destinada à integração com o Active Directory e monitorização via Zabbix, a instalação travou na fase de configuração de pacotes (tasksel). O tempo estimado de conclusão ultrapassou 1 hora e 30 minutos devido a um gargalo severo de rede no download de pacotes através do espelho oficial (deb.debian.org).

## 2. Sintomas e Evidências (Sintomatologia)


Comportamento Observado: A barra de progresso na etapa “Selecionar e instalar software” estagnou ao processar uma fila de mais de 1400 pacotes, exibindo tempos estimados absurdos (ex: 1h 33min restantes).  

Evidências Visuais (Capturas de Tela):

  - Tela de Seleção de Espelhos: Configuração padrão inicial apontando para o redirector global deb.debian.org.

  - Tela de Progresso do APT: Travamento na contagem de pacotes volumosos (ex: ambiente gráfico GNOME selecionado por padrão).
