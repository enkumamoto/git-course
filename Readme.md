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
