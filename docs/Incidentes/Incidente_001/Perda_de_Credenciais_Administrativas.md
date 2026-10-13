# Incidente 001 - Perda de Credenciais Administrativas

**Autor: Lucas Cavalcante Chaves**    
Contexto do Ambiente: Homelab Corporativo Simulado (lab.do.max.local / Operador: Max - Suporte TI)

Data do Incidente: 03/10/2026   
Ambiente: OpenWrt (Roteador Cudy WR3000 v1.0)   
Status: Resolvido

 
## Resumo do Ocorrido
Durante a implementação do ambiente OpenWrt no roteador Cudy WR3000 v1.0, ocorreu a perda da senha administrativa, impossibilitando o acesso via interface web (LuCI) e SSH. O impacto resultou na interrupção temporária das atividades de configuração do laboratório, visto que a interface web respondia, mas recusava as tentativas de autenticação.

## 2. Diagnóstico e Resolução
* **Diagnóstico:** Verificou-se que a conectividade LAN estava funcional, o serviço SSH ativo e o sistema operacional íntegro, confirmando que o problema estava restrito exclusivamente à credencial de acesso. Tentativas iniciais com senhas salvas no navegador, credenciais de outros serviços e ficheiros de backup prévios (.tar.gz) não tiveram sucesso.

* **Resolução:**

Utilizou-se o modo de recuperação FailSafe do OpenWrt para redefinir a palavra-passe sem recorrer ao reset de fábrica, preservando todas as configurações do laboratório.

O equipamento foi reiniciado com o acionamento físico do botão RESET durante o boot, alterando o acesso para o IP de recuperação padrão.

Configurou-se um endereço IP estático no computador e estabeleceu-se uma sessão SSH direta com o roteador em modo FailSafe.

Executou-se o comando mount_root para montar a partição persistente (overlay JFFS2) e o comando passwd para redefinir a senha do utilizador root.

O equipamento foi reiniciado com o comando reboot, restabelecendo com sucesso o acesso administrativo e mantendo o projeto totalmente íntegro.

## 3. Lições Aprendidas
Implementar uma política rigorosa de gerenciamento e documentação atualizada de credenciais administrativas.

Configurar e validar o acesso SSH logo após a implantação inicial de novos dispositivos de rede.

Testar periodicamente os procedimentos de recuperação de desastres (como o modo FailSafe) para garantir maior agilidade e resiliência em ambientes de laboratório.

### Resolvido

* **[Clique aqui para ver as imagens](Imagens_001.md)**
