(ssh-conf)=

# Configuração do cliente SSH 

De maneira sucinta, você verá aqui como acessar o servidor: (1) por meio de um comando curto e (2) sem solicitar a senha. Vamos fazer isso passo a passo.

É importante que você observe o conteúdo do diretório `~/.ssh` vez por outra para compreender os passos abaixo. O comando {command}`ls -F1 ~/.ssh` será bastante útil. Dica para memorização do comando: *LiStar na Fórmula Um o TIO BARRA PONTO SSH*

<script id="asciicast-364458" src="https://asciinema.org/a/364458.js" async></script>

Seguem os comando que foram digitados no vídeo acima:

  657. `ls -F1 ~/.ssh`
  658. `# Primeiro acesso`
  659. `ssh fulano.tal@oulu.ifrn.edu.br`
  660. `ls -F1 ~/.ssh`
  661. `# Foi criado o arquivo de hosts conhecidos`
  662. `# Vamos gerar par de chaves (privada/pública)`
  663. `ssh-keygen`
  664. `# Pressionei a tecla Enter 3x`
  665. `ls -F1 ~/.ssh`
  666. `# Chave privada: <id_rsa>`
  667. `# Chave pública: <id_rsa.pub>`
  668. `# Vamos copiar esta chave para o servidor`
  669. `ssh-copy-id fulano.tal@oulu.ifrn.edu.br`
  670. `# Chave adicionada com sucesso`
  671. `# Agora será possível fazer o acesso sem a solicitação de senha`
  672. `# OBS.: Só faça isso em seus próprios dispositivos`
  673. `# Em máquina em que outros possam ter acesso, JAMAIS!`
  674. `ssh fulano.tal@oulu.ifrn.edu.br`
  675. `ls -F1 ~/.ssh`
  676. `# Vamos facilitar mais ainda o acesso`
  677. `# Em vez de digitar:`
  678. `#    ssh fulano.tal@oulu.ifrn.edu.br`
  679. `# Digitarei:`
  680. `#    ssh oulu`
  681. `# Como?`
  682. `# Crie o arquivo ~/.ssh/config`
  683. `# Siga o exemplo`
  684. `nano ~/.ssh/config`
  685. `cat -n ~/.ssh/config`
  686. `# Explicações`
  687. `# 1: Apelido`
  688. `# 2: Nome da máquina`
  689. `# 3: Nome do usuário`
  690. `ssh oulu`


## Acesso sem senha

Veja o conteúdo do diretório `~/.ssh`. Caso exista os arquivos {file}`id_rsa` e {file}`id_rsa.pub`, siga para o passo de número X.

1. Crie um para de chaves (privada/pública) caso não as tenha. Execute o comando:

    * `ssh-keygen`


## Acesso por meio de um comando curto

A ideia é criar um arquivo de configuração para o cliente SSH em seu dispositivo. Neste arquivo, terá os seguintes dados:

1. Apelido para servidor (Ex.: `oulu`)
2. Nome do servidor: (Ex.: `oulu.ifrn.edu.br`) 
3. Nome de seu usuário: (Ex.: `fulano.tal`)

echo -n "Seu usuário na Oulu: "
read usuario
mkdir -p ~/.ssh/

cat <<FIM >> ~/.ssh/config
Host oulu
    hostname oulu.ifrn.edu.br
    user ${usuario}
FIM