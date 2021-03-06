# CUSRO GIT E GITHUB
Apenas anotações do que estudei neste curso:

[Git e GitHub para iniciantes](https://www.udemy.com/course/git-e-github-para-iniciantes/)

# SECAO 1: ENTENDENDO GIT E GITHUB

## INTRODUÇÃO

GIT é utilizado para controle de versão

### DIFERENCAS ENTRE GIT E OUTROS 
	- Os outros guardam a diferença dos arquivos das versões
	- GIT guarda o estado 

## HISTORIA DO GIT
	- Controle do kernel do linux
	- Linus fez o controle dele, o git

### MELHORIAS
	- DESIGN
	- SIMPLES
	- RAPIDO
	- ROBUSTO
	- FACILITA TRABALHO EM EQUIPE
	- TOTALMENTE DISTRIBUIDO
	- FUNCIONA EM GRANDES PROJETOS

## O QUE É O GITHUB
	É UM PROJETO NA NUVEM QUE VAI ARMAZENAR OS PROJETOS QUE UTILIZAM O GIT PARA VERSIONAMENTO

# SECAO 2: CONFIGURANDO O GIT

## INSTALANDO

## CONFIGURAÇÃO INICIAL

# SECAO 3:ESSENCIAL DO GIT

## INICIALIZANDO UM REPOSITORIO
	.git - repositorio git

## USANDO O EDITOR DO TERMINAL

## CICLO DE VIDA DOS STATUS DOS ARQUIVOS
	4 ESTADOS
	- UNTRACKED
	- UNMODIFIED
	- MODIFIED
	- STAGED

## DETALHANDO CICLO
	- UNTRACKED
		- Arquivo foi adicionado mas ainda não visto pelo git
	- UNMODIFIED
		- Quando adicionado ao git ele recebe este status
		- Existe no git mas ainda não foi editado/modificado
	- MODIFIED
		- Existe e foi alterado
	- STAGED
		- Se você enviá-lo para criar a versão atual ele fica como staged

### ESTADO LOGO APÓS O COMMIT
    Após fazer o commit, os arquivos voltao ao estado umnomified, pois, na versão mais atualizada, estes arquivos ainda não foram modificados

### O QUE SIGNIFICA COMANDO GIT ADD
    É quando você iforma ao git que quer inserir aquele estado atual do arquivo na próxima versão

## O QUE É O COMMIT
    - É quando você avisa ao git: Olha, pega todos estes arquivos do repostitório e crie uma imagem dele ( tipo um snapshot, uma versão )
    - git commit -m "Add Readme.md"

### O -m SIGNIFICA MENSAGEM, O QUE ESTA ENTRE "bla bla bla"  E A MENSAGEM EM SI
    - É interessante que a mensagem enviada seja direta e explicativa do que foi realizado

### GIT COMMIT -AM "MENSAGEM"
    - O -am adiciona e comita ao mesmo tempo. ( une o add com o -m)

## VISUALIZANDO LOGS
    - git log

## VISUALIZANDO O DIFF
    - git diff

## DESFAZENDO COISAS
    - se nao estiver modificacdo (add)
    	- git checkout <nome do arquivo>
    
    - se estiver modificado (add e pronto pra ser comitado)
    	- git reset HEAD R<nome do arquivo> (tira ele do stage) 
    	- em seguida
    	- git checkout <nome do arquivo>

    - se já commitei
    	- existem 3 tipos de reset
    	- git reset --soft [destroi o commit e deixa staged]
    	- git reset -- mixed [destroi o commit e volta antes do staged, ou seja, modified]
    	- git reset --hard [destori o commit como se ele o que foi feito nele não existisse]

    - EX
    - 1 - usar o git log pra pegar a hash do penultimo (ou ponto) ponto onde você quer voltar. Pegar o ultimo, pois o git ira ignorar o hash após aquele, como se ele não existisse
    - 2 - git reset --soft 83a2d46465d7689438574d8c6580391df1cb12cd

# SECAO 4: REPOSITORIOS REMOTOS

## REPOSITORIOS REMOTOS
    - UTILIZAREMOS O GITHUB

### CRIANDO E ADICIONANDO UMA CHAVE SSH
    - APOS CRIAR ENTRAR NA PASTA
    	- cd ~/.ssh/
    	- LA ESTARAO OS ARQUIVOS [chaves]
    	- id_rsa
    	- id_rsa.pub [chave adicionada no github]
    - PARA VISUALIZAR A CHAVE, DIGITE NO PROMPT 
    -	 cat id_rsa.pub
    	- COPIAR A CHAVE QUE APARECE (UM TEXTO GIGANTE COM UM MONTE DE CARACTERES MISTURADOS)
    	- ADICIONAR ESSA CHAVE EM SETTINGS DO GITHUB NEW SSH KEY
    	- DAR UM NOME (NÃO IMPORTA MT ESSE NOME) E COLAR A CHAVE NO CAMPO

## LIGANDO REPOSITORIO LOCAL A UM REMOTO
    - COMO NOSSO REPOSITORIO LOCAL E REMOTO JÁ EXISTEM, BASTA DIGITAR NO PROMPT
    	- git remote add origin <caminho do repositorio>
    - EX (https):
    	- git remote add origin https://github.com/dev-michael-lourenco/curso-git-github.git
    - EX (ssh):
    	- git remote add origin git@github.com:dev-michael-lourenco/curso-git-github.git 
    - EM SEGUIDA
    	- git push -u origin master

### ENVIANDO MUDANÇAS PARA UM REPOSITÓRIO REMOTO
    - APOS REALIZAR O COMMIT
    	- git push origin <branch> 
    - EX
    	- git push origin master

### CLONANDO REPOSITORIOS REMOTOS
    - git clone <caminho do repositorio>
    - EX (ssh):
    	- git clone git@github.com:dev-michael-lourenco/curso-git-github.git 

### FAZENDO FORK DE UM PROJETO
    - o fork pega um projeto que não é seu e faz uma cópia pra você
    - ai você faz a mudança e envia um pull request informando o que alterou
    - a diferença do clone é:
    	- você só consegue enviar alterações feitas para um repositório próprio
    	- com o fork você pode enviar as alterações para submeter a mesma para o dono do repositorio original, ou seja, você pode até clonar um repositório de terceiro, mas as alterações não serão realizadas no projeto principal, a não ser que você tenha feito um fork e, atraves dele, envie estas mudanças para submeter a análise do dono do repositório principal


# SEÇÃO 5: RAMIFICACAO ( BRANCH)
    
## O QUE E UM BRANCH E POR QUE USAR?
	O branch é um ponteiro móvel que leva a um commit 
## POR QUE USAR UMA BRANCH?
        - Poder modificar os arquivos sem alterar o local principal (master)
        - Facilmente "desligável"
        - Múltiplas pessoas trabalhando
        - Evita conflitos

### CRIANDO UM BRANCH
    - git checkout -b <nome da branch>
    -EX:
    	- git checkout -b teste

### VERIFICAR EM QUE BRANCH ESTOU
    - git branch

### MOVENDO E DELETANDO BRANCH
    - Para mudar de branch
    	- git checkout <nome da branch>
    - EX:
    	- ir da branch "master" para a branch "teste"
    	- git checkout teste
    - Para deletar
    	- git branch -D < nome da branch>
    - EX:
    	- git branch -D teste

## ENTENDENDO O MERGE
    - Cria um novo commit e junta as outras branchs num ciclo ou forma diamante
    - Sempre que criar um merge, ele criar um branch separado para unir os outros branches

### PROS
    - Operação não destrutiva
    - Não mexe no histórico

### CONTRAS
    - Cria um commit extra cujo unico sentido de existir é fazer a união dos branches
    - Histórico poluído

## ENTENDENDO O REBASE
    - Move para frente da branch que ele esta enviando, pegando tudo que ele tinha no branch separado e bota no inicio da fila do novo branch (fast foward).
    - Assim, tanto a branch que fez o rebase como a que recebeu o mesmo, estarão apontando para o mesmo commit, mantendo a linearidade do historico

### PROS
    - Evita commits extras
    - Historico linear

### CONTRAS
    - Perde ordem cronologica
    - Mudanca de historico

### RESUMO DAS DIFERENCAS
    - O merge cria um novo commit para juntar as diferenças (MANTEM HISTORICO LINEAR)
    - O rebase joga as mudanças para o início da fila       (MANTEM ESTRUTURA LINEAR)

## MERGE E REBASE NA PRATICA
    - MERGE
    	- git merge <nome do branch que se unira ao atual>
    - REBASE
    	- git rebase <nome do branch que se unira ao atual>


### OBSERVAÇÃO/DICA
    - No menio do desenvolvimento, tentar usar o rebase
    - No final quando for unir, usar o merge

# SECAO 6: EXTRAS

### CRIANDO O .GITIGNORE
    - o que você não quer usar para o repositório

### GIT STASH
    - Guarda modificações que ainda não foram comitadas num arquivo que pode ser chamado depois, quando for necessário
    - git stash
    - git stash list
    - git stash clear

### ALIAS
    - EX:
    	- git config --globa alias.s status

### VERSIONAMENTO COM TAGS
    - EX:
    	- git tag -a 1.0.0 -m "A mensagem que voce quiser"
    	- Depois envia 
    	- git push origin master --tags

### GIT REVERT
    - EX:
    	- git revert ae95356d93fbc9ff1006bfb716044d0cbf7885ea

## APAGANDO TAGS E BRANCHS REMOTOS

### APAGANDO TAGS REMOTAS
    - git push origin :<nome da tag>
    - EX:
    	- git push origin :1.0.0

### APAGANDO BRANCHES
    - git push origin :<nome da branch>
    - EX:
    	- git push origin :teste    

