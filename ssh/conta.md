(ssh-conta)=

# Conta para acesso via SSH

O acesso à máquina Oulu via {abbr}`SSH (Secure SHell)` depende da criação de uma conta, processo este que é feito por meio de uma conexão *ssh* realizada com usuário e senha específicos, que, por questão de segurança, será repassado em um primeiro momento por um(a) professor(a), e posteriormente por meio de um aplicativo. Vamos aos passos:

1. {ref}`Abra um terminal <ssh-cliente>`
2. Execute o seguinte comando, substituindo `USUARIO` pelo nome de usuário fornecido pelo(a) professor(a):
    * `ssh USUARIO@oulu.ifrn.edu.br`
    
3. Se for seu primeiro acesso, você poderá receber o seguinte aviso: 
    ```{literalinclude} teste-autenticidade-servidor.txt
    ```
    Digite `yes` para aceitar a chave pública do servidor. Esta chave será acrescentada ao arquivo de {ref}`known_hosts`.

4. Entre com a senha fornecida por seu professor(a) e pressione :

    ```
    USUARIO@oulu.ifrn.edu.br's password: 
    ```

    Não será exibido nenhum caractere enquanto você digita.

5. Verifique se você realmente conseguiu se conectar.

    ```
    USUARIO@oulu:~$
    ```

    Seu prompt, isto é, o aviso que o sistema apresenta para informar que está pronto para receber comandos, tem o formato `USUARIO`@`oulu:$ `.

6. Digite o seguinte comando:

    * `sudo cria-meu-usuario`

7. Informe:

    1. Senha do usuário que acessou
    2. Sua matrícula
    3. Senha do SUAP

    Observe as linhas 1, 2 e 3 do próximo passo.

8. Se você tiver informado os dados corretos no passo anterior, você receberá uma mensagem parecida com a seguinte:

    ```{literalinclude} cria-meu-usuario.txt
    :linenos:
    :emphasize-lines: 1-3
    ```

9. Siga as instruções fornecidas no passo anterior, a saber:

    Os passos seguintes são genéricos. Substitua *fulano.tal* pelo nome de seu usuário na Oulu, que segue o formato *nome.sobrenome* ou *sobrenome.nome*. Copie e cole a senha que é exibida no passo de número 3 das instruções que você recebeu, pois você precisará dela duas vezes (2x).

    1. Encerre esta sessão da conta estudante (tecla de atalho {kbd}`CTRL+D` ou comando {command}`exit`);
    2. Inicie uma sessão com seu usuário:

        `ssh nome.sobrenome@oulu.ifrn.edu.br`

    3. Quando solicitada, ofereça a senha: `SENHA-FÁCIL!`
    4. Será solicitada a troca desta senha:
        1. Digite a senha atual: `SENHA-FÁCIL!`
        2. Digite a nova senha
        3. Repita a nova senha
    5. Sua sessão foi automaticamente encerrada após a troca da senha.

    PS: Eventualmente você terá sua sessão na Oulu encerrada após determinado 
    tempo de ociosidade. Para evitar isso, recomendamos o uso de algum 
    gerente de terminais, como o byobu. Para ativá-lo, execute:

        * `byobu-enable`

    Na próxima sessão remota, ele será executado automaticamente para seu usuário.
    Para dicas de como utilizá-lo, veja: <https://mange.ifrn.edu.br/byobu>

10. Pronto, agora você já tem um usuário na Oulu. O que você pode fazer para facilitar seu acesso à este servidor:
    1. 
    2. 