(ssh-conf)=

# Configuração do cliente SSH 

De maneira sucinta, você verá aqui como acessar o servidor: (1) por meio de um comando curto e (2) sem solicitar a senha. Vamos fazer isso passo a passo.

É importante que você observe o conteúdo do diretório `~/.ssh` vez por outra para compreender os passos abaixo. O comando {command}`ls -F1 ~/.ssh` será bastante útil.

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


## Acesso sem senha

Veja o conteúdo do diretório `~/.ssh`. Caso exista os arquivos {file}`id_rsa` e {file}`id_rsa.pub`, siga para o passo de número X.

1. Crie um para de chaves (privada/pública) caso não as tenha. Execute o comando:

    * `ssh-keygen`


## Acesso por meio de um comando curto

A ideia é criar um arquivo de configuração para o cliente SSH em seu dispositivo. Neste arquivo, terá os seguintes dados:

1. Apelido para servidor (Ex.: `oulu`)
2. Nome do servidor: (Ex.: `oulu.ifrn.edu.br`) 
3. Nome de seu usuário: (Ex.: `fulano.tal`)

```sh
echo -n "Seu usuário na Oulu: "
read usuario
mkdir -p ~/.ssh/

cat <<FIM >> ~/.ssh/config
Host oulu
    hostname oulu.ifrn.edu.br
    user ${usuario}
FIM
```