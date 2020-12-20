(ssh-conf)=

# Configuração do cliente SSH 

De maneira sucinta, você verá aqui como acessar o servidor: (1) por meio de um comando curto e (2) sem solicitar a senha. Vamos fazer isso passo a passo.

É importante que você observe o conteúdo do diretório `~/.ssh` vez por outra para compreender os passos abaixo. O comando {command}`ls -F1 ~/.ssh` será utilizado para fazer isso.

<script id="asciicast-364458" src="https://asciinema.org/a/364458.js" async></script>

Seguem os comando que foram digitados no vídeo acima:

1. `# Vamos gerar par de chaves (privada/pública)`
2. `ssh-keygen`
3. `# Pressionei a tecla Enter 3x`
4. `ls -F1 ~/.ssh`
5. `# Chave privada: <id_rsa>`
6. `# Chave pública: <id_rsa.pub>`
7. `# Vamos copiar a chave pública para o servidor`
8. `ssh-copy-id fulano.tal@oulu.ifrn.edu.br`
9. `# Chave adicionada com sucesso`
10. `# Agora será possível fazer o acesso sem a solicitação de senha`
11. `# OBS.: Só faça isso em seus próprios dispositivos`
12. `# Em máquina em que outros possam ter acesso, JAMAIS!`
13. `ssh fulano.tal@oulu.ifrn.edu.br`
14. `ls -F1 ~/.ssh`
15. `# Vamos facilitar mais ainda o acesso`
16. `# Em vez de digitar:`
17. `#    ssh fulano.tal@oulu.ifrn.edu.br`
18. `# Digitarei:`
19. `#    ssh oulu`
20. `# Como?`
21. `# Crie o arquivo ~/.ssh/config`
22. `# Siga o exemplo`
23. `nano ~/.ssh/config`
24. `cat -n ~/.ssh/config`
25. `# Explicações`
26. `# 1: Apelido`
27. `# 2: Nome da máquina`
28. `# 3: Nome do usuário`
29. `ssh oulu`


Segue um resumo do que foi feito.

## Acesso sem senha

O acesso sem senha depende da existência de par(es) de chaves privada/pública que se encontra(m) no diretório `~/.ssh`, isto é, o diretório `.ssh` que se encontra na pasta base (`echo $HOME`) de seu usuário. No caso do [algoritmo RSA](https://pt.wikipedia.org/wiki/RSA_(sistema_criptogr%C3%A1fico)), este par de chaves é representado pelos arquivos {file}`id_rsa` e {file}`id_rsa.pub`. Caso não haja esses arquivos para seu usuário, você poderá gerá-los por meio do comando: `ssh-keygen`


## Acesso por meio de um comando curto

A ideia é criar um arquivo de configuração para o cliente SSH em seu dispositivo. Neste arquivo, haverá os seguintes dados:

1. Apelido para servidor (Ex.: `oulu`)
2. Nome do servidor: (Ex.: `oulu.ifrn.edu.br`) 
3. Nome de seu usuário: (Ex.: `fulano.tal`)

O roteiro básico seria:

1. Criar o diretório `.ssh` na área de seu usuário: `mkdir -p ~/.ssh/`
2. Editar o arquivo `~/.ssh/config`: `nano ~/.ssh/config`
3. Inserir o conteúdo:   

   ```
   Host oulu
     hostname oulu.ifrn.edu.br
     user fulano.tal
   ```

   PS: Troque <*fulano.tal*> pelo nome de seu usuário na Oulu.

4. Salvar o arquivo: Pressionar as teclas {kbd}`Ctrl+o` e posteriormente {kbd}`Enter`
5. Sair do nano: Pressionar as teclas {kbd}`Ctrl+x`.


Pronto. Agora você pode acessar a máquina Oulu via SSH digitando simplesmente: `ssh oulu`