## Diário de Incidentes
 
### Incidente 001 - Perda de Credenciais Administrativas

Data: 03/Outubro/2026
 
#### Problema
Eu esqueci a senha administrativa do roteador.
Após avaliar os arquivos de configuração, constatei que durante a implementação do ambiente OpenWrt, a senha administrativa do roteador não foi documentada adequadamente, impossibilitando o acesso via interface LuCI / SSH.
 
#### Impacto
Interrupção temporária das atividades de configuração do projeto.
 
#### Diagnóstico
- Interface web acessível.
- Conectividade LAN funcional.
- Serviço SSH ativo.
- Falha restrita à autenticação do usuário root.
 
#### Ações Realizadas
- Verificação de senhas armazenadas no navegador.
- Inspeção do arquivo de backup (.tar.gz).
- Validação do acesso via SSH.
- Levantamento de procedimentos de recuperação utilizando FailSafe Mode.
 
#### Lições Aprendidas
- Implementar política de gerenciamento de credenciais.
- Manter documentação atualizada das senhas administrativas.
- Configurar acesso SSH logo após a implantação inicial.
- Validar periodicamente os procedimentos de recuperação.
 
Status: Em tratamento.
