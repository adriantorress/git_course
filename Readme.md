# Git Course

## Git commands

### Inicialização

**git init**
> cria o .git na pasta atual e cria uma ramificação principal e inicial -> a branch master.

### Configurações

**git config --global (user.name, user.email) (*nome ou email*)**
> configuração do nome e email do usuário para a máquina local

**git remote add origin (*portfólio remoto*)**
> configurando para qual repositório remoto a sua pasta atual vai apontar

### Branch commands

**git checkout -b  (*nome da branch*)**
> criando uma nova branch

**git branch**
> visualizando as branchs existentes

**git checkout (*nome da branch*)**
> trocando de branch

**git branch -D (*nome da branch*)**
> deletando uma branch

**git merge**
> junção de branchs: gera um novo commit (a branch master apontará para ele), com a junção (as mudanças das branchs que se deram o merge estará nele), continuando com a ordem cronológica dos commits das branchs que foram juntadas

**git rebase**
> junção de branchs: não gera um novo commit, apenas move um deles para o inicio e forma uma única fila (as branchs apontarão para esse commit movido para a frente). gera um histórico linear, mas perde a ordem cronológica

### Alterando estado

**git add (*arquivo*, .)**
> pegando os arquivos que estão untracked ou modified e deixando-os staged, ou seja, que podem ser "comitados"

**git commit (-m, -am) (*mensagem*)**
> pega os arquivos que estão staged adiciona uma mensagem "a eles", os tornam unmodified e os deixam preparados para ir para o repositório remoto com o push //o -am pega todos os arquivos que já foram trackeados e estão em modified ou staged

**git reset HEAD (*arquivo*)**
> pega os arquivos que estão em staged e os tornam unstaged, que não podem ser "comitados"

**git checkout (*arquivo*)**
> os arquivos que estão modified perdem todas as alterações e voltam ao estado do último commit

**git reset (--soft, --mixed, --hard) (*chave*)**
> git reset vai receber a chave de um estado, se for anterior ao atual, ele vai pegar o estado atual e voltar para estados anteriores conforme ordenado: com o --soft, ele volta do último commit feito para o estado de staged; com o --mixed ele volta para o estado de modified e com o --hard ele volta para o estado de unmodified, apagando todas as alterações, ou seja, basicamente excluindo o commit atual 

**git revert (*chave*)**
> ele reverte as alterações do último commit, mas não o exclui, cria outro commit com a reversão e o que foi revertido continua no histórico para possíveis correções futuras 

### Checando estado e mudanças de estado

**git status**
> checa o estado atual

**git show**
> mostra o último commit

**git diff**
> checa as mudanças do último commit para o estado atual

**git log**
> mostra todos os commits com todas as infos sobre eles

> --graph: ver os logs de uma forma mais visual

**git shortlog (-s)**
> mostra os commits de forma abreviada (autor e commits), com o -s da pra abreviar para mostrar somente autor e quantidade de commits

### "Github commands" 
> os comandos usados para subir ou pegar estado no github

**git push -u origin master**
> subindo para a branch inicial

**git pull**
> sincronizando o repositório local com o remoto 

### Ignorando arquivos
> com o .gitignore da para ignorar arquivos que você não quer subir para o github, fazendo com que eles não apareçam para serem trackeados 

> da para utilizar o "*" para ignorar arquivos pelas extensões, exemplo: *.json ignoraria todos os arquivos que tivessem essa extensão

> há também uma biblioteca no github chamada gitignore, no qual consegue-se ver padrões de arquivos que costumam ser ignorados por cada tipo de projeto

### Guardando mudanças ainda não finalizadas
**git stash**
> guarda as mudanças de um arquivo que está modified, escondendo as mudanças do ciclo de estados do git, ficará como "work in progress", ou seja, consegue-se continuar trabalhando em outros arquivos e só chamar as mudanças quando for conveniente.

**git stash apply**
> pega as mudanças que estão escondido e as tornam visíveis novamente, tornando o arquivo modified

**git stash list**
> mostra todos os arquivos que estão em stash

**git stash clear**
> apaga as mudanças que estão no stash

### Criando alias para os comandos
**git config --global alias.(*alias*) (*comando do alias*)**
> cria um apelido para o comando desejado

### Criando tags para agrupar commits
**git tag -a (*versão*) -m (*mensagem*)**
> cria a tag

**git tag**
> mostra as tags criadas

**git push --tags**
> sobe as tags pro Github

**git tag -d (*tag*)**
> apaga a tag

### Apagando tag ou branch no repositório remoto
**git push  origin: (*tag* ou *branch*)**
> diferente de outros comandos que só apagam no repositório local, esse comando apaga a tag ou a branch no repositório remoto, ou seja, no Github 

### Criando chave SSH para acesso ao repositório remoto
> algumas vezes é possível que tenha alguma negação de permissão para subir o projeto para o repositório remoto, e então se faz necessário criar a chave para dar essa permissão ao dispositivo.

**ssh-keygen -t rsa -b 4096 -C (*email*)**
> gera a chave ssh

**cd ~/.ssh**
> navega até a pasta que está a chave

**(cat ou more) id_rsa.pub**
> retorna a chave pública

> ao pegar a chave pública é só ir em settings no github e adicioná-la aos seus SSHs

