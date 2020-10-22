(ssh-cliente)=

# Clientes SSH

Para acessar a máquina Oulu via SSH você precisará de um cliente SSH. Nesta documentação, é dada preferência ao cliente OpenSSH via linha de comando.

Escolha seu sistema operacional:
* [Android](#android)
* [iPad/iPhone](#ipad-iphone)
* [Linux](#linux)
* [macOS](#macos)
* [Windows](#windows)


## Android

Para ter um terminal em seu dispositivo Android, instale o app 
[Termux](https://play.google.com/store/apps/details?id=com.termux&hl=pt_BR). Uma vez aberto o programa, instale o pacote `openssh` executando o comando:

* `pkg install openssh`

Adicionar mais teclas a seu teclado do Termux, com as teclas <kbd>Esc</kbd>, <kbd>PgUp</kbd> e <kbd>PgDown</kbd>, siga os passos do seguinte vídeo, gentilmente compartilhado por [Rodrigo Rodrigues](https://mange.ifrn.edu.br/site/redes20191par/manual-asa//equipe/rodrigo.html).

<iframe width="560" height="315" src="https://www.youtube.com/embed/rFsMcuc6omg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## iPad/iPhone

No iPhone ou iPad, sugere-se a instalação do app [Termius - SSH client](https://apps.apple.com/br/app/termius-ssh-client/id549039908). Não serão oferecidas instruções específica para esta app por ela não oferecer o cliente SSH via linha de comando.

## Linux

Em distribuições Linux para Desktop, é comum vir com o pacote *openssh-client* instalado. A única coisa que você precisa fazer é abrir um terminal. Na distruição Ubuntu e derivadas, você pode fazer isso com a tecla de atalho: `Control`+`Alt`+`t`.

## macOS

[De acordo com essa página](https://www.ssh.com/ssh/putty/mac/), o macOS vem com um cliente SSH de linha de comando como parte do sistema operacional. 

## Windows

A maneira mais simples de ter um cliente SSH para Windows é instalar o programa [Git for Windows](https://git-scm.com/download/win), que disponibiliza vários comandos típicos do Linux na aplicação de terminal chamada de *Git Bash*.
