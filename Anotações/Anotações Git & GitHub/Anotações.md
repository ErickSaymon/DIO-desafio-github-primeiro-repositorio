# Anotações que fiz sobre Git e GitHub 
### O que é GIT?

- O editor mais exigente possível é o compilador de código. Qualquer erro, o editor acusa a falha, pedindo uma nova versão.

O GIT foi criado para ser um sistema de versionamento distribuído. Seu criador é o mesmo criador do Linux. Como o Linux foi criado colaborativamente, e o Linus não estava contente com os sistemas de versionamento de códigos da época, assim surgiu o GIT.

> “O software não é feito sozinho, mas sim, de forma colaborativa.”
> 

---

***GIT E GITHUB NÃO SÃO AS MESMAS COISAS.***

### Comandos básicos do GIT

O GIT não possui interface gráfica, funciona apenas por linhas de comando.

- Principais comandos para o CMD:
    - -CD: Comando para acessar determinados diretórios.
    - -DIR: Mostra os diretórios dentro dos diretórios que estamos.
    - -CLS: Limpar o terminal.
    - -MKDIR: Criar diretórios.
    - -RMDIR: Deletar diretórios (Utilizar flags /S /Q para deletar tudo).
    - -DEL: Deletar arquivos dentro de um diretório.
    - *DICA: TAB auto completa os nomes.*

---

- **SHA significa Secure Hash Algorithm** que gera 40 dígitos únicos. O GIT utiliza essa forma de encriptação pois é uma ótima encriptação.

### Tipos básicos de objetos do GIT

Como num sistema operacional, pastas podem conter ou subpastas, ou arquivos. O GIT utiliza uma estrutura parecida, onde o *Blob* seria o arquivo, e a *Tree* seriam as pastas.


- Blobs
    - O objeto blob guarda os arquivos, e contem metadata, guardando o tipo do arquivo, o tamanho, “\0”, e por fim o conteúdo do arquivo.
- Trees
    - As trees armazenam os blobs, o nome do arquivo e o tamanho do arquivo. Ela é responsável por montar a estrutura de onde ficam os arquivos. Elas podem guardar blobs, ou outras trees. Ela também possui um SHA, onde qualquer mudança dentro de um blob, o SHA deste mudará, e daquele também.
- Commit
    - Este objeto é o mais importante de todos. Ele junta todos os outros objetos. Este aponta para uma árvore, para um commit anterior, para o autor, para uma mensagem, e tem seu timestamp, ou seja, armazena o horário em que foi criado. Também possuem SHA1, que é o hash de toda informação acima.
    
    ---
    
    O GIT é um sistema distribuído e seguro. 
    
    Ao mandar o código para o GITHUB, você deverá se autenticar.
    
    - CHAVE SSH
        - É uma forma de estabelecer uma conexão segura entre duas máquinas, utilizando chaves públicas e chaves privadas.
        - Para criar uma chave SSH, devemos ir no terminal e digitar  o comando:
        
        ```powershell
        ssh-keygen -t ed 25519 -C (email)
        ```
        
        - Feito isso, a chave será criada em um determinado diretório. Devemos acessar esse diretório, abrir o arquivo com a chave pública, e coloca-la no GitHub.
        - Para a chave privada, utilizaremos dois comandos:
        
        ```powershell
        eval $(ssh-agent -s)
        ```
        
        ```powershell
        ssh-add (arquivo com a chave privada)
        ```
        
        - Ao clonar um repositório no GitHub, devemos usar o caminho SSH.
    - Token
        - Para utilizar um token, devemos cria-lo no GitHub. Utilizando o token para copiar um repositório, devemos pegar o caminho HTTPS e utilizar o comando para clonagem. O Git requisitará uma senha, que será o token de acesso criado. Lembrando que o token tem um tempo limite de uso.

---

### Primeiros passos com Git

*Markdown = Formas humanizadas de escrever um HTML.*

Ao utilizar os comandos do Git, sempre deveremos utilizar o prefixo git.

- Comandos úteis:

```powershell
git init
git add
git status
git commit
git remote add origin
git push origin master
git pull origin master
git clone
```

Untracked:  Arquivos nao rastreados pelo git.

Tracked: Arquivos rastreados pelo Git.

Os Unmodified são aqueles que nao foram modificados. 

Os modifieds são aqueles que já sofreram modificaçoes.

O arquivo que passa para o Staged está preparado para ir para o objeto Commit. Ao utilizar o Commit, todos os arquivos voltam para o estado de Unmodified.

---

### Repositórios

O Repositório Remoto está salvo num servidor. No ambiente de desenvolvimento, temos o repositório de trabalho. Ao modificar arquivos no repositório local, as modificações nao são passadas para o repositório remoto, a nao ser que as modificações sejam salvas lá.

Ao fazer um commit, os arquivos passarão para o repositório local. Os arquivos sairão da staging area e irão para uma commit.

---

### Resolvendo conflitos

Ao tentar mandar um código para o GitHub, aonde tenha uma atualização mais recente que a reposição em seu ambiente de trabalho, o Git retornará um erro. Para resolve-lo, devemos puxar o arquivo do GitHub com o comando “git pull origin master”, verificar os conflitos, corrigir os conflitos e entao enviar o arquivo novamente para o GitHub.