Git e Git Flow Cheat Sheet em Português do Brasil [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============
<hr>
<p align="center">
	<img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>
<hr>

# Outras línguas disponíveis:
1. [Inglês Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/README.md)
2. [Árabe Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-ar.md)
3. [Chinês Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-zh.md)
4. [Híndi Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-hi.md)
5. [Turco Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-tr.md)
6. [Espanhol Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-es.md)

Git cheat sheet salva você de decorar os comandos.

Sinta-se livre para contribuir e/ou atualizar os erros de gramática . Você pode também adicionar um arquivo do seu idioma.
<hr>

Git Cheat Sheet Português do Brasil
===============
### Índice
* [Configuração](#setup)
* [Arquivos de Configuração](#configuration-files)
* [Criar](#create)
* [Mudanças locais](#local-changes)
* [Buscar](#search)
* [Histórico de Commits](#commit-history)
* [Branches & Tags](#branches--tags)
* [Atualizar & Publicar](#update--publish)
* [Merge & Rebase](#merge--rebase)
* [Desfazer](#undo)
* [Git Flow](#git-flow)


<hr>

## Configuração

##### Mostrar a configuração atual:
```
$ git config --list
```
##### Mostrar a configuração do repositório:
```
$ git config --local --list
```

##### Mostrar a configuração global:
```
$ git config --global --list
```

##### Mostrar a configuração do sistema:
```
$ git config --system --list
```

##### Definir um nome que é usado para crédito quando se revisa o histórico de versão:
```
$ git config --global user.name "[primeiroNome sobrenome]"
```

##### Definir um endereço de email que será associado com cada marca no histórico:
```
$ git config --global user.email "[valid-email]"
```
##### Definir cores automáticas na linha de comando do Git para fácil revisão:
```
$ git config --global color.ui auto
```

##### Definir o editor global para commit
```
$ git config --global core.editor vi
```

<hr>

## Arquivos de Configuração

##### Arquivo de configuração específico do Repositório [--local]:
```
<repo>/.git/config
```

##### Arquivo de configuração específico do usuário [--global]:
```
~/.gitconfig
```

##### Arquivo de configuração do Sistema [--system]:
```
/etc/gitconfig
```

<hr>

## Criar

##### Clonar um repositório existente:

Existem duas maneiras:

Através de SSH

```
$ git clone ssh://usuario@dominio.com/repo.git
```

Através de HTTP

```
$ git clone http://dominio.com/usuario/repo.git
```

##### Crie um novo repositório local:
```
$ git init
```
<hr>

## Mudanças Locais

##### Mudanças no diretório de trabalho:
```
$ git status
```

##### Mudanças nos arquivos rastreados:
```
$ git diff
```

##### Adiciona todas as alterações atuais ao próximo commit:
```
$ git add .
```

##### Adiciona algumas mudanças feitas no &lt;arquivo&gt; ao próximo commit:
```
$ git add -p <arquivo>
```

##### Realizar um commit de todas as mudanças nos arquivos rastreados:
```
$ git commit -a
```

##### Realizar um commit de mudanças previamente adicionadas na staging área:
```
$ git commit
```

##### Realizar um commit com mensagem:
```
$ git commit -m 'mensagem aqui'
```

##### Realizar um commit ignorando a staging área e adicionando uma mensagem:
```
$ git commit -am 'mensagem aqui'
```

##### Realizar um commit para alguma data anterior:
```
git commit --date="`date --date='n dias atrás'`" -am "Mensagem de Commit"
```

##### Modificar o último commit:<br>
<em><sub>Não modificar commits já publicados!</sub></em>
```
$ git commit -a --amend
```

##### Modificar data do último commit:
```
GIT_COMMITTER_DATE="date" git commit --amend
```

##### Modificar data do autor do último commit:
```
git commit --amend --date="date"
```

##### Mover mudanças que não foi feito commit ainda do branch atual para outro brach:<br>
```
git stash
git checkout branch2
git stash pop
```

##### Restaurar mudanças armazenadas de volta para o branch atual:
```
git stash apply
```

##### Remover o último conjunto de mudanças armazenadas:
```
git stash drop
```

<hr>

## Search

#####A text search on all files in the directory:
```
$ git grep "Hello"
```

#####In any version of a text search:
```
$ git grep "Hello" v2.5
```

<hr>
###Commit History

#####Show all commits, starting with newest (it'll show the hash, author information, date of commit and title of the commit):
```
$ git log
```

#####Show all the commits(it'll show just the commit hash and the commit message):
```
$ git log --oneline
```

#####Show all commits of a specific user:
```
$ git log --author="username"
```

#####Show changes over time for a specific file:
```
$ git log -p <file>
```

#####Display commits that are present only in remote/branch in right side
```
$ git log --oneline <origin/master>..<remote/master> --left-right
```

#####Who changed, what and when in &lt;file&gt;:
```
$ git blame <file>
```

#####Show Reference log:
```
$ git reflog show
```

#####Delete Reference log:
```
$ git reflog delete
```
<hr>
##Branches & Tags

#####List all local branches:
```
$ git branch
```

#####List all remote branches:
```
$ git branch -r
```

#####Switch HEAD branch:
```
$ git checkout <branch>
```

#####Create and switch new branch:
```
$ git checkout -b <branch>
```

#####Create a new branch based on your current HEAD:
```
$ git branch <new-branch>
```

#####Create a new tracking branch based on a remote branch:
```
$ git branch --track <new-branch> <remote-branch>
```

#####Delete a local branch:
```
$ git branch -d <branch>
```

#####Force delete a local branch:
<em><sub>You will lose unmerged changes!</sub></em>

```
$ git branch -D <branch>
```

#####Mark the current commit with a tag:
```
$ git tag <tag-name>
```

#####Mark the current commit with a tag that includes a message:
```
$ git tag -a <tag-name>
```
<hr>
##Update & Publish

#####List all current configured remotes:
```
$ git remote -v
```

#####Show information about a remote:
```
$ git remote show <remote>
```

#####Add new remote repository, named &lt;remote&gt;:
```
$ git remote add <remote> <url>
```

#####Download all changes from &lt;remote&gt;, but don't integrate into HEAD:
```
$ git fetch <remote>
```

#####Download changes and directly merge/integrate into HEAD:
```
$ git remote pull <remote> <url>
```

#####Get all changes from HEAD to local repository:
```
$ git pull origin master
```

#####Get all changes from HEAD to local repository without a merge:
```
git pull --rebase <remote> <branch>
```

#####Publish local changes on a remote:
```
$ git push remote <remote> <branch>
```

#####Delete a branch on the remote:
```
$ git push <remote> :<branch> (since Git v1.5.0)
or
git push <remote> --delete <branch> (since Git v1.7.0)
```

#####Publish your tags:
```
$ git push --tags
```
<hr>
##Merge & Rebase

#####Merge <branch> into your current HEAD:
```
$ git merge <branch>
```

#####Rebase your current HEAD onto &lt;branch&gt;:<br>
<em><sub>Don't rebase published commit!</sub></em>

```
$ git rebase <branch>
```

#####Abort a rebase:
```
$ git rebase --abort
```

#####Continue a rebase after resolving conflicts:
```
$ git rebase --continue
```

#####Use your configured merge tool to solve conflicts:
```
$ git mergetool
```

#####Use your editor to manually solve conflicts and (after resolving) mark file as resolved:
```
$ git add <resolved-file>
```

```
$ git rm <resolved-file>
```

#####Squashing commits:
```
$ git rebase -i <commit-just-before-first>
```

Now replace this,

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

to this,

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```
<hr>
##Undo

#####Discard all local changes in your working directory:
```
$ git reset --hard HEAD
```

#####Get all the files out of the staging area(i.e. undo the last `git add`):
```
$ git reset HEAD
```

#####Discard local changes in a specific file:
```
$ git checkout HEAD <file>
```

#####Revert a commit (by producing a new commit with contrary changes):
```
$ git revert <commit>
```

#####Reset your HEAD pointer to a previous commit and discard all changes since then:
```
$ git reset --hard <commit>
```

#####Reset your HEAD pointer to a remote branch current state.
```
git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

#####Reset your HEAD pointer to a previous commit and preserve all changes as unstaged changes:
```
$ git reset <commit>
```

#####Reset your HEAD pointer to a previous commit and preserve uncommitted local changes:
```
$ git reset --keep <commit>
```

#####Remove files that were accidentally committed before they were added to .gitignore
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
```
<hr>

##Git-Flow

###Index
* [Setup](#setup)
* [Getting Started](#getting-started)
* [Features](#features)
* [Make a Release](#make-a-release)
* [Hotfixes](#hotfixes)
* [Commands](#commands)
<hr>


###Setup
######You need a working git installation as prerequisite. Git flow works on OSX, Linux and Windows.

#####OSX Homebrew:
```
$ brew install git-flow
```

#####OSX Macports:
```
$ port install git-flow
```

#####Linux (Debian-based):
```
$ apt-get install git-flow
```

#####Windows (Cygwin):
######You need wget and util-linux to install git-flow.
```
$ wget -q -O - --no-check-certificate https://github.com/nvie/gitflow/raw/develop/contrib/gitflow-installer.sh | bash
```
<hr>


###Getting Started
######Git flow needs to be initialized in order to customize your project setup. Start using git-flow by initializing it inside an existing git repository:
#####Initialize:
######You'll have to answer a few questions regarding the naming conventions for your branches. It's recommended to use the default values.
```
git flow init
```
<hr>


###Features
######Develop new features for upcoming releases. Typically exist in developers repos only.
#####Start a new feature:
######This action creates a new feature branch based on 'develop' and switches to it.
```
git flow feature start MYFEATURE
```

#####Finish up a feature:
######Finish the development of a feature. This action performs the following:
######1)Merged MYFEATURE into 'develop'.
######2)Removes the feature branch.
######3)Switches back to 'develop' branch
```
git flow feature finish MYFEATURE
```

#####Publish a feature:
######Are you developing a feature in collaboration? Publish a feature to the remote server so it can be used by other users.
```
git flow feature publish MYFEATURE
```

#####Getting a published feature:
######Get a feature published by another user.
```
git flow feature pull origin MYFEATURE
```

#####Tracking a origin feature:
######You can track a feature on origin by using
```
git flow feature track MYFEATURE
```
<hr>


###Make a Release
######Support preparation of a new production release. Allow for minor bug fixes and preparing meta-data for a release

#####Start a release:
######To start a release, use the git flow release command. It creates a release branch created from the 'develop' branch. You can optionally supply a [BASE] commit sha-1 hash to start the release from. The commit must be on the 'develop' branch.
```
git flow release start RELEASE [BASE]
```
######It's wise to publish the release branch after creating it to allow release commits by other developers. Do it similar to feature publishing with the command:
```
git flow release publish RELEASE
```
######(You can track a remote release with the: ```git flow release track RELEASE``` command)

#####Finish up a release:
######Finishing a release is one of the big steps in git branching. It performs several actions:
######1)Merges the release branch back into 'master'
######2)Tags the release with its name
######3)Back-merges the release into 'develop'
######4)Removes the release branch
```
git flow release finish RELEASE
```
######Don't forget to push your tags with ```git push --tags```
<hr>


###Hotfixes
######Hotfixes arise from the necessity to act immediately upon an undesired state of a live production version. May be branched off from the corresponding tag on the master branch that marks the production version.

#####Git flow hotfix start:
######Like the other git flow commands, a hotfix is started with
```
$ git flow hotfix start VERSION [BASENAME]
```
######The version argument hereby marks the new hotfix release name. Optionally you can specify a basename to start from.

#####Finish a hotfix:
######By finishing a hotfix it gets merged back into develop and master. Additionally the master merge is tagged with the hotfix version
```
git flow hotfix finish VERSION
```
<hr>


###Commands
<p align="center">
	<img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

###Git flow schema

<p align="center">
	<img alt="Git" src="Img/git-flow-commands-without-flow.png">
</p>
<hr>
