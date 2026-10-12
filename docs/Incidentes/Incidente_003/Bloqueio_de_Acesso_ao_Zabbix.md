# Incidente 003 - Bloqueio de Acesso ao Zabbix

Data do Incidente: 12/10/2026      
Autor: Max (Suporte TI)        
Ambiente: Painel Web do Zabbix        
Status: Resolvido      



## 1. Resumo do Ocorrido

Durante os testes iniciais e a validação do ambiente de laboratório, ocorreram falhas sucessivas na introdução das credenciais de acesso ao painel do Zabbix. Como mecanismo de segurança nativo para mitigar ataques de força bruta, a aplicação bloqueou o utilizador após atingir o limite estipulado de tentativas falhadas, impedindo novos logins mesmo com a palavra-passe correta.

## 2. Diagnóstico e Resolução

Para ultrapassar o bloqueio sem recorrer à reinstalação ou perda de dados, a intervenção foi realizada diretamente ao nível da base de dados relacional (MariaDB).

**Passos de Resolução Executados:**

Acesso ao console do servidor Debian:   

Acesso à linha de comandos do sistema operativo onde o Zabbix e o MariaDB se encontram alojados.

Ligação à Base de Dados do Zabbix:  

Autenticação no cliente de linha de comandos do MariaDB com privilégios administrativos:

sudo mysql -u root -p


Seleção da Base de Dados e Limpeza do Contador:
Navegação para a base de dados do Zabbix e redefinição do contador de falhas de autenticação na tabela de utilizadores (users):

USE zabbix;
UPDATE users SET attempt_failed = 0 WHERE alias = 'Admin';


**Confirmação e Validação:**
Após a execução bem-sucedida do comando de atualização, o registo de falhas foi limpo, permitindo efetuar o login imediato no painel web do Zabbix.

## 3. Lições Aprendidas

Segurança Nativa: Compreendeu-se o funcionamento do mecanismo de bloqueio por tentativas falhadas (attempt_failed) do Zabbix.

Procedimento de Emergência Documentado: Estabeleceu-se um procedimento rápido de recuperação de acesso via console de base de dados para situações semelhantes em ambiente de homelab.

