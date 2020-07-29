# CUSRO GIT E GITHUB

# SECAO 1: ENTENDENDO GIT E GITHUB

# INTRODUÇÃO

# CONTROLE DE VERSÃO

# DIFERENCAS ENTRE GIT E OUTROS 
 	# OUTROS GUARDAM A DIFERENCA DOS ARQUIVOS DAS VERSÕES

# GIT GUARDA O ESTADO 

# HISTORIA DO GIT
	# CONTROLE DO KERNEL DO LINUX
	# LINUS FEZ O CONTROLE DELE

# MELHORIAS
	# DESIGN
	# SIMPLES
	# RAPIDO
	# ROBUSTO
	# FACILITA TRABALHO EM EQUIPE
	# TOTALMENTE DISTRIBUIDO
	# FUNCIONA EM GRANDES PROJETOS

# O QUE É O GITHUB
	# É UM PROJETO NA NUVEM QUE VAI ARMAZENAR OS PROJETOS QUE UTILIZAM O GIT PARA VERSIONAMENTO

# SECAO 2: CONFIGURANDO O GIT

# INSTALANDO

# CONFIGURAÇÃO INICIAL

# SECAO 3:ESSENCIAL DO GIT

# INICIALIZANDO UM REPOSITORIO
	# .git - repositorio git

# USANDO O EDITOR DO TERMINAL

# CICLO DE VIDA DOS STATUS DOS ARQUIVOS
	# 4 ESTADOS[
	# UNTRACKED
	# UNMODIFIED
	# MODIFIED
	# STAGED

# DETALHANDO CICLO
	# UNTRACKED
		# ARQUIVO FOI ADICIONADO MAS AINDA NÃO VISTO PELO GIT
	#UNMODIFIED
		# QUANDO ADICIONADO AO GIT ELE RECEBE ESTE STATUS
		# EXISTE NO GIT MAS AINDA NÃO FOI EDITADO/MODIFICADO
	# MODIFIED
		# EXISTE E FOI ALTERADO
	# STAGED
		# SE VOCÊ ENVIA-LO PARA CRIAR A VERSÃO ATUAL ELE FICA COMO STAGED

# ESTADO LOGO APÓS O COMMIT
    # APÓS FAZER O COMMIT, OS ARQUIVOS VOLTAM AO ESTADO UNMODIFIED, POIS, NA VERSÃO MAIS ATUALIZADA ESTES ARQUIVOS AINDA NÃO FORAM MODIFICADOS

# O QUE SIGNIFICA COMANDO GIT ADD
    # É QUANDO VOCE INFORMA AO GIT QUE QUER INSERIR AQUELE ESTADO ATUAL DO ARQUIVO NA PRÓXIMA VERSÃO

# O QUE É O COMMIT
    # É QUANDO VOCE AVISA AO GIT: OLHA, PEGA TODOS ESTES ARQUIVOS DO REPOSITÓRIO E CRIE UMA IMAGEM DELE ( TIPO UM SNAPSHOT, UMA VERSÃO )
    # git commit -m "Add Readme.md"

# O -m SIGNIFICA MENSAGEM, O QUE ESTA ENTRE "bla bla bla"  E A MENSAGEM EM SI
    # E INTERESSANTE QUE A MENSAGEM ENVIADA SEJA DIRETA E EXPLICATIVA DO QUE FOI REALIZADO

# GIT COMMIT -AM "MENSAGEM"
    # o -am adiciona e comita ao mesmo tempo. ( une o add com o -m)

# VISUALIZANDO LOGS
    # git log

# VISUALIZANDO O DIFF
    # git diff

# DESFAZENDO COISAS
    # se nao estiver modificacdo (add)
    # git checkout <nome do arquivo>
    
    # se estiver modificado (add e pronto pra ser comitado)
    # git reset HEAD R<nome do arquivo> (tira ele do stage) 
    # em seguida
    # git checkout <nome do arquivo>

    # se já commitei
    # existem 3 tipos de reset
    # git reset --soft [destroi o commit e deixa staged]
    # git reset -- mixed [destroi o commit e volta antes do staged, ou seja, modified]
    # git reset --hard [destori o commit como se ele o que foi feito nele não existisse]

    # EX
    # 1 - usar o git log pra pegar a hash do penultimo (ou ponto) ponto onde você quer voltar. Pegar o ultimo, pois o git ira ignorar o hash após aquele, como se ele não existisse
    # 2 - git reset --soft 83a2d46465d7689438574d8c6580391df1cb12cd

# SECAO 4: REPOSITORIOS REMOTOS

# REPOSITORIOS REMOTOS
    # UTILIZAREMOS O GITHUB

# CRIANDO E ADICIONANDO UMA CHAVE SSH
    # APOS CRIAR ENTRAR NA PASTA
    # cd ~/.ssh/
    # LA ESTARAO OS ARQUIVOS [chaves]
    # id_rsa
    # id_rsa.pub [chave adicionada no github]
    # PARA VISUALIZAR A CHAVE, DIGITE NO PROMPT 
    # cat id_rsa.pub
    # COPIAR A CHAVE QUE APARECE (UM TEXTO GIGANTE COM UM MONTE DE CARACTERES MISTURADOS)
    # ADICIONAR ESSA CHAVE EM SETTINGS DO GITHUB NEW SSH KEY
    # DAR UM NOME (NÃO IMPORTA MT ESSE NOME) E COLAR A CHAVE NO CAMPO

# LIGANDO REPOSITORIO LOCAL A UM REMOTO
    # COMO NOSSO REPOSITORIO LOCAL E REMOTO JÁ EXISTEM, BASTA DIGITAR NO PROMPT
    # git remote add origin <caminho do repositorio>
    # EX (https):
    # git remote add origin https://github.com/dev-michael-lourenco/curso-git-github.git
    # EX (ssh):
    # git remote add origin git@github.com:dev-michael-lourenco/curso-git-github.git 
    # EM SEGUIDA
    # git push -u origin master
    # digitar nome de usuario
    # digitar password

# ENVIANDO MUDANÇAS PARA UM REPOSITÓRIO REMOTO
    # APOS REALIZAR O COMMIT
    # git push origin <branch> 
    # EX
    # git push origin master

# CLONANDO REPOSITORIOS REMOTOS
    # git clone <caminho do repositorio>
    # EX (ssh):
    # git clone git@github.com:dev-michael-lourenco/curso-git-github.git 

# FAZENDO FORK DE UM PROJETO
    # o fork pega um projeto que não é seu e faz uma cópia pra você
    # ai você faz a mudança e envia um pull request informando o que alterou
    # a diferença do clone é:
    # você só consegue enviar alterações feitas para um repositório próprio
    # com o fork você pode enviar as alterações para submeter a mesma para o dono do repositorio original
    # ou seja, você pode até clonar um repositório de terceiro, mas as alterações não serão realizadas no projeto principal, a não ser que você tenha feito um fork e, atraves dele, envie estas mudanças para submeter a análise do dono do repositório principal


# SEÇÃO 5: RAMIFICACAO ( BRANCH)
    # O QUE E UM BRANCH E POR QUE USAR?
        # O branch é um ponteiro móvel que leva a um commit 
    # POR QUE USAR UMA BRANCH?
        # Poder modificar os arquivos sem alterar o local principal (master)
        # Facilmente "desligável"
        # Múltiplas pessoas trabalhando
        # Evita conflitos

# CRIANDO UM BRANCH
    # git checkout -b <nome da branch>
    #EX:
    # git checkout -b teste

# VERIFICAR EM QUE BRANCH ESTOU
    # git branch

# MOVENDO E DELETANDO BRANCH
    # pra mudar de branch
    # git checkout <nome da branch>
    # EX:
    # ir da branch "master" para a branch "teste
    # git checkout teste
    # pra deletar
    # git branch -D < nome da branch>
    # EX:
    # git branch -D teste

# ENTENDENDO O MERGE
    # Cria um novo commit e junta as outras branchs num ciclo ou forma diamante
    # Sempre que criar um merge, ele criar um branch separado para unir os outros branches
# PROS
    # Operação não destrutiva
    # Não mexe no histórico
# CONTRAS
    # Cria um commit extra cujo unico sentido de existir é fazer a união dos branches
    # Histórico poluído

# ENTENDENDO O REBASE
    # Move para frente da branch que ele esta enviando, pegando tudo que ele tinha no branch separado e bota no inicio da fila do novo branch (fast foward).
    # Assim, tanto a branch que fez o rebase como a que recebeu o mesmo, estarão apontando para o mesmo commit, mantendo a linearidade do historico
# PROS
    # Evita commits extras
    # Historico linear

# CONTRAS
    # Perde ordem cronologica
    # Mudanca de historico

# RESUMO DAS DIFERENCAS
    # O MERGE CRIA UM NOVO COMMIT PARA JUNTAR AS DIFERENCAS (MANTEM HISTORICO LINEAR)
    # O REBASE JOGA AS MUDANCAS PARA O INICIO DA FILA       (MANTEM ESTRUTURA LINEAR)

# MERGE E REBASE NA PRATICA
    # MERGE
    # git merge <nome do branch q se unira o atual>



