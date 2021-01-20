(ssh-conf)=

# Configuração do cliente SSH 

Você pode ver nesta página: 
- [Como acessar, via SSH e sem senha, o servidor Oulu](#acesso-sem-senha) e
- {ref}`Como acessar, via SSH e por meio de um comando curto, o servidor Oulu <ssh-conf-acesso-curto>`
- {ref}`Vídeo de demonstração das configurações anteriores <ssh-conf-video-demo>`

```{warning}
Para seguir os passos desta página, presume-se que você já tenha:
1. {ref}`Um cliente SSH <ssh-cliente>`;
2. {ref}`Uma conta na máquina Oulu <ssh-conta>`.
```

## Acesso sem senha

O acesso sem senha ao servidor Oulu depende da existência de par(es) de chaves privada/pública que se encontra(m) no diretório `~/.ssh`, isto é, o diretório `.ssh` que se encontra na pasta base (`echo $HOME`) de seu usuário. No caso do [algoritmo RSA](https://pt.wikipedia.org/wiki/RSA_(sistema_criptogr%C3%A1fico)), este par de chaves é representado pelos arquivos {file}`id_rsa` e {file}`id_rsa.pub`. Caso não haja esses arquivos para seu usuário, você poderá gerá-los por meio do comando: `ssh-keygen`

```{warning}
Só faça isso em seus próprios dispositivos (PC, notebook, celular ou tablet). Em máquina em que outros possam ter acesso, JAMAIS!
```

1. Vamos gerar par de chaves (privada/pública). Execute:
   - `ssh-keygen`

2. Pressionei três vezes (3x) a tecla {kbd}`Enter`. Serão apresentadas mensagens em Inglês. Caso não as compreenda, experimente usar o [Google Tradutor](https://translate.google.com) para traduzi-las.
    
3. Veja o conteúdo do diretório `.ssh` de seu usuário:
   - `ls -F1 ~/.ssh`

4. Breve explicação sobre os arquivos que podem aparecer:

   |Função do arquivo | Nome do arquivo |
   | --- | --- | 
   |Chaves autorizadas | `authorized_keys` |
   |Arquivo de configuração | `config`
   |Chave privada do tipo RSA | `id_rsa` |
   |Chave pública do tipo RSA | `id_rsa.pub` |
   |Hospedeiros conhecidos | `known_hosts` |

5. Vamos copiar a chave pública para o servidor. Substitua `fulano.tal` pelo nome de seu usuário na Oulu. Execute:
   - `ssh-copy-id fulano.tal@oulu.ifrn.edu.br`

6. Se sua chave pública tiver sido adicionada com sucesso, você receberá uma mensagem informando que isso aconteceu. Caso não compreenda as mensagens em Inglês que forem exibidas, lembre-se de traduzi-las no [Google Tradutor](https://translate.google.com). Na pasta de seu usuário da Oulu, deverá aparecer o arquivo de chaves autorizadas. Se você executar o mesmo comando do passo 3 **na máquina Oulu**, perceberá que foi criado o arquivo de chaves autorizadas (`~/.ssh/authorized_keys`). Execute:
  - `ssh fulano.tal@oulu.ifrn.edu.br ls -F1 ~/.ssh`
   
A partir de agora você poderá acessar a máquina Oulu por meio de seu par de chaves pública/privada do SSH e sem a solicitação de senha (Foi por esta razão que você pressionou a tecla {kbd}`Enter` três vezes no passo 1). Experimente!

(ssh-conf-acesso-curto)=

## Acesso por meio de um comando curto

A ideia é criar um arquivo de configuração para o cliente SSH em seu dispositivo. Neste arquivo, haverá os seguintes dados:

1. Apelido para servidor (Ex.: `oulu`)
2. Nome do servidor: (Ex.: `oulu.ifrn.edu.br`) 
3. Nome de seu usuário: (Ex.: `fulano.tal`)

```{warning}
Certifique-se de estar em seu dispositivo e não na máquina Oulu. Experimente executar os comandos:
- `hostname`
- `whoami`

A saída dos comandos anteriores deve ser, respectivamente, o nome de seu dispositivo (`hostname`, nome do hospedeiro, em Inglês) e o nome de seu usuário (`whoami`, quem sou eu, em Inglês) em seu dispositivo. Caso a saída seja `oulu` e o nome de seu usuário na Oulu, execute o comando `exit`. Na dúvida, é melhor executar os passos seguintes em um novo terminal.  
```

O roteiro básico é:

1. Criar o diretório `.ssh` na área de seu usuário.
   - `mkdir -p ~/.ssh/`

2. Editar o arquivo `~/.ssh/config`: 
   - `nano ~/.ssh/config`

3. Inserir o conteúdo:   

   ```
   Host oulu
     Hostname oulu.ifrn.edu.br
     User fulano.tal
   ```

   PS: Troque *fulano.tal* pelo nome de seu usuário na Oulu.

4. Salvar o arquivo. Pressionar as teclas:
   1. {kbd}`Ctrl+o`
   2. {kbd}`Enter`

5. Sair do `nano`. Pressionar:
   - `Ctrl+x`.

Pronto. Agora você pode acessar a máquina Oulu via SSH digitando simplesmente:
- `ssh oulu`

(ssh-conf-video-demo)=

## Vídeo de demonstração

<script id="asciicast-364458" src="https://asciinema.org/a/364458.js" async></script>

