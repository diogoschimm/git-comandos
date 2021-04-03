# Comandos do Git

Criando um repositório local, nesse momento será criado a pasta .git e uma branch local chamada master

```console
git init
```

Agora o sistema de versão de controle já irá verificar o diretório atual verificando os arquivos e pastas que colocarmos dentro dessa pasta que definimos como repositório
Por exemplo podemos adicionar um arquivo de teste chamado index.html, uma pasta js, uma pasta css alguns arquivos a mais também.

```console
touch index.html
mkdir css
mkdir js
touch css/styles.css
touch js/scripts.js
```

Agora podemos analisar o status do repositório git com o seguinte comando

```console
git status
```

Ao executarmos um git status o seguinte resultado será mostrado

```console
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        contato.html
        css/
        index.html
        js/

nothing added to commit but untracked files present (use "git add" to track)
```

Devemos adicionar os arquivos para serem vistos pelo git, para isso iremos usar o comando add.

```console
git add .
ou 
git add *
ou 
git add --all
ou
git add <nomeArquivo>
```

Ao executarmos o add o git irá incluir nossos arquivo na Stage, se quisermos voltar os arquivos para o Working Dir devemos executar o seguinte comando

```console
git rm --cached -r .
ou 
git rm --cached <nomeArquivo>
```

Após adicionar os arquivos na Stage, devemos envia-los para a HEAD, para isso vamos executar um Commit.

```console
git commit -m "Mensagem do Commit"
```

Para visualizar o histórico de commits devemos executar o seguinte comando

```console
git log
ou 
git log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short 
```

O git irá exibir da seguinte forma no caso do git log, note que o Commit recebei um hash (id)

```console
commit 1809514df775cbde3488645f884550061cfc246e (HEAD -> master)
Author: Diogo Schimmelpfennig <diogo@hotmail.com>
Date:   Fri Apr 2 23:40:15 2021 -0400

    Arquivos
```

## Alterando o Commit anterior

Para alterar o comit anterior iremos usar o parametro --amend

```console
touch hmoe.html
git add home.html
git commit --amend -m "Arquivos Novos"
```

Se executarmos o git log iremos ver que só vamos ter um commit no log

```console
git log

commit efc185c8f392c48b682608f08e690108da10b357 (HEAD -> master)
Author: Diogo Schimmelpfennig <diogo@hotmail.com>
Date:   Fri Apr 2 23:46:14 2021 -0400

    Arquivos Novos
```








