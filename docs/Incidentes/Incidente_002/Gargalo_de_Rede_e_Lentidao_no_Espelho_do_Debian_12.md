# Incidente 002 - Gargalo de Rede e Lentidão no Espelho NetInst do Debian 12

**Autor: Lucas Cavalcante Chaves**      
Contexto do Ambiente: Homelab Corporativo Simulado (lab.do.max.local / Operador: Max - Suporte TI)

Data do Incidente: 11/10/2026    
Ambiente: VirtualBox (Máquina Virtual Debian 12 NetInst, Modo Bridged)   
Status: Resolvido

## Resumo do Ocorrido
   
Durante o provisionamento da estação de trabalho Debian 12 (debian-12.15.0-amd64-netinst.iso), a instalação estagnou na etapa de configuração de pacotes (tasksel), ultrapassando 1 hora e 30 minutos de espera devido a um gargalo severo de rede no download de mais de 1.400 pacotes do ambiente gráfico GNOME através do espelho oficial (deb.debian.org).

## Diagnóstico e Resolução

* **Diagnóstico**: A imagem NetInst descarrega grande parte do sistema operativo e da interface gráfica em tempo de execução via internet. A seleção padrão do ecossistema completo do GNOME sobrecarregou a largura de banda, provocando saturação e lentidão extrema no espelho remoto.

* **Resolução:**

 - Interrompeu-se a instalação travada de forma controlada para evitar corrupção de estado na VM.

 - Reiniciou-se o processo, desmarcando o ambiente gráfico pesado no menu do tasksel e mantendo apenas os utilitários padrão de sistema.

 - A carga de pacotes exigidos via rede caiu de ~1.400 para cerca de 200 itens essenciais, reduzindo o tempo total de instalação para menos de 5 minutos (sistema base entregue com sucesso em modo CLI).

## Lições Aprendidas

Em instalações via imagem NetInst, a seleção prévia de ambientes gráficos completos em redes de laboratório expõe o provisionamento a gargalos de espelhos externos. A prática recomendada de engenharia e resiliência é realizar o deploy inicial em modo mínimo (CLI) e aplicar as camadas de interface ou pacotes adicionais de forma iterativa após o primeiro arranque bem-sucedido.
 
### Resolvido

* **[Clique aqui para ver as imagens](Imagens_002.md)**
