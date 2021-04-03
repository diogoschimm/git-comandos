# Comandos do Git

Sistema de controle de versões do git 

## Criando um repositório git local

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

## Visualizando o status do repositório local

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

## Adicionando na Stage

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

## Removendo da Stage

Ao executarmos o add o git irá incluir nossos arquivo na Stage, se quisermos voltar os arquivos para o Working Dir devemos executar o seguinte comando

```console
git rm --cached -r .
ou 
git rm --cached <nomeArquivo>
```

## Comitando Alteração para o repositório

Após adicionar os arquivos na Stage, devemos envia-los para a HEAD, para isso vamos executar um Commit.

```console
git commit -m "Mensagem do Commit"
```

## Visualizando Logs de Commit

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

## Revertendo Commits

Vamos adicionar um novo arquivo chamado contato.html e fazer o commit dele, logo após vamos reverter esse commit.

```console
touch contato.html
git add .
git commit -m "Criação do arquivo contato.html"
```

Agora ao analisar o log teremos

```console
git log 

commit 6c85191d88c8aaa26081bbcd659f784f9ca42f8e (HEAD -> master)
Author: Diogo Schimmelpfennig <diogo@hotmail.com>
Date:   Sat Apr 3 00:02:21 2021 -0400

    Criação da página de contato

commit efc185c8f392c48b682608f08e690108da10b357
Author: Diogo Schimmelpfennig <diogo@hotmail.com>
Date:   Fri Apr 2 23:46:14 2021 -0400

    Arquivos Novos
```

Podemos analizar os dois commits com o comnado git log, sendo eles respectivamente os hashs 
1º:  efc185c8f392c48b682608f08e690108da10b357
Último: 6c85191d88c8aaa26081bbcd659f784f9ca42f8e

Agora queremos voltar para o primeiro commit, para isso teremos duas possibilidades:
1º possibilidade:
Excluir o commit "Criação da página de contato" e manter somente o commit "Arquivos Novos"

Para isso vamos usar o comando git reset
```console
git reset --soft 6c85191d88c8aaa26081bbcd659f784f9ca42f8e
ou
git reset --mixed 6c85191d88c8aaa26081bbcd659f784f9ca42f8e
ou
git reset --hard 6c85191d88c8aaa26081bbcd659f784f9ca42f8e
ou
git reset 6c85191d88c8aaa26081bbcd659f784f9ca42f8e 
```

2º possibilidade:
Manter o commit "Criação da página de contato" e criar um novo commit revertendo o que está no commit 6c85191d88c8aaa26081bbcd659f784f9ca42f8e

Para isso vamos usar o comando git revert

```console
git revert HEAD --no-edit
```









