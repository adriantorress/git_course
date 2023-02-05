#Git Course

##Git commands


###Configurações
git config (--global) *user.* **name** **email**
git remote add origin *portfólio remoto*

###Inicialização
git init

###Alterando estado
git add *arquivo*
git commit (-am) *mensagem*
git reset HEAD *arquivo*
git checkout *arquivo*
git reset (--soft, --mixed, --hard) *chave*

###Checando estado e mudanças de estado
git status
git diff
git show
git log
git shortlog (-sn)

###"Github commands" *usados para subir ou pegar estado no github*
git push -u origin master *branch inicial*