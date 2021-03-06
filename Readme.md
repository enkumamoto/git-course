#Git e Github

Arquivo da aula de Git e github para iniciante.

1 - Ciclo de vida dos status dos arquivos:
	Untracked ou Não marcado: 
	São arquivos recem adicionados ao repositório mas não foram vistos pelo Git, ou seja,
	o Git não ainda não conhece dentro do repositório outra versão do arquivo. 
	
	Unmodified:
	Após adicionar o arquivo ao Git, ele passa ser consiferado não modificado. Ele existe no Git 
	mas sem modificações

	Modified:
	Quando o arquivo é editado por alguma razão, o Git o classifica como modificado.

	Staged:
	Após a modificação, pode-se se enviar o arquivo para a área de staged onde é criada a versão.
	O que acontece é quando fechar a versão, o Git "diz": Leve todos estes arquivos.
	Ao realizar o commit, o Git altera o arquivo no status Staged para Unmodified e diz que "a versão
	atual não foi modificada" até que por alguma razão o arquivo seja editado novamente e o Git realizará
	todo o ciclo.

2 - Comandos Git
	Adicionando Usuário Global:
	git config --global user.name "User Name"

	Adicionando Editor padrão:
	git config --global core.editor "nano"

	Adicionando Contato de email o Usuário:
	git config --global user.email "email@dominio.com"

	Antes de começar a usar o git, deve-se criar a pasta do projeto. E dentro dela digitar o comando git init e ele é responsável por iniciar o repositório.

	Checagem do Status do Git:
	git status

	Adicionando arquivo ao repositório:
	git add nomedoarquivo

	Realizando commit:
	git commit -m "Add Readme.md"  ---- O -m é usado para passar alguma mensagem alertando alguma modificação

	[master (root-commit) 6539a04] Add Readme.md ---- O código ápos o (toot-commit) é um rash identificador, caso queira voltar versão ou verificar os logs
	1 file changed, 39 insertions(+) ---- Aqui diz quantos arquivos modificados e quantas interações no arquivo.
	create mode 100644 Readme.md

	Lembre-se, se o arquivo for editado e não readiciona-lo ao repositório e realizar commit, o git retornará um erro.

	Verificando o log do GIT
	git log ---- este comando apresenta:
	
	eiji@lpiss:~/git-course$ git log
	commit cc1d6907250b01685fbb64b3576a006fb71fe702 (HEAD -> master) ---- uma HASH do commit para identificação
	Author: Eiji Kumamoto <eiji.kumamoto@gmail.com> ---- o email de quem editou
	Date:   Tue May 5 14:03:20 2020 -0300 ---- Data e hora

            Readme.md editado por Eiji novamente ---- O arquivo e o comentário

	commit 85bae6dd3dee29e82eb7765b13665e944694e04c
	Author: Eiji Kumamoto <eiji.kumamoto@gmail.com>
	Date:   Tue May 5 14:01:24 2020 -0300

	    Readme.md editado por Eiji

	commit 6539a043d9292d1265ec7ce5ba8ae11f56d65c41
	Author: Eiji Kumamoto <eiji.kumamoto@gmail.com>
	Date:   Tue May 5 13:55:16 2020 -0300

	    Add Readme.md
	
	Pode-se filtrar por Autor
	git log --author="Autor"

	Pode-se filtrar por ordem alfabetica
	git shortlog
	eiji@lpiss:~/git-course$ git shortlog
	Eiji Kumamoto (4): ---- Quem realizou commit e a quantidade
      		Add Readme.md ---- Arquivos e mensagens que foram editados
      		Readme.md editado por Eiji
      		Readme.md editado por Eiji novamente
      		Readme.md editado por Eiji novamente
	
	Se executado o git shortlog -sn só aparecerá os usuários e a quantidades de commits feitos por cada um

	O comando git log --graph apresenta um gráfico representando as manipulações dos arquivos.

	Executando o comando git show 'hash' ---- este comando é importante para acompanha o andamento do arquivo

	eiji@lpiss:~/git-course$ git show b241e3c765fcb376b07fcda531937ea69fd772fa
	commit b241e3c765fcb376b07fcda531937ea69fd772fa (HEAD -> master)
	Author: Eiji Kumamoto <eiji.kumamoto@gmail.com>
	Date:   Fri May 8 13:18:05 2020 -0300
	
	    Readme.md editado por Eiji novamente
	
	diff --git a/Readme.md b/Readme.md
	index 2a7afbb..a6d75cc 100644
	--- a/Readme.md
	+++ b/Readme.md
	@@ -45,3 +45,31 @@ Arquivo da aula de Git e github para iniciante.
	        create mode 100644 Readme.md
	 
	        Lembre-se, se o arquivo for editado e não readiciona-lo ao repositório e realizar commit, o git retornará um erro.
	+
	+       Verificando o log do GIT
	+       git log ---- este comando apresenta:
	+       
	+       eiji@lpiss:~/git-course$ git log
	+       commit cc1d6907250b01685fbb64b3576a006fb71fe702 (HEAD -> master) ---- uma HASH do commit para identificação
	+       Author: Eiji Kumamoto <eiji.kumamoto@gmail.com> ---- o email de quem editou
	+       Date:   Tue May 5 14:03:20 2020 -0300 ---- Data e hora
	+
	+            Readme.md editado por Eiji novamente ---- O arquivo e o comentário
	+
	+       commit 85bae6dd3dee29e82eb7765b13665e944694e04c
	+       Author: Eiji Kumamoto <eiji.kumamoto@gmail.com>
	+       Date:   Tue May 5 14:01:24 2020 -0300
	+
	+           Readme.md editado por Eiji
	+
	+       commit 6539a043d9292d1265ec7ce5ba8ae11f56d65c41
	+       Author: Eiji Kumamoto <eiji.kumamoto@gmail.com>
	+       Date:   Tue May 5 13:55:16 2020 -0300
	+
	+           Add Readme.md
	+       
	+       Pode-se filtrar por Autor
	+       git log --author="Autor"
	+
	+       Pode-se filtrar por ordem alfabetica
	+       git shortlog

	Executando o comando git diff apresentará a ultima modificação feita no arquivo. Mesmo que não adicione e realize commit
	será apresentado está modificação. Mas se adicionar e commitar, o git diff não retorna output. Este comando é importante
	para revisar o conteudo do arquivo antes de realizar um commit.
	
	Com o git diff --name-only pode-se filtrar pelo nome do arquivo e ele listará todos os arquivos com o mesmo nome.
	
	Usando git commit -am faz com que o arquivo já existente seja adicionado e commitado.

	Caso o arquivo contenha alguma coisa errada, ou desnecessário, basta usar o comando git checkout seguido do nome do arquivo
	assim o arquivo volta para o ponto anterior a edição.

	Simulando:
	eiji@lpiss:~/git-course$ git add Readme.md ---- Adicionando arquivo
	eiji@lpiss:~/git-course$ git status ---- Checando status
	No ramo master
	Mudanças a serem submetidas:
	  (use "git reset HEAD <file>..." to unstage)
	
	        modified:   Readme.md 
	
	eiji@lpiss:~/git-course$ git diff Readme.md ---- Checando e recebendo sem retorno
	eiji@lpiss:~/git-course$ 
	eiji@lpiss:~/git-course$ git reset HEAD Readme.md ---- Retirando de modo Staged
	Unstaged changes after reset:
	M       Readme.md
	eiji@lpiss:~/git-course$ git status ---- checando status
	No ramo master
	Changes not staged for commit:
	  (utilize "git add <arquivo>..." para atualizar o que será submetido)
	  (utilize "git checkout -- <arquivo>..." para descartar mudanças no diretório de trabalho)
	
	        modified:   Readme.md
	
	nenhuma modificação adicionada à submissão (utilize "git add" e/ou "git commit -a")
	eiji@lpiss:~/git-course$ git diff ---- verificando conteúdo
	diff --git a/Readme.md b/Readme.md
	index 7bd0e30..55e5ab7 100644
	--- a/Readme.md
	+++ b/Readme.md
	@@ -140,3 +140,5 @@ Arquivo da aula de Git e github para iniciante.
	+
	+svdkjghaproghaerbjajobaejgb --- linha com erro
	eiji@lpiss:~/git-course$ git checkout Readme.md ---- Retornando arquivo para o ponto anterior
	eiji@lpiss:~/git-course$ git status ---- checando status
	No ramo master
	nothing to commit, working tree clean
	
	Caso queira retornar a versão do arquivo após ter realizado o commit deve-se ficar atento para usar o reset.
	O git reset --soft --mixed --hard 'hash'
	
	git reset --soft 'hash': deve-se usar a hash anterior ao último commit, pois voltando a versão o ultimo hash deixará de existir
	com isso deverá veririficar usando um git log, achar a hash e em seguida usar o git reset --soft 'hash' e por fim a versão que 
	foi retornada estará pronta para realizar commit.

	git reset --mixed 'hash': faz o que o --soft mas põe o arquivo antes do modo staged

	git reset --hard 'hash': faz o mesmo do mixed, mas também sobrescreve o conteúdo do meu working dir.

	Adicionando repositorio remoto
	git remote add origin git@github.com:enkumamoto/git-course.git
	eiji@lpiss:~/git-course$ git remote ---- apresenta o nome do repositório
	origin
	eiji@lpiss:~/git-course$ git remote -v ---- apresenta o endereçamento
	origin  git@github.com:enkumamoto/git-course.git (fetch)
	origin  git@github.com:enkumamoto/git-course.git (push)

	Enviando arquivos remotamente para o repositório remoto
	git push -u origin master ---- o comando enviará todos os arqivos do diretório (master) para o repositório (origin)
	
	Git permite clonar repositórios do github. o caminho do repositório é disponibilizado na página do github
	VIA SSH: git clone git@github.com:enkumamoto/python-LOM.git

	ou

	VIA HTTPS: git clone https://github.com/enkumamoto/python-LOM.git

	git stash ---- serve quando está trabahando num arquivo, salva-lo sem subir para uma nova versão e mantê-lo em WIP (Work In Progress). 
		       Com isso pode-se realizar outros trabalhos e depois retornar a editar o arquivo em stash usando o comando seguinte.
	git stash apply ---- quando retornar ao trabalho com o arquivo ele apresentará as modificações feitas.
	git stash list ---- apresenta todos os arquivos em stash.
	git stash clear ---- limpará tudo que está no stash.

3 - Recursos na página do GitHub
	
	Botão Fork serve para copiar um repositório de terceiros, a intenção é contribuir com o repositório
	corrigindo-o ou complementando ou melhorando o código e por fim reenvia-lo para o dono do repositório 
	através de request e informar as mudanças realizadas. Então clica em Fork e vai abrir as opções para 
	onde irá a cópia, clica na organização e a cópia será automaticamente feita. É diferente do clone, pois
	irá copiar, o usuário consegue modificar mas não envia de volta para o owner.

4 - O que é branch?
	
	É um ponteiro móvel que leva a um commit.
	Quando um repositório é criado e a cada commit é gerado uma hash e para cada hash é feito um snapshot,
	o branch apontará para o commit e o primeiro branch se chama master, quando realizado o commit a versão 
	original deixa de ser master, recebe um hash, faz-se um snapshot e a versão atualizada do arquivo torna-se 
	master. O git permite que o branch master fique em outro hash (que não é o arquivo que esteja trabalhando 
	no momento)
	
	Vantagens do uso do branch:
	1 - poder modificar sem alterar o local principal (Master)
	2 - é facilmente desligável, pode-se criar e apagar os branches sem problemas
	3 - múltiplas pessoas trabalhando em branches diferente ao mesmo tempo
	4 - evita conflitos, já que existe branches diferentes, pode-se trabalhar isoladamente
	    de outras pessoas e evitando conflitos no arquivo.

4.1 - Utilizando branches

	git checkout -b <branch name> ---- o argumento -b cria um branch
	
	ao digitar o comando git branch, ele mostrará qual branch está utilizando.
	
	para mudar de um branch para outro deve-se utilizar git branch <branch name>
	
	para apagar um branch basta utilizar git branch -D <branch name>

5 - Merge e rebase
	
	São métodos de unir branches. Ambos tem mesma função mas com algumas diferenças
	


5.1 - Merge

	Imagine que temos o seguinte estado inicial onde dois branches apontam para o mesmo commit

			   Branch Master

	C0 <------- C1 <------- C2

			   Branch Iss53

	
	Com isso criaou-se um novo commit com o novo branch, deixando o commit master apontando para o C2.
	isso ainda mantem a situação abaixo linear.

                           Branch Master

        C0 <------- C1 <------- C2 <------- C3

				       Branch Iss53


	Se criar um outro novo commit a partir do master, será criada uma ramificação

                          Branch Master     Branch Hotfix

        C0 <------- C1 <------- C2 <------- C4
				 \
				  \
				   C3
                                Branch Iss53


        Se criar um outro novo commit a partir do Iss53, será modificada a ramificação.
	C5 e C3 estrão apontados para o C2 e o C4 passa a ser o master.

                                       Branch Master

        C0 <------- C1 <------- C2 <------- C4
                                 \ 
                                  \  
                                   C3 <------- C5
                                          Branch Iss53


	Para juntar todos os commits e deixar tudo linear, será necessário realizar um novo
	commit juntando C3, C4 e C5.

                                                   Branch Master

        C0 <------- C1 <------- C2 <------- C4 <------- C6
                                 \                      /
                                  \                    /  
                                   C3 <------- C5 <----
                                          Branch Iss53

	Isso é realizar merge, que acaba criando um ciclo ou forma diamante.

	Quais os pros e contras do merge?
	Pro:
	   Operação não destrutiva, não vai destruir commit mas criará novo commit
	   para juntar tudo, sem estragar ou movimentar o histórico
	   

	Contra:
	   commit extra sem sentido, que não junta código ou cria novo arquivo
	   deixa o histórico poluído

5.2 - Rebase

	Estado inicial, commits distintos apontados para o C2

                                       Branch Master

        C0 <------- C1 <------- C2 <------- C4
                                 \
                                  \
                                   C3
                                Branch Experiment


	O rebase moverá o commit do Experiment (C3) para após o C4 e assim ficará linear
	e acaba realizando um processo de fast foward e aplica todas as mudanças para frente
	da fila.
	Assim os dois branches apontam para o mesmo commit.

	                                         Branch Master    
 
        C0 <------- C1 <------- C2 <------- C4 <-------C3' 

                                                 Branch Experiment
                                  
                                   C3 (Branch Morto)

       Quais os pros e contras do rebase?
        Pro:
           Evita commits extras
	   Historico linear


        Contra:
           Perde a ordem cronológica dos commits
	   Se mais pessoas estão trabalhando no mesmo arquivo
	   pode gerar problemas para upload de arquivos e con
	   flitos.

	Obs.: use git pool --rebase (para evitar mudanças de histórico)

6 - Arquivo .gitignore
	
	Serve para evitar que arquivos especificos não tornem-se públicos.
	Ele funciona como um arquivo dentro do repositório (diretporio principal) e dentro dele
	tem escrito alguns padões para não ser utilizado. Por exemplo:
	1 - Criar um arquivo .gitignore
	2 - Dentro do arquivo escreve-se o que será ignorado ou não público: *.json - Neste caso
	    todos os arquivos json serão ignorados
	3 - Se rodar o comando git status, todos os arquivos json não serão apresentados
	
	Pode-se ignorar um arquivo específico.
	
7 - Criando Alias de comandos
	
	O GIT aceita que sejam criados alias para os comandos, por exemplo:
	git config --global alias.<alias desejado> <comando/argumento> ---- o --global é para manter
	 o alias em escopo global.
	Na prática mudando git status para git s: git config --global alias.s status

8 - Tags
	
	A teg serve para apresentar um versionamento (que mudará o release dentro do GitHub)
	e nela pode-se passar uma mensagem sobre o arquivo que deu upload. Para isso deve-se
	usar o comando:
	git tag -a <número da versão> -m "Mensagem sobre o arquivo"
	Feito isso basta rodar o comando:
	git push origin master --tags
	Verificando no GitHub e acessando o release verá quem fez o upload, data, número de 
	versão e o código fonte.
	Verificando as tags do arquivo:
	git tag

9 - git revert
	
	Serve para reverte um modificação feita num arquivo que problematico dentro da aplicação
	em produção.
	Para resolver este problema, deve-se pegar o hash do commit problematico usar o comando:
	git revert <hash>
	Na prática este comando puxará o commit anterior ao hash dado no comando e sinalizará
	dentro do log.
	Se verificar mais a fundo, o comando apagará o que foi feito. Mas ele não apaga o commit 
	problemático.
	Atenção para não confundir revert com reset.

10 - Apagando Tags e Branches remotamente

	Para apagar tags dentro do git basta usar o comando:
	git tag -d <tag>
	Se realizar novo push o GitHub não apagará as tags que foram subidas.
	Para apagar do repositório remoto basta usar:
	git push origin :<tag>
	O branch é da mesma forma:
	git push origin :<branch>
