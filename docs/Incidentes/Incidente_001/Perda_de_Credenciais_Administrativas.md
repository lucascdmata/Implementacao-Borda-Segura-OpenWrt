# Incidente 001 - Perda de Credenciais Administrativas

Data: 03/Outubro/2026

 
### Problema

Eu esqueci a senha administrativa do roteador.

Após avaliar os arquivos de configuração, constatei que durante a implementação do ambiente OpenWrt, a senha administrativa do roteador não foi documentada adequadamente, impossibilitando o acesso via interface LuCI / SSH.

 
### Impacto

Interrupção temporária das atividades de configuração do projeto.


### Sintomas Observados

A interface administrativa permanecia acessível pelo endereço: 10.0.x.x/cgi-bin/luci
Entretanto, as tentativas de autenticação resultavam em falha.

 
### Diagnóstico

As verificações realizadas indicaram que:

- A conectividade LAN estava funcional.
- O serviço SSH (Dropbear) estava ativo.
- O OpenWrt estava carregando normalmente.
- O usuário root existia.
- Não havia indícios de corrupção do sistema.

Concluiu-se que o incidente estava restrito à perda da credencial administrativa.

 
### Tentativas Iniciais

- Verificação de Senhas Salvas

Foram verificadas:

- Senhas armazenadas no navegador.
- Credenciais utilizadas em outros serviços.
- Arquivo de backup do OpenWrt (.tar.gz).

Nenhuma credencial válida foi encontrada.


### Estratégia de Recuperação

Utilizar o modo de recuperação FailSafe do OpenWrt para redefinição da senha sem realizar reset de fábrica.

Objetivos:

- Preservar toda a configuração existente.
- Evitar reinstalação.
- Evitar perda do laboratório em desenvolvimento.


### Entrada em FailSafe Mode

Notebook conectado diretamente à porta LAN do roteador.

Procedimento:

- Desligamento do roteador.
- Religamento do equipamento.
- Acionamento do botão RESET durante o processo de boot.
- Verificação visual através do LED de energia piscando.

Após o procedimento, o roteador deixou de responder no endereço original e passou a responder pelo IP: 192.168.x.x


### Ajuste de Rede para Recuperação

Foi configurado endereço IP estático no notebook:

- IP: 192.168.x.x
- Máscara: 255.255.255.0
- Gateway: 192.168.x.x


### Acesso ao OpenWrt em FailSafe

Foi iniciado acesso SSH utilizando o PowerShell: ssh root@ 192.168.x.x

O sistema apresentou: ================= FAILSAFE MODE active ================

Confirmando que o OpenWrt havia iniciado em modo de recuperação.


### Montagem da Configuração

Foi executado: mount_root

Resultado: switching to jffs2 overlay

Esta etapa permitiu acesso às configurações persistentes armazenadas no overlay do sistema.


### Redefinição da Senha
Com a configuração montada, foi executado: 

passwd

O sistema solicitou:

New password e Retype password

Após confirmação: 

password for root changed by root

A nova senha administrativa foi gravada com sucesso.


### Reinicialização
Após a redefinição da credencial foi executado: reboot (para reiniciar o roteador)


### Resultado
✅ Acesso administrativo recuperado.

✅ Configurações preservadas.

✅ Sem necessidade de reset de fábrica.

✅ Sem necessidade de reinstalar OpenWrt.

✅ Projeto permaneceu íntegro.

✅ SSH validado como método de administração do ambiente.


### Lições Aprendidas

- Implementar política de gerenciamento de credenciais.
- Manter documentação atualizada das senhas administrativas.
- Configurar acesso SSH logo após a implantação inicial.
- Validar periodicamente os procedimentos de recuperação.

### Resolvido

* **![Clique aqui para ver as imagens](docs/Incidentes/Incidente 001/INC_001_Imagens)**
