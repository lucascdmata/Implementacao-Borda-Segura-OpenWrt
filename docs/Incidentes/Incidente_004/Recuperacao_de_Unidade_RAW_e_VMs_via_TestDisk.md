# Incidente 004 - Recuperação de Unidade RAW e VMs via TestDisk

**Autor: Lucas Cavalcante Chaves**      
Contexto do Ambiente: Homelab Corporativo Simulado (lab.do.max.local / Operador: Max - Suporte TI)

Data do Incidente: 12/10/2026    
Ambiente: Painel Web do Zabbix    
Status: Resolvido    


## Resumo do Ocorrido
Durante as atividades no homelab, o SSD secundário sofreu uma falha lógica repentina e o sistema operacional passou a reportar a unidade em formato RAW, impedindo o acesso aos ficheiros das máquinas virtuais (VERR_PATH_NOT_FOUND no VirtualBox). O incidente gerou risco iminente de perda total dos dados e do progresso do laboratório.

## Diagnóstico e Resolução
**Diagnóstico:**

O Explorador de Ficheiros bloqueou o acesso à unidade e o Gerenciamento de Discos confirmou que a partição estava em formato RAW com 100% de espaço livre aparente.

Após reatribuir a letra da unidade (de D: para L:), executou-se o comando CHKDSK L:, que detetou segmentos corrompidos e ficheiros órfãos, mas interrompeu a análise por não conseguir reparar a estrutura em modo de leitura.

**Resolução:**

Varredura com TestDisk: Utilizou-se o utilitário TestDisk selecionando o disco físico afetado e executando a análise (Analyse e Quick Search) para mapear e recuperar a tabela de partições NTFS perdida.

Resgate dos Dados: Através da listagem de ficheiros da ferramenta, navegaram-se pelas pastas das máquinas virtuais (VM_Linux e VM_Windows_Server2022) e realizou-se a cópia direta de todo o conteúdo para um disco de destino seguro (K:).

Validação Final: Confirmou-se a integridade da estrutura de pastas recuperadas na unidade K: (incluindo ficheiros de configuração .vbox, discos virtuais e a pasta Snapshots), restabelecendo o funcionamento completo das máquinas no VirtualBox.

## Lições Aprendidas
Implementar rotinas frequentes de cópia de segurança (backup) externas para mitigar o impacto de corrupções lógicas súbitas em unidades de armazenamento.

Ferramentas de recuperação de baixo nível e reestruturação de partições (como o TestDisk) são recursos indispensáveis no kit de ferramentas de um administrador de sistemas para reversão de desastres de armazenamento.

Validar a integridade e o arranque dos ambientes virtualizados imediatamente após concluir processos de salvamento de dados.

### Resolvido

* **[Clique aqui para ver as imagens](Incidente_004_Imagens.md)**
