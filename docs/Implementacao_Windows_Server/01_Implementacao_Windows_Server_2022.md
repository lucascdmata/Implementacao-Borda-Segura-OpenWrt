# Passo a Passo da Instalação do Windows Server 2022 no VirtualBox

## Início

Entre no site da Microsoft e procure pela ISO do windows Server 2022.

Tenha o VirtualBox instalado em seu computador.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_00_ISO.png)



## Criação da Máquina Virtual

Abra o VirtualBox e clique em Novo.

Defina um Nome (ex: Windows Server 2022).

Escolha o local onde o arquivo da máquina virtual será salvo (C:\Users\...\VirtualBox...)

Em Imagem ISO, selecione o arquivo baixado (procure a ISO do Windows Server 2022)

Escolha Tipo: Microsoft Windows e Versão: Windows 2022 (64-bit).

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_01_Escolha_do_nome_e_Selecao_da_ISO.png)


Ignorar esta etapa

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_02_Ignorar_esta_etapa.png)


Defina a Memória RAM (recomenda-se pelo menos 2 GB ou 4 GB) e o número de CPUs (2 núcleos).

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_03_Selecao_da_Memoria_Ram_e_Nucleos_do_Processador.png)


Escolha Criar um novo disco rígido virtual e defina o tamanho (USEI UM DISCO DE 100 GB). Clique em finalizar.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_04_Selecao_da_Quantidade_de_Armazenamento_para_uso.png)



## Instalação do Sistema


Clique em Iniciar para ligar a máquina virtual.

Pressione qualquer tecla quando aparecer a mensagem para dar o boot pela ISO.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_05_Start_Para_Iniciar_a_VM.png)


Escolha o Idioma, o Formato de hora e o Teclado, e clique em Avançar.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_06_Comeco_da_Instalacao_Idioma_e_Teclado.png)


Clique em Instalar agora.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_07_Instalacao.png)

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_07_Instalacao_Versao_2.png)


Escolha a versão desejada: selecione Windows Server 2022 Standard (Experiência Desktop) caso queira a interface gráfica (tela normal com mouse).

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_08_Selecao_da_Versao_do_Windows_Server.png)


Aceite os termos de licença e clique em Avançar.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_09_Termos_do_Aceite.png)


Selecione Personalizada: instalar apenas o Windows (avançado).

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_10_Opcoes_Avancadas.png)


Escolha o disco virtual criado e clique em Avançar. A instalação dos arquivos vai começar.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_11_Particao_Selecao_do_Disco_para_Instalacao.png)

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_12_Instalacao_Versao_2.png)

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_12_Instalacao_Versao_3.png)

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_12_Instalacao_Versao_4.png)


O sistema vai reiniciar sozinho algumas vezes.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_13_Reinicializacao_Durante_a_Instalacao.png)



## Configurações Iniciais


Após a instalação, defina a senha para a conta de Administrador do sistema.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_14_Criacao_da_Senha_de_Administrador.png)


Para fazer o primeiro login, vá no menu superior do VirtualBox, clique em Entrada > Teclado > enviar Ctrl+Alt+Del, e digite a senha criada.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_15_Desbloqueio_de_Tela.png)

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_15_Desbloqueio_de_Tela_Versao_2_Usando_as_Configurações_da_VM_para_o_Desbloqueio.png)

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_17_Acesso_Administrador.png)


Assim que a área de trabalho carregar, crie um snapshot para segurança. Vá em Máquina, Snapshot, em seguida coloque o nome do snapshot e dê OK.

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_18_Tela_Inicial.png)

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_19_Snapshoot_para_Seguranca.png)

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_19_Snapshoot_para_Seguranca_Informar_Nome.png)

![Criação](Imagens/01_Instalacao_do_Windows_Server_2022_utilizando_VirtualBox/Passo_19_Snapshoot_Sendo_Criado.png)

