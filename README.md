# Git Cheat Sheet


| Comando	|Função| 
| -------- | ------- |
|git status	|List which files are staged, unstaged, and untracked.|
|git add <directory>|	Stage all changes in <directory> for the next commit. Replace <directory> with a <file> to change a specific file|
|git rm --cached <file>	| unstage file - não será enviado ao repositório|
|git rm --cached -r .	| unstage all files|
|git restore —staged <file> |	funciona como o rm —cached <file> porém quando já existe um commit, assim o git tem um ponto para retornar.|
|git commit -m “mensagem” |	Comita o arquivo|
|git diff |	irá mostrar as diferenças entre o que está comitado vs o arquivo atual (porém não pode estar staged)|
|git diff --cached / git diff --staged|mostra as diferenças entre o que está comitado vs os arquivos que estão staged|
|git log |	mostra o histórico de commits|
|git log --oneline |	mostra apenas o início do SHA do commit e a mensagem de commit
|git log -[x] |	irá mostrar apenas [ x ] commits
|git log --patch / git log -p |	Mostra as alterações que foram feitas nos commits
|git log --stat	| mostra os arquivos que foram modificados
|git log —shortstat |	mostra apenas quantos arquivos foram modificados. não especifica quais
|git commit —amend -m “Nova mensagem” |	Irá substituir a mensagem do último commit. ATENÇÃO!!! TAMBÉM IRÁ EXCLUIR O COMMIT E CRIAR UM NOVO COMMIT, PODE SER PERIGOSO QUANDO TRABALHO EM EQUIPE
|git commit —amend —no-edit |	Irá criar um novo commit com a mesma mensagem do último commit, porém se tivermos feito modificações(adição e modificação de arquivos) essas modificações são comitadas. ATENÇÃO: EXCLUI O COMMIT ANTERIOR E CRIA UM NOVO. ATENÇÃO PARA TRABALHO EM EQUIPE QUE JÁ FORAM FEITO O PUSH PARA O REPOSITORIO |
|git commit —amend	| entra no editor para editar o último commit |
| git checkout [sha] |	irá retornar ao commit indicado pelo sha |
|git checkout main	| retorna para a branch main|
|git checkout [file-name]|	retorna o arquivo [file-name] para a versão do último commit. Irá perder todas as novas alterações.|
|git clean -f 	|remove todos os arquivos não rastreados; |
|git checkout . + git clean -f |	Retorna o repositório ao estado do último commit (porém não irá perder os arquivos que estiverem staged)|
|git reset —hard	|ignora todas modificações e retorna para o último commit, mesmo tendo arquivos em staged. (o checkout não iria retornar para o estado anterior se tiver um arquivo que já foi staged)|
|git update-index --skip-worktree <file> |	para de rastrear o <file> (mais infos na sessão de gitignore)|
|git clone <repositorio-a-ser-clonado> <nome-da-nova-pasta> |	clonar repositório|
|git remove -v	| mostra qual o repositório remoto que está setado para fazer o ‘pull’ e quando para fazer o ‘push’ |
|git remote add origin <url do repo remoto> |	Associa um repositorio remoto O ‘origin’ não é necessariamente este nome, porém é o padrão utilizado |
| git remote set origin <nova url> |	Atualiza a url do repositório remoto. Se o nome ‘origin’ for outro usamos este outro nome. |
|git branch —list |	listagem das branches |
| git branch <nome-da-branch> |	cria uma nova branch |
|git checkout <nome-da-branch>	|troca a branch atual|
|git checkout -b <nome-da-branch>|	cria e faz checkout em um comando|
|git switch -|	volta para a branch anterior|
|git switch -c <nome-da-nova-branch>	|cria e faz o checkout para a nova branch|
| git push —set-upstream origin <nome-da-branch> / git push -u origin <nome-da-branch>	| envia a branch local para o servidor, o <nome-da-branch> não necessariamente tem que ser o mesmo que a branch local, mas é boa prática usar o mesmo para nao ter confusao |
|git branch -d <nome-da-branch> / git branch -D <nome-da-branch>	 | deleta a branch ao usar D maiúsculo faça a deleção “forçada|
| git push —delete origin <nome-da-branch> |	deleta a branch do repositorio remoto|
|git branch -m <novo-nome> |	renomeia a branch atual |
|git branch -m <nome-antigo> <novo-nome>| 	renomeia a branch <nome-antigo> para <novo-nome>
Não é possível renomear a branch do repositorio. Para isso devemos deletar a branch com nome antigo e enviar para o repositorio novamente. |
|git log <nome-da-branch> |	mostra os commits feitos na <nome-da-branch> |
| git merge <nome-da-branch> |	irá fazer o merge na branch atual a partir da branch <nome-da-branch> |
| git branch —no-merged	| mostra quais branchs possuem modificações que não foram mergeadas na branch atual |
|git branch —merged|	mostra as branchs que foram mergeadas na branch atual|
|git merge —abort + git reset —hard |	cancela o merge em casos de conflito |
|git tag <nome-da-tag> |	cria uma tag na branch atual, no último commit feito esta é uma tag ‘lightweight’|
|git tag -a -m “mensagem da tag” <nome-da-tag> |	Cria uma tag na branch atual, no último commit feito, adicionando a mensagem |
|git show <nome-da-tag>  (em uma tag com mensagem)| irá aparecer informações de quem criou a tag, seu email e a data de criação da tag |
|git tag	 |mostra todas as tags do projeto|
|git tag -n|	mostra as tags e também as mensagens associadas a elas. Se a tag não possui mensagem, a mensagem será a mesma mensagem do commit associado a ela |
|git tag <nome-da-tag> <número-de-um-commit>|	adiciona uma tag ao commit especificado|
|git push origin <nome-da-tag>|	envia a tag para o repositorio|
|git push --tags|	envia todas as tags para o repositorio|
|git checkout <tag>|	funciona como fazer o checkout para um commit|
|git diff <tag> <outra-tag>|	mostra as diferenças entre o codigo das tags|
|git tag -d <tag>|	apaga a <tag> localmente|
|git push --delete origin <tag>|	apaga a <tag> do repositorio|
|git stash	|‘guarda’ as modificações feitas sem realizar um commit. Dessa forma podemos mudar a branch atual sem a necessidade de commitar e sem perder o trabalho atual. Salva apenas arquivos rastreados|
|git stash list|	mostra o que está stashed|
|git stash apply|	aplica as mudanças que estão stasheadas na posição 0 na branch atual|
|git stash apply stash@{x}	|aplica as mudanças que estão stashed na posição x|
|git stash pop|	aplica o ultimo stash e remove ele da lista|
|git stash drop |	remove o stash mais recente|
| git stash drop stash@{x} | remove o stash da posição x|
|git stash branch <nome-da-branch>|	cria uma nova branch a partir do stash|
| git revert HEAD | Reverte o último commit. Um arquivo com possibilidade de edição será aberto. Para confirmar basta fechar o arquivo.
Esse comando não exclui o commit, mas cria um novo commit fazendo a reversão do que foi feito no último commit|
|git rever HEAD --no-edit |(esse comando não abre um arquivo para edição da mensagem)	Reverte o último commit|
|Esse comando não exclui o commit, mas cria um novo commit fazendo a reversão do que foi feito no último commit|
|git reset —hard HEAD~x|	Reverte o Head X commits (se for 1, apaga o último commit, se for 2, apaga os últimos 2 commits…)|
|git reset --mixed HEAD~1|	Retorna o HEAD 1 commit (ou seja, apaga o último commit), porém sem perder o arquivo que foi feita a mudança. Este arquivo ficará unstaged, ou seja, as mudanças ainda não foram adicionadas.|
|git reset --mixed HEAD~1	|Retorna o HEAD 1 commit (ou seja, apaga o último commit), porém sem perder o arquivo que foi feita a mudança. Este arquivo ficará staged, ou seja, as mudanças já foram adicionadas.|
|git push --force|	Quando o repositório remoto está diferente do local podemos usar este comando para forçar o envio do repo local para o servidor. O que estiver no servidor que for diferente do repositorio local será perdido|
|git push --force-with-lease|	Irá forçar o envio do repo local para o servidor, mas apenas se isso não apagar nenhum commit.|
|git rebase <branch-para-fazer-o-rebase>|	faz com que a base de criação da branch atual traga as mais recentes mudanças da <branch-para-fazer-o-rebase>|
|git pull --rebase|	faz o pull do repositorio remoto para o local, fazendo um rebase do repo local, sem precisar, desta maneira, realizar um commit de merge|
|git fetch origin develop|Irá trazer informações da branch remota ‘develop’, sem criar uma branch local|
|git branch -a|Mostra todas as branch, incluindo as branchs remotas
|git checkout develop	|Irá entender que é para criar a branch buscando as informações do servidor (tem que ser feita depois de usar o fetch) |
|git rebase --interactive HEAD~x|	Faz a integração dos últimos X commits a partir do HEAD.|
|git cherry-pick <Commit>	|Traz para a branch atual apenas o <commit>|
|git bisect |	Utiliza de busca binária para procurar em qual commit há um erro|
|git fetch|traz as atualizações do servidor remoto, porém sem fazer o merge com a branch atual. Podemos fazer o diff entre a origin/main com a main|
|git log origin/main|mostra o log da origin|
|git diff origin/main|mostra as diferenças da main local com a origin/main|
|git merge	| faz o merge origin/main com o main|
