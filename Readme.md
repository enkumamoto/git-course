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

