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


IMG: Passo 9
Aceite os termos de licença e clique em Avançar.
![Criação]()
IMG: Passo 9

IMG: Passo 10
Selecione Personalizada: instalar apenas o Windows (avançado).
![Criação]()
IMG: Passo 10

IMG: Passo 11
Escolha o disco virtual criado e clique em Avançar. A instalação dos arquivos vai começar.
![Criação]()
IMG: Passo 11

IMG: Passo 12
O sistema vai reiniciar sozinho algumas vezes.
![Criação]()
IMG: Passo 13

## Configurações Iniciais


IMG: Passo 14
Após a instalação, defina a senha para a conta de Administrador do sistema.
![Criação]()
IMG: Passo 14

 IMG: Passo 15
• Para fazer o primeiro login, vá no menu superior do VirtualBox, clique em Entrada > Teclado > enviar Ctrl+Alt+Del, e digite a senha criada.
![Criação]()
IMG: Passo 16




IMG: Passo 18
Assim que a área de trabalho carregar, crie um snapshot para segurança. Vá em Máquina, Snapshot, em seguida coloque o nome do snapshot e dê OK.

![Criação]()
![Criação]()
![Criação]()
![Criação]()
![Criação]()
