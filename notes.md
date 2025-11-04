#04/11/2025

Curso de Git e GitHub: dominando controle de versão de código

@01-Analisando mudanças

@@01
Apresentação

Transcrição

Boas-vindas à Alura! Sou o instrutor Vinícius Dias e irei orientar você neste curso sobre Git e GitHub, onde iremos nos aprofundar ainda mais nos conhecimentos.
Antes de falar sobre o que iremos aprender, vou me descrever por motivos de acessibilidade.

Audiodescrição: Vinícius descreve a si mesmo como um homem de pele clara, cabelos escuros e curtos, com um bigode e cavanhaque. Ele está vestindo uma camisa preta com o logo da Alura Escola de Programação.
Para quem é este curso?
Este curso é destinado a você que já tem alguma familiaridade, já conhece um pouco de Git, já aprendeu no nosso curso inicial de Git, mas deseja se aprofundar e aprender mais sobre colaboração utilizando uma ferramenta de controle de versão.

O que aprenderemos?
Visualização de alterações;
Branches;
manipulação de alterações no projeto;
tags;
comandos específicos do Git.
Neste curso, iremos abordar uma variedade de conceitos, incluindo branches (ramificações), Git Merge e Git Rebase. Nos aprofundaremos significativamente no tema do Git, explorando diversas facetas. Começaremos discutindo métodos para visualizar alterações, seja através do uso de parâmetros no git log, examinando detalhes de commits específicos ou comparando diferenças entre commits.

Depois, vamos discutir sobre o conceito de branch: o que é um branch, como utilizar branches, como unir branches, separar branches e etc. Após aprendermos bastante sobre branches, vamos trabalhar um pouco guardando alterações para depois, desfazendo alterações, basicamente manipulando o que temos no nosso projeto.

A partir desse ponto, exploraremos o uso de tags, criaremos uma versão e faremos uma release no GitHub. Abordaremos alguns detalhes sobre as tags e, por fim, discutiremos alguns comandos mais específicos, como buscar um commit específico em nossa branch e identificar o autor de uma determinada linha em nosso arquivo.

É fundamental destacar que durante este curso, faremos uso extensivo do terminal. Portanto, é essencial que você se sinta confortável navegando nele, pois ocasionalmente precisaremos alternar entre diferentes comandos. Embora não nos aprofundemos em comandos complexos, limitando-nos a executar apenas comandos do Git, é importante que você se sinta confiante ao executá-los.

Além disso, esperamos que você aproveite ao máximo este curso. Se surgir alguma dúvida durante o processo, não hesite em iniciar uma discussão no fórum ou no nosso servidor do Discord. No Discord, as discussões tendem a ser mais dinâmicas, garantindo que suas dúvidas sejam prontamente respondidas.

Novamente, boas-vindas! Esperamos que você aproveite ao máximo, e aguardamos você no próximo vídeo para começarmos a digitar comandos relacionados ao Git.

@@02
Preparando o ambiente

Este curso é uma continuação do curso Git e GitHub: compartilhando e colaborando em projetos, então nós vamos partir do ponto onde paramos nele.
Caso você não tenha feito o curso anterior, será necessário clonar o repositório do curso para que todo o histórico de commits exista em seu ambiente local. Para isso, acesse o repositório do instrutor Rodrigo Ferreira e clique no botão “Fork”. Isso criará uma cópia do repositório em sua conta. Com isso, você pode executar o git clone informando o endereço do seu repositório.

Agora você já está pronto(a) para continuar com esse curso.

Bons estudos!

https://cursos.alura.com.br/course/git-github-compartilhando-colaborando-projetos

https://github.com/alura-cursos/numero-secreto

@@03
Parâmetros do log

Transcrição

Olá a todos! Boas-vindas de volta. Vamos prosseguir com o nosso projeto, aprofundando nossos conhecimentos sobre o Git.
Relembrando o que aprendemos anteriormente
No curso anterior, exploramos um comando em particular. Deixe-me abrir o terminal e executar git log.

git log
COPIAR CÓDIGO
Obtemos como retorno:

commit 237cadaa5c19dcb03263d08f97c107dc03268a7 (HEAD -> main, origin/main, origin/ HEAD)

Author: Rodrigo Ferreira <rodrigo.alura87@gmail.com>
Date: Wed Sep 6 10:31:17 2023-0300

        mudanças no titulo e gitignore

commit 16018ade439fdae0582aa0108f2a94974f9c97ec
Author: rodrigoalura87 <144138057+rodrigoalura87@users.noreply.github.com>
Date: Wed Sep 6 10:20:02 2023 -0300

        Create README.md

commit 7f69ff8220e093d2c8ad234ceec109a6e794e5f6
Author: Gabrielle Ribeiro <gabrielleribeiro2010@gmail.com>
Date: Tue Sep 5 17:43:02 2023-0300
COPIAR CÓDIGO
Com esse comando, aprendemos a visualizar nossa lista de commits, o registro de versionamento. Para sair dessa visualização do git log, simplesmente pressionamos a tecla "Q". Isso já foi abordado e assimilado.

O git log apresenta um formato bastante consistente e invariável. Sempre o enxergamos da mesma maneira: visualizamos o hash completo do commit, e sua posição no histórico, incluindo a qual branch ele pertence. Em breve, discutiremos mais sobre branches. Visualizamos o autor, a data e a mensagem desse commit.

Entretanto, às vezes, queremos verificar mais ou menos informações. Algumas IDEs podem mostrar esse log de maneira diferente. Contudo, como estamos no VSCode, que não exibe o log para nós, e é importante sabermos nos virar fora de alguma IDE, vamos entender como visualizar esse log de maneira diferente.

Alterando a visualização do log
Imagine que desejamos apenas visualizar as mensagens dos commits, de forma simplificada. Não estamos interessados em quem foi o autor do commit, em qual branch ele está, ou outros detalhes. Não desejamos verificar o hash completo do commit, apenas uma lista das mensagens, de forma mais compacta, linha por linha.

Para sair do comando git log, pressionaremos "Q". Agora, no terminal, digitaremos git log, mas com a flag --oneline.

git log --oneline
COPIAR CÓDIGO
Isso nos permitirá visualizar o log de commits de forma muito mais resumida.

237cada (HEAD -> main, origin/main, origin/HEAD) mudanças no titulo e gitignore
16018ad Create README.md
7f69ff8 Revert "removendo foto"
2ad48c0 removendo foto
7679e24 Merge branch 'main' of github.com:rodrigoalura87/numero-secreto
5bc160e deixando o jogo mais facil ainda
ea44803 Alterando limite para 40
5880fc1 Deixando o jogo mais facil
dc89722 alterando limite para 100
250c665 projeto inicial
COPIAR CÓDIGO
Com git log --oneline, teremos nosso histórico de commits exibido com os hashes reduzidos, mostrando apenas os primeiros caracteres do hash. Isso já é suficiente para identificarmos algum commit.

E apenas a mensagem do commit, por exemplo "removendo foto". Não visualizamos quem foi a autora ou o autor, em que momento isso foi feito, etc. Assim, temos uma visualização um pouco mais clara do nosso log.

Isso é bastante semelhante ao que vemos no GitHub. Vou abrir meu navegador neste projeto no GitHub. Ao clicar em "Commits" na parte direita abaixo do botão verde "Code", observamos a nossa lista de commits, algo semelhante.

Na parte direita, temos o hash de commit menor (16018ad) e a mensagem do commit, como a "Revert "removendo foto"". Claro que aqui também visualizamos a autora ou o autor e quando esse commit foi feito, mas já tem uma aparência um pouco mais semelhante, um pouco mais reduzida.

Visualizando a alteração do commit
No entanto, o oposto pode ocorrer. Estamos interessados em examinar o commit e suas alterações, não apenas sua mensagem, mas também seu conteúdo. Portanto, ao retornar ao terminal, limpamos a tela e digitamos o comando git log -p.

git log -p
COPIAR CÓDIGO
Essa opção -p vai nos fornecer, além das informações padrão, o hash completo, o autor ou autora, a data e a mensagem do commit.

O retorno abaixo foi parcialmente transcrito. Para conferi-lo na íntegra, execute o código na sua máquina
commit 237cadaa5c19dcb03263d08f9f7c107dc03268a7 (HEAD -> main, origin/main, origin/ HEAD)
Author: Rodrigo Ferreira <rodrigo.alura87@gmail.com>
Date: Wed Sep 6 10:31:17 2023 -0300

    mudanças no titulo e gitignore

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..cd78447
---- /dev/null
+++ b/.gitignore
@@ -0,0 +1 @@
+temp/
\ No newline at end of file
diff --git a/index.htmlb/index.html
index 61ff158…7eb8cc 100644
---- a/index.html
+++  b/index.html
@@ -19,7 +19,7 @@
    <div class="container_conteudo">
        <div class="container_informacoes">
            <div class="container_texto">
-			<h1>Adivinhe o <span class="container__texto-azul">numero secreto</span></h1>
+			<h1>Descubra o <span class="container__texto-azul">numero secreto</span></h1>

            <p class=texto__paragrafo>Escolha um número entre 1 a 40</p>
</div>

// retorno omitido
COPIAR CÓDIGO
Além disso, ele mostrará um diff, que é essencialmente um formato que o git utiliza para exibir as alterações de um commit específico.

Vamos entender o formato dessas alterações. Primeiramente, descemos, pressionando a tecla de seta para baixo, até a seção referente ao index.html, nosso arquivo principal, onde a maioria das alterações está ocorrendo.

Aqui, ele mostra como esse formato funciona. Ele diz que as linhas que começam com "-" (---- a/index.html), significa que foram linhas que foram removidas. E as linhas que começam com "+" (+++ b/index.html), são as linhas adicionadas.

Então, se houver alguma modificação, uma mudança em uma linha, veremos duas entradas nesse diff: uma em que a linha começa com "-" e outra em que a linha começa com "+", indicando que trocamos uma linha por outra.

Ao analisar a saída no terminal, fechamos esse menu com os arquivos para visualizar essa saída um pouco melhor. Observamos que a linha com o h1 foi alterada; portanto, foi mudado de "Adivinhe" para "Descubra". Esse é o formato diff.

Conseguimos visualizar neste commit o que aconteceu, e esse é o formato diff. Ao percorrer a lista de alterações, em cada arquivo conseguimos verificar tudo o que foi modificado.

// retorno omitido

new file mode 100644
index 0000000..46406f2
--- /dev/null
+++ b/README.md

// retorno omitido
COPIAR CÓDIGO
No README, que é um arquivo novo, ele exibe "new file" e mostra o modo de permissão desse arquivo. No entanto, essencialmente, estamos observando que este é um arquivo adicionado, não algo que modificamos. Ao contrário do index.html. Aqui, podemos visualizar em cada commit todas as alterações que foram feitas.

Em suma, temos o git log --online para visualizar o log de forma compacta. Temos também o git log -p para ver isso de forma expandida, com as alterações.
Outras formas de exibição do log
E várias outras opções também, como o git log --graph, que exibirá uma linha do nosso log, e isso será ainda mais útil quando falarmos um pouco sobre branches.

Mas, essencialmente, se percorro isso até a parte em que temos um merge, que foi feito no curso anterior, percebemos que ele representa graficamente uma linha do tempo se desviando para outro ponto e depois retornando à nossa linha principal.

Note que à esquerda há uma linha vertical, e a partir do ponto de merge, outra linha se ramifica dessa vertical, estendendo-se até o commit do Rodrigo. Isso ficará um pouco mais claro, mas com o uso de --graph, conseguimos visualizar o log de uma forma mais visual.

Há ainda uma opção interessante, que é o --pretty ou --format. Ambos são sinônimos.

git log --pretty 
git log --format
COPIAR CÓDIGO
Com --format ou --pretty, podemos exibir o commit da maneira que desejar. Por exemplo, utilizarmos --format="" e dentro das aspas digitar %H %an.

git log --format="%H %an"
COPIAR CÓDIGO
Ao pressionarmos "Enter", o hash do commit e o autor de cada commit é exibido:

O retorno abaixo foi parcialmente transcrito.
237cadaa5c19dcb03263d08f9f7c107dc03268a7 Rodrigo Ferreira
16018ade439fdae0582aa0108f2a94974f9c97ec rodrigoalura87
7f69ff8220e093d2c8ad234ceec109a6e794e5f6 Gabrielle Ribeiro
2ad48c068dc9677fb57efec70620700410f976b0 Rodrigo Ferreira
7679e2478db577be411adf8c02cac57aae6bfa3b Rodrigo Ferreira
5bc160e8a7a3b53861e2e3da1a75c23e230a3c51 Rodrigo Ferreira
COPIAR CÓDIGO
Esse --format nos permite exibir o que desejarmos desse commit.

Usando o git log --help
E como sabemos quais são as opções, de onde vem esse %H, %an? Se digitamos git log --help, temos um manual, uma ajuda desse comando. E se digitarmos /pretty formats e teclarmos "Enter".

/PRETTY FORMATS
COPIAR CÓDIGO
Em "PRETTY FORMATS", visualizamos que conseguimos escolher diversos formatos. Temos o formato de one line, short, medium, full, fuller, e aqui conseguimos colocar coisas específicas, um formato específico.

Exemplo de formato:
short
commit <hash> 
Author: <author>

<title line>
COPIAR CÓDIGO
Os placeholders para nova linha, ou então, por exemplo, mudar a cor para deixar esse log mais legível, bem formatado. Mas temos o hash do commit com %H maiúsculo, ou o hash abreviado com %h minúsculo.

Também temos o nome da autora ou do autor, que é o %an, ou o nome do autor com %aN maiúsculo, o email com %ae, a data do commit, então %aD, temos diversas informações que podemos utilizar aqui.

Portanto, se descermos nesta página de documentação, veremos que esse pretty ou format pode ser utilizado de forma bem ampla. Isso normalmente é usado quando estamos criando algum script, automatizando alguma coisa. Então, no dia a dia, não vamos utilizar tanto.

Agora, o git log --oneline e o git log -p, esses sim são comandos bastante utilizados no dia a dia.

Conclusão
Agora, sobre esse -p aqui, onde visualizamos quais arquivos foram removidos, modificados ou adicionados, como podemos verificar isso? Somente para um commit, ao invés de verificar no log.

Se desejamos visualizar, por exemplo, no último commit, o que foi feito, quais foram as alterações, como podemos verificar isso? Aprenderemos exatamente sobre esse caso no próximo vídeo!

@@04
Vendo as alterações

Transcrição

Olá, pessoal! Boas-vindas de volta.
Vamos considerar este cenário: estamos revisando nossa lista de commits ao executarmos o comando git log --oneline, por exemplo.

237cada (HEAD -> main, origin/main, origin/HEAD) mudanças no titulo e gitignore
16018ad Create README.md
7f69ff8 Revert "removendo foto"
2ad48c0 removendo foto
7679e24 Merge branch 'main' of github.com:rodrigoalura87/numero-secreto
5bc160e deixando o jogo mais facil ainda
ea44803 Alterando limite para 40
5880fc1 Deixando o jogo mais facil
dc89722 alterando limite para 100
250c665 projeto inicial
COPIAR CÓDIGO
Nosso foco está no commit denominado "removendo foto".

Analisando um commit específico
Desejamos compreender as alterações realizadas neste commit específico, independentemente de quem o tenha feito. Portanto, ao pressionarmos "Q", sairemos do registro (log) e solicitaremos ao Git que nos apresente o conteúdo e os detalhes desse commit.

Para isso, copiaremos o hash correspondente e digitaremos git show, seguido do respectivo hash.

git show {hash do commit}
git show 2ad48c0
COPIAR CÓDIGO
O comando git show nos proporcionará uma exibição semelhante ao git log -p, porém focado apenas no commit em questão, não em todo o registro:

O retorno abaixo foi parcialmente transcrito. Para conferi-lo na íntegra, execute o código na sua máquina
commit 2ad48c068dc9677fb57efec70620700410f97660
Author: Rodrigo Ferreira <rodrigo.alura87@gmail.com>
Date: Tue Sep 5 17:19:08 2023 -0300

        removendo foto

diff --git a/index.html b/index.html
index 61ff158..e993d93 100644
--- a/index.html
+++ b/index.html

// retorno omitido
COPIAR CÓDIGO
São apresentados o hash do commit, o nome do autor, a data, a mensagem de commit e o diff correspondente, que detalha as alterações realizadas. Dessa forma, podemos navegar pelo conteúdo, descendo para visualizar as mudanças específicas. Por exemplo, notamos que uma linha referente à imagem, identificada como uma tag img, foi removida de um arquivo index.html.

Agora, ao pressionarmos "Q", sairemos dessa visualização. Podemos executar novamente o comando git log --oneline. Ao visualizarmos novamente o registro, podemos selecionar o commit de "7f69ff8 Revert "removendo foto"". Para isso, digitamos git show seguido do hash correspondente.

git show 7f69ff8
COPIAR CÓDIGO
Observamos que a mesma linha foi adicionada novamente.

Observe como o comando git show é bastante simples, ele exibe o diff para nós. Novamente, basta pressionar "Q" para sair. Um detalhe interessante é que, ao digitarmos git show --help, podemos entender melhor como o comando funciona.

git show --help
COPIAR CÓDIGO
O Git segue o padrão de nome do comando seguido de --help, com isso, podemos solicitar ajuda em caso de dúvidas em um determinado comando. Obtemos como retorno:

NAME
    git-show - Show various types of objects
    
SYNOPSIS
    git show [<options>] [<object>…]
    
// retorno omitido
COPIAR CÓDIGO
Isso nos mostra que o git show espera algumas opções e objetos, como um commit, por exemplo.

Outra possibilidade é que o objeto seja algo diferente, mas para nossos propósitos, vamos focar no commit. Porém, antes de prosseguir, deixe-me explicar brevemente o formato de sinopse apresentado pelo help.

git show [<options>] [<object>…]
Sempre que algo está entre colchetes, isso indica que é opcional.

Você percebeu que apenas digitamos git show seguido pelo nome do nosso hash do commit, certo? Não especificamos nenhum opcional. Isso significa que, além das opções que já discutimos, esse objeto, o commit, também é opcional. O que isso implica? Vamos voltar ao help para esclarecer, descemos um pouco no terminal.

// retorno omitido
    
OPTIONS
<object>...
    The names of objects to show (defaults to HEAD). For a more complete list of(…) object names, see "SPECIFYING REVISIONS" section in gitrevisions(7).
    
// retorno omitido
COPIAR CÓDIGO
Se esse objeto não for informado, o help indica que ele "defaults to head" (assume o padrão como sendo o "head"). Portanto, ao pressionar "Q" para sair e digitar git log novamente, podemos destacar um detalhe interessante.

git log
COPIAR CÓDIGO
Obtemos:

commit 237cadaa5c19dcb03263d08f9f7c107dc03268a7 (HEAD -> main, origin/main, origin/HEAD)
Author: Rodrigo Ferreira <rodrigo.alura87@gmail.com>
Date: Wed Sep 6 10:31:17 2023 -0300

    mudanças no titulo e gitignore

commit 16018ade439fdae0582aa0108f2a94974f9c97ec
Author: rodrigoalura87 <144138057+rodrigoalura87@users.noreply.github.com>
Date: Wed Sep 6 10:20:02 2023-0300
COPIAR CÓDIGO
O nosso último commit, do lado do hash do commit, temos (HEAD -> main, origin/main, origin/HEAD). O que isso significa?

Primeiro, main é o nome de um branch e vamos falar sobre branch mais adiante. E esse origin, já sabemos que é o nosso repositório remoto, é lá no GitHub. Portanto, esse origin/main significa que esse commit também é onde está o nosso branch main no repositório remoto.

Basicamente, o que isso significa é que este commit representa o estado atual da nossa branch main, ou seja, é o estado atual da "main" no nosso repositório remoto.

Agora, o "HEAD" e o "origin/HEAD", que significam a mesma coisa que "HEAD" no repositório remoto, referem-se ao estado atual no repositório remoto. O que isso implica? "HEAD" representa simplesmente o último commit, ou seja, o commit atual do qual estamos trabalhando.

HEAD: commit mais recente da branch atual
Assim, como "mudanças no título e gitignore" é o último commit, ou seja, o mais recente, ele é o nosso HEAD. Portanto, HEAD é essencialmente um sinônimo, um ponteiro, um apelido para o nosso último commit, o mais recente estado do nosso projeto no momento.

Então, por que toda essa explicação sobre "HEAD"? Porque ao digitar apenas git show, sem mais nada, o Git mostrará os detalhes do último "commit".

git show
COPIAR CÓDIGO
Então, observamos aqui que o último registro de alterações (commit) foi modificado de "adivinha" para "descubra" no nosso cabeçalho (H1).

Assim, mais uma vez, o comando git show exibe os detalhes de um ou mais registros de alterações (commits), e se nenhum registro for especificado, ele por padrão seleciona o cabeçalho (HEAD), que é o último registro de alterações.

Portanto, sempre que encontrarem referências ao HEAD em documentação, artigos, textos ou similares, é bastante simples. Ele é apenas um alias para o registro de alterações mais recente da sua posição atual. Então, entendemos o funcionamento do git show. Ele exibe os detalhes do último registro de alterações ou de um registro específico.

Conclusão
Agora, uma observação interessante: se estivermos no meio de uma edição, realizando alterações, mas ainda não fizemos o registro de alterações? E queremos visualizar o que já foi alterado, o que está pronto para ser registrado.

Como podemos fazer isso? Como podemos ver as diferenças (diff) dos arquivos que ainda não foram incluídos no registro de alterações (commit)? Vamos abordar isso no próximo vídeo.

@@05
Próximas alterações

Transcrição

Olá, pessoal! Já nos familiarizamos um pouco mais com o log e aprendemos sobre o git show. Agora, queremos levantar o seguinte cenário.
Explorando outros comandos
Primeiro, vamos abrir o terminal e digitar git status.

git status
COPIAR CÓDIGO
Obtemos como retorno:

On branch main
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean
COPIAR CÓDIGO
Este comando nos indica em qual ramificação (branch) estamos - abordaremos isso em breve - e se há algo para adicionar e realizar um commit. Vamos fechar o terminal. No arquivo index.html, renomeamos "JS Game" para "Jogo em JS".

index.html
<!-- código omitido -->

    <link rel="stylesheet" href="style.css">
    <title>Jogo em JS</title>
</head>

<!-- código omitido -->
COPIAR CÓDIGO
Salvamos este arquivo.

Ao retornar ao terminal, digitamos git status novamente.

On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified: index.html

no changes added to commit (use "git add" and/or "git commit -a")
COPIAR CÓDIGO
Neste git status, encontramos "Changes not staged for commit", ou seja, modificações que ainda não foram adicionadas para realizar o commit. Aqui há apenas uma modificação, fácil de visualizar.

Em um contexto mais prático, como trabalhar em equipe em um projeto de grande escala, é comum realizar alterações em vários arquivos. Ao concluir as modificações no último arquivo, é natural desejar revisar todas as mudanças antes de confirmar o commit, garantindo assim sua correção. Essencialmente, o objetivo é visualizar todas as alterações antes de prosseguir com o commit.

Usando o git diff
Para isso, é possível utilizar o comando git diff, que já é familiar.

git diff
COPIAR CÓDIGO
Ao executar git diff, são exibidas as diferenças entre dois estados.

O retorno abaixo foi parcialmente transcrito.
diff --git a/index.html b/index.html
index 7eb8bcc..c5d087d 100644
a/index.html
+++ b/index.html
@@ -10,7 +10,7 @@
    <link href="https://fonts.googleapis.com/cssfamily=Chakra+Petch:wght@700&family=…splay=swap"
        rel="stylesheet">
    <link rel="stylesheet" href="style.css">
-  <title>JS Game</title>
+  <title>Jogo em JS</title>
COPIAR CÓDIGO
Por padrão, os estados comparados são as modificações que foram realizadas e ainda não foram adicionadas ao commit, e o último commit realizado, também conhecido como head. Esse comando exibe a diferença entre o último commit e o que temos modificado no arquivo. No nosso caso, é apenas a alteração do title

Portanto, com o git diff conseguimos visualizar a diferença entre os dois estados.

Vamos voltar para aquela documentação digitando git diff --help.

git diff --help
COPIAR CÓDIGO
Obtemos como retorno:

O retorno abaixo foi parcialmente transcrito.
NAME
    git-diff - Show changes between commits, commit and working tree, etc

SYNOPSIS
    git diff [<options>] [<commit>] [--] [<path>...]
    git diff [<options>] --cached [<commit>] [--] [<path>...]
    git diff [<options>] <commit> <commit> [--] [<path>...]
COPIAR CÓDIGO
Ao utilizar o comando --help, ele exibe as alterações, diferenças entre commits, diferenças entre um commit e o projeto de trabalho (working tree), e assim por diante. Em resumo, ele mostra as diferenças entre dois estados distintos.

Por padrão, o Git compara o último commit com o estado atual do código, mas é possível especificar outras opções, como o commit com o qual deseja-se fazer a comparação.

Teclamos "Q" para sair.

Para visualizar as mudanças entre os commits "deixando o jogo mais fácil" e "deixando o jogo mais fácil ainda" enquanto usamos o comando git log --oneline, observamos que existe um commit intermediário entre eles.

237cada (HEAD -> main, origin/main, origin/HEAD) mudanças no titulo e gitignore
16018ad Create README.md
7f69ff8 Revert "removendo foto"
2ad48c0 removendo foto
7679e24 Merge branch 'main' of github.com:rodrigoalura87/numero-secreto
**5bc160e deixando o jogo mais facil ainda**
ea44803 Alterando limite para 40
**5880fc1 Deixando o jogo mais facil**
dc89722 alterando limite para 100
250c665 projeto inicial
COPIAR CÓDIGO
Desejamos analisar a diferença entre eles.

Para analisar a diferença entre esses dois commits específicos, precisamos incluir os três commits em nossa análise. Podemos fazer isso utilizando o comando git diff.

Primeiro, copiamos o hash do commit mais antigo que desejamos comparar, que é o "deixando o jogo mais fácil", e depois colamos esse hash seguido de "..": git diff 5880fc1... Em seguida, copiamos o hash do commit mais recente que queremos comparar, que é o "deixando o jogo mais fácil ainda", e o colamos após "..".

git diff 5880fc1..5bc160e
COPIAR CÓDIGO
O comando completo fica git diff, o commit mais antigo, "..", o commit mais novo. Ao teclarmos "Enter", ele mostra todas as alterações.

O retorno abaixo foi parcialmente transcrito. Para conferi-lo na íntegra, execute o código na sua máquina
diff --git a/app.js b/app.js
index d9966e1..c4aa249 100644
--- a/app.js
+++ b/app.js
@@ -1,5 +1,5 @@ 
    let listaDeNumerosSorteados = [];
-let numeroLimite = 50;
+let numeroLimite = 30;
    let numeroSecreto = gerarNumeroAleatorio();
    let tentativas = 1;
COPIAR CÓDIGO
Obervamos que mudamos o número de limite de 50 para 30, alteramos o texto na "Escolha um número entre 1 e 30", alteramos de 50 para 30.

O retorno abaixo foi parcialmente transcrito. Para conferi-lo na íntegra, execute o código na sua máquina
- <p class="texto_paragrafo">Escolha um número entre 1 a 50</p>
+ <p class="texto__paragrafo">Escolha um número entre 1 a 30</p>
COPIAR CÓDIGO
Então, visualizamos que entre esses commits, que são três aqui, "deixando o jogo mais fácil", tem um commit no meio e "deixando mais fácil ainda", conseguimos verificar todas as modificações feitas de uma vez só, conseguimos unificar esse diff.

Isso se torna especialmente interessante quando há necessidade de comparar o trabalho em dois estados distintos.
Vamos recapitular.

Recapitulando
O comando git diff, por padrão, compara as modificações que foram feitas mas ainda não foram adicionadas para serem commitadas, mostrando a diferença entre o estado atual do projeto e o último commit.

Quando utilizamos git add em um arquivo, como por exemplo index.html (git add index.html), e em seguida executamos git diff, percebemos que não é mais exibido nenhum resultado. Por quê?

git add index.html
git diff
COPIAR CÓDIGO
Ao executar git status, observamos que o arquivo index.html já foi adicionado e está pronto para ser commitado.

Retorno do comando git status:

On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
    (use "git restore --staged <file>..." to unstage) 
        modified: index.html I
COPIAR CÓDIGO
Ou seja, ele está em um estado que chamamos de stage (palco), ou seja, ele foi colocado em um local onde os commits são realizados.

Portanto, o arquivo não está mais no estado anterior, fora do stage, onde o diff normalmente aponta. Assim, o comando git diff não mostrará mais diferenças para esse arquivo. Se rodarmos o git diff, não obtivemos nenhum retorno.

Realizando o commit
Agora estamos prontos para realizar o commit dele. Vamos incluir uma mensagem indicando "alteração do título para português".

git commit -m "Mudando o título para português"
COPIAR CÓDIGO
Obtemos a mensagem de confirmação como retorno:

[main 39dd858] Mudando o titulo para portugues 
1 file changed, 1 insertion(+), 1 deletion(-)
COPIAR CÓDIGO
Se executarmos git diff neste momento, com nenhum arquivo no stage, nenhum arquivo preparado após o git add, e nenhum arquivo modificado em nosso projeto, ele não mostrará nenhuma diferença. Isto é, não retorna nada.

Porém, podemos utilizar novamente o comando git log --oneline.

39dd858 (HEAD -> main) Mudando o titulo para portugues
237cada (origin/main, origin/HEAD) mudanças no titulo e gitignore
16018ad Create README.md
7f69ff8 Revert "removendo foto"
2ad48c0 removendo foto
7679e24 Merge branch 'main' of github.com:rodrigoalura87/numero-secreto
5bc160e deixando o jogo mais facil ainda
ea44803 Alterando limite para 40
5880fc1 Deixando o jogo mais facil
dc89722 alterando limite para 100
COPIAR CÓDIGO
Podemos visualizar a diferença entre os dois pontos.

Então, estamos interessados em identificar as diferenças desde a criação do readme até o nosso último commit. Para isso, utilizamos o comando git diff. Copiamos o registro "Create README.md" e o colamos.

git diff 16018ad
COPIAR CÓDIGO
Agora, neste último ponto, notamos que apenas um commit foi realizado:

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..cd78447
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1 @@
+temp/
\ No newline at end of file
diff --git a/index.html b/index.html
index 61ff158..c5d087d 100644

// retorno omitido
COPIAR CÓDIGO
Quando há apenas um commit no diff, ele compara com o último commit, ou seja, com nosso head atual. Descemos um pouco mais o retorno.

Dessa forma, podemos observar a alteração no título feita no último commit, a mudança de "adivinha" para "descubra" no commit anterior, e essas são as duas modificações entre a criação do readme e nosso head atual.

Então, essencialmente, o comando git diff revela a diferença entre dois estados. Por padrão, ele compara o último commit com as alterações presentes no momento atual, mas também podemos especificar a diferença entre dois commits, ou entre um commit e o estado atual do projeto, ou seja, nosso head.

Dessa forma, podemos sempre visualizar as discrepâncias entre dois momentos distintos.

Conclusão
Em algumas ocasiões, mencionamos o termo branch.

Agora é hora de compreender o significado de branch, assim como o que representa essa referência à main quando executamos git status. Portanto, primeiro realizaremos um git push origin main e, em seguida, no próximo vídeo, nos aprofundaremos no entendimento do conceito de branch.

@@06
Diff vs Show

Ao explicar para uma pessoa de sua equipe que o git permite visualizar o que foi alterado nos arquivos do projeto, os comandos git diff e git show foram citados e você precisa explicar a diferença entre ambos.
Qual a diferença entre o comando git diff e o comando git show?


O comando git show mostra a diferença entre 2 pontos enquanto o git diff mostra o que foi alterado em um commit.
 
Alternativa incorreta
Enquanto o git show mostra o trabalho realizado em um commit específico, o git diff mostra o trabalho realizado no último commit.
 
Alternativa incorreta
Ambos os comandos são sinônimos e realizam exatamente a mesma tarefa.
 
Alternativa incorreta
O comando git show mostra o que foi alterado em um commit enquanto o git diff mostra a diferença entre 2 pontos.
 
Quando digitamos git diff sem parâmetros adicionais, visualizamos as diferenças entre o que não foi adicionado à staging area (ou seja, quando não foi feito o git add) e o último commit. Já com o git show, também sem parâmetros adicionais, podemos visualizar o trabalho que foi realizado no último commit.
Parabéns, você acertou!

@@07
Faça como eu fiz: visualizando alterações e o histórico do projeto

Nesta aula, aprendemos a visualizar o que já foi feito em nosso projeto, seja analisando o log de commits ou observando alterações específicas.
Agora é sua vez! Chegou a hora de você praticar os comandos do git que exibem o que já foi realizado no projeto.

Já teve a chance de praticar os comandos necessários para exibir o que foi realizado no projeto? Oferecemos algumas sugestões na seção Opinião do instrutor.

Opinião do instrutor

1 - Para começar a explorar os comandos que exibem a visualização de alterações no projeto, utilize o comando git log com os seguintes parâmetros:
a) -p para visualizar as alterações em cada arquivo modificado;
b) --oneline para visualizar cada commit de forma resumida em uma única linha;
c) --graph para visualizar a linha do tempo dos commits com suas ramificações;
d) --pretty ou --format para especificar com detalhes o que será exibido.
2 - Na sequência, execute git show para visualizar o trabalho realizado em algum commit específico. Lembre-se que se não for informado algum commit, o último commit será exibido.

3 - Por fim, com git diff, exiba a diferença entre 2 pontos da linha do tempo de nosso repositório. Caso nenhum parâmetro seja passado para o comando, a diferença exibida será entre o último commit e o que ainda não foi adicionado com git add.

Se surgirem dúvidas, não hesite em recorrer ao nosso Fórum.

@@08
O que aprendemos?

Nesta aula, nós:
Aprendemos sobre parâmetros adicionais do git log para alterar sua forma de exibição;
Conhecemos o comando git show, que nos exibe os detalhes de um commit específico;
Utilizamos o comando git diff para visualizar as diferenças entre dois pontos no histórico de nosso repositório git.

