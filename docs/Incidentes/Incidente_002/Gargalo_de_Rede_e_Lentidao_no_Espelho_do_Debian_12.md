# Incidente 002 - Gargalo de Rede e Lentidão no Espelho NetInst do Debian 12

Data do Incidente: 11/10/2026   
Autor: Max (Suporte TI)   
Ambiente: VirtualBox (Máquina Virtual Debian 12 NetInst, Modo Bridged)   
Status: Resolvido

## 1. Resumo
   
Durante o processo de provisionamento da estação de trabalho Linux (Debian 12) destinada à integração com o Active Directory e monitorização via Zabbix, a instalação travou na fase de configuração de pacotes (tasksel). O tempo estimado de conclusão ultrapassou 1 hora e 30 minutos devido a um gargalo severo de rede no download de pacotes através do espelho oficial (deb.debian.org).

## 2. Sintomas e Evidências

 - **Comportamento Observado**: A barra de progresso na etapa “Selecionar e instalar software” estagnou ao processar uma fila de mais de 1400 pacotes, exibindo tempos estimados absurdos (ex: 1h 33min restantes).  

 - **Evidências Visuais** (Capturas de Tela):

  - **Tela de Seleção de Espelhos**: Configuração padrão inicial apontando para o redirector global deb.debian.org.

  - **Tela de Progresso do APT**: Travamento na contagem de pacotes volumosos (ex: ambiente gráfico GNOME selecionado por padrão).

## 3. Análise de Causa Raiz

Natureza da Imagem NetInst: A ISO utilizada (debian-12.15.0-amd64-netinst.iso) descarrega quase a totalidade do sistema operacional e da interface gráfica diretamente da internet durante o processo de instalação.

Saturação do Espelho: A escolha do espelho padrão (deb.debian.org) resultou em rotas lentas ou congestionamento de banda no momento da requisição dos pacotes do ambiente gráfico.

Escopo Excessivo na Instalação Base: A seleção prévia do ecossistema completo do GNOME forçou o download de mais de 1.400 pacotes individuais em uma única fase síncrona.

## 4. Ação Corretiva e Resolução (Troubleshooting)

Para contornar o bloqueio operacional e otimizar o tempo de entrega do laboratório, foram adotadas as seguintes medidas:

 - **Interromper Instalação**: Interrupção controlada da instalação travada para evitar corrupção de estado na VM.

 - **Ajuste de Escopo (Instalação Mínima**): Na nova tentativa de instalação, optou-se por desmarcar o ambiente de área de trabalho pesado na ferramenta tasksel, mantendo apenas os utilitários de sistema padrão.

 - **Redução de Carga**: A quantidade de pacotes exigidos via rede despencou de ~1400 para cerca de 200 pacotes essenciais, reduzindo o tempo de instalação para menos de 5 minutos.

 - **Pós-Instalação Planejada**: O sistema base foi entregue com sucesso em modo CLI (terminal), permitindo a instalação posterior da interface gráfica de forma controlada.

## 5. Lições Aprendidas

Em ambientes de laboratório ou provisionamentos rápidos, o uso de imagens NetInst com ambientes gráficos completos pode gerar dependência crítica de instabilidades na rede externa.

A melhor prática para ambientes enxutos é provisionar o servidor/estação em modo mínimo (CLI) e aplicar as camadas de interface ou pacotes adicionais iterativamente após o primeiro boot bem-sucedido.

### Resolvido

* **[Clique aqui para ver as imagens](Imagens_002.md)**
