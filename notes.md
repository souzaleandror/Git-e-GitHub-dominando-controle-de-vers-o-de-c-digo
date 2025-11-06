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

#06/11/2025

@02-Organizando o trabalho

@@01
Problemas ao colaborar

Olá! Boas-vindas a mais uma aula deste curso de Git e GitHub. Na aula anterior, entendemos como trabalhar mais com log, visualizar os detalhes de commit com show, e as diferenças entre dois estados com diff. Agora falaremos sobre colaboração e como organizamos o trabalho colaborativo.
Problemas ao colaborar
Queremos levantar um ponto para você: se realizamos, por exemplo, um push que gerou erro na aula anterior, é porque utilizamos o usuário de trabalho e não o usuário pessoal. Com o usuário correto selecionado, fizemos o push novamente.

git push origin main
COPIAR CÓDIGO
Agora vamos executar o comando abaixo:

git log --graph
COPIAR CÓDIGO
Comentamos que existe uma linha, e em alguns momentos, pode existir uma bifurcação nessa linha. Vamos entender o que é essa bifurcação?

Simulando um cenário
Imagine um cenário mais próximo da realidade, onde trabalhamos em um projeto real, grande, com vários arquivos, funcionalidades e uma equipe com diversas pessoas, e nesse trabalho, alteramos alguns arquivos. Para simular esse caso, vamos abrir outro terminal e fazer o git clone do projeto:

git clone git@github.com:CViniciusSDias/numero-secreto.git
COPIAR CÓDIGO
Em seguida, vamos acessar o projeto numero-secreto em outro lugar:

cd numero-secreto/
COPIAR CÓDIGO
Ou seja, estamos fora do Visual Studio Code, em um terminal em outro local, e vamos abrir o arquivo index.html no ambiente diferente de outro editor para modificá-lo.

vim index.html
COPIAR CÓDIGO
Feito isso, vamos remover o "em" do título "Jogo em JS"; será somente "Jogo JS".

index.html:
<title>Jogo JS</title>
COPIAR CÓDIGO
Uma vez salvo o arquivo, podemos executar o comando git status. Além disso, com o comando git diff, conseguimos visualizar o que foi alterado.

git status
COPIAR CÓDIGO
git diff
COPIAR CÓDIGO
Agora vamos adicionar o arquivo index.html, e na sequência, adicionaremos um commit chamado "Removendo palavra do título". Após o commit, faremos o push para a origin main.

git add index.html
COPIAR CÓDIGO
git commit -m "Removendo palavra do título"
COPIAR CÓDIGO
git push origin main
COPIAR CÓDIGO
Imagine que isso foi feito por uma pessoa que trabalha conosco, ou seja, outra pessoa fez o commit, o push, e está agora no repositório. Nós, ao mesmo tempo, trabalhamos em outra funcionalidade, como, por exemplo, corrigir o acento da palavra "número" na tag <h1> da linha 22.

index.html:
<h1>Descubra o <span class="container__texto-azul">número secreto</span></h1>
COPIAR CÓDIGO
Após fazer a alteração, vamos abrir o terminal no Visual Studio Code, executar o comando git diff para garantir que está tudo certo e que vamos comitar corretamente. Novamente, vamos adicionar o index.html, e adicionar o commit com a mensagem "Adicionando acento".

git commit -m "Adicionando acento"
COPIAR CÓDIGO
Fizemos o commit, mas agora, quando formos fazer o git push origin main, o Git vai rejeitar esse push, dizendo que existem atualizações feitas que ainda não estão no código.

Isso é um "problema" que já conhecemos antes, então o que precisa ser feito? Primeiro, precisamos fazer um git pull. Com isso, ele vai trazer as alterações e fazer o que ele chama de merge.

Entenderemos melhor sobre merge em breve.
git pull
COPIAR CÓDIGO
Vamos aceitar esse merge. No nosso editor, basta executar o comando :x para salvar. Assim, fizemos o merge e agora podemos fazer o push do origin main, ou seja, ele buscou as alterações que estavam no repositório, mesclou com as nossas (significado de "merge"), e agora temos o repositório atualizado. Com o repositório atualizado, podemos enviar as alterações.

Porém, já abordamos tudo isso no curso anterior e você já passou por esse problema. Tanto que, se fizermos git log --graph, temos exatamente o cenário de bifurcação que já vimos anteriormente.

git log --graph
COPIAR CÓDIGO
Por que mostramos isso de novo? Porque, novamente, pensando em um cenário colaborativo, imagine uma equipe pequena, com 10 pessoas. Imagine um projeto pequeno, com 1.000 arquivos.

Isso, em uma escala de mundo real, são coisas pequenas; uma equipe de 10 pessoas é pequena, da mesma forma que um projeto com 1.000 arquivos é pequeno. Imagine ter que lidar com essa situação toda vez que alteramos algum desses 1.000 arquivos para cada uma dessas 10 pessoas.

Toda hora terá alguém enviando modificação para o repositório, porque a cada alteração que fazemos no projeto, executamos um commit e enviamos essa alteração, para garantir que, caso nosso computador dê problema, nada seja perdido.

Há ainda outro ponto: imagine que estamos fazendo uma alteração e estamos no processo de tornar a nossa aplicação como um todo gramaticalmente correta, então adicionamos o acento em "número", temos que verificar outros arquivos que provavelmente têm a palavra "número" sem acento, e assim por diante.

Com isso, podemos ter vários commits nessa funcionalidade, isto é, uma única funcionalidade pode conter vários commits.

Imagine que corrigimos a palavra "número" e fizemos o push para enviar a alteração para o repositório remoto. Assim, todas as pessoas que utilizarem esse repositório, irão visualizar a alteração no meio do caminho. Ainda não terminamos a funcionalidade, mas ela já está no repositório remoto para todos verem.

Imagine que queremos colocar isso em produção. Sempre que vamos colocar um código em produção e disponibilizar efetivamente esse projeto para o mundo ver, ele deve estar pronto, no estado completo.

Portanto, se estamos no meio de uma alteração, não podemos fazer o deploy (implantação), não podemos colocar esse projeto no ar.

Sendo assim, alguém que desenvolvia outra funcionalidade, agora precisará nos esperar terminar essa funcionalidade para colocar a dela no ar, porque também enviamos metade de uma alteração.

Conclusão
Perceba que se todas as pessoas estiverem trabalhando na mesma linha de trabalho, no mesmo local, temos vários problemas: um problema organizacional, onde as funcionalidades estarão todas juntas no mesmo lugar; o problema de sempre precisar fazer a mescla dos trabalhos de outras pessoas com os nossos; entre outras questões.

Há alguns problemas ao colaborar dessa forma. Por isso, vamos entender como separar linhas de trabalho, ou seja, como ramificar nossas alterações através de branches no Git. É isso que vamos abordar no próximo vídeo!

@@02
Ramificando o trabalho

Transcrição

Olá! Boas-vindas de volta. Já entendemos o problema de realizar commits no mesmo local. Se todos realizarem push para os commits no mesmo local, teremos problemas ao colaborar.
Por isso, queremos te mostrar um site interessante chamado Visualizing Git (Visualizando Git). Nesse site, como o próprio nome diz, conseguimos visualizar como o Git funciona.

Conhecendo o Visualizing Git
Por padrão, temos um único commit chamado first commit. Repare que temos um master, que no nosso caso, chamamos de main; e o HEAD é exatamente o último commit, que está no mesmo lugar.

No Visualizing Git, podemos executar o comando abaixo:

git commit -m "Teste"
Com isso, será adicionado um novo commit chamado "Teste". Podemos adicionar alguns commits, inclusive sem mensagem, apenas utilizando o comando git commit.

git commit
Ramificando o trabalho
Temos nosso projeto desenvolvido e queremos começar a trabalhar em outra funcionalidade. Para isso, podemos criar uma ramificação, um galho na nossa árvore. Isso é o que chamamos de branch.

Se digitarmos o comando git branch no Visualizing Git, ele vai mostrar quais são as branches, isto é, quais são as ramificações existentes no nosso trabalho.

git branch
Por padrão, só temos a branch main, que o Visualizing Git chama de master. Antigamente, a branch principal se chamava master, mas essa nomenclatura padrão foi alterada para main. Sendo assim, hoje em dia, a branch padrão se chama main.

Se quisermos renomear a master para main, usamos o comando abaixo:

git branch -m master main
Se quisermos remover alguma branch, caso tenhamos uma lista de várias branches, podemos usar o comando git branch -d seguido do nome da branch que queremos remover. Por exemplo:

git branch -d master
Criando uma nova ramificação
Em vez de renomear ou remover, queremos criar uma nova ramificação, ou seja, uma nova linha de trabalho, para que possamos criar essa nossa nova funcionalidade.

Vamos chamar essa nova linha de trabalho de gramatica. Para isso, basta digitar o comando git branch seguido do nome do ramo que queremos trabalhar. Esse ramo, ou seja, essa branch será criada sem espaço, maiúsculas e acentos, porque é uma identificação de algo.

git branch gramatica
Agora, se fizermos um novo commit, ele será feito na branch master, onde estamos no momento, ou na branch gramatica? Vamos fazer esse commit com a mensagem "Onde estou".

git commit -m "Onde estou"
Perceba que foi feito o commit na branch master. Não fizemos na branch gramatica, porque o local de trabalho do projeto está na branch master. Se quisermos modificar a branch atual para outra, precisamos de algum comando, e existem alguns para isso.

Alternando entre branches
Primeiro, vamos mostrar um comando antigo, depois falamos sobre o mais novo. Inicialmente, digitaremos um comando chamado git checkout. O comando git checkout faz um monte de coisa. Nesse caso, se passarmos o nome de uma branch, ele vai alterar onde estamos.

git checkout gramatica
Ao fazer isso, repare que o HEAD muda de lugar e vai para baixo da branch gramatica. Isso indica que agora estamos na branch gramatica, trabalhando a partir desse commit.

Sendo assim, se fizermos um commit com a mensagem "Agora na branch certa", por exemplo, visualizaremos uma ramificação no nosso trabalho.

git commit -m "Agora na branch certa"
Agora, há duas linhas de trabalho diferentes e independentes. Portanto, podemos executar o comando branch -d master para remover a branch master se quisermos.

git branch -d master
Feito isso, a branch master não existirá mais. Podemos fazer o git checkout para a branch main e adicionar alguns commits com o comando git commit sem mensagem.

git checkout main
git commit
Repare que temos, novamente, duas linhas de trabalho diferentes. É isso que o comando git log --graph mostrou para nós anteriormente: a ramificação no nosso trabalho. Depois, podemos mesclar isso.

Criando ramificações no projeto
Agora que entendemos como funciona o processo no Visualizing Git, vamos fazer o mesmo no projeto real. Com o VS Code aberto, vamos acessar o terminal.

Se digitarmos o comando git branch, ele vai retornar que só temos a branch main:

git branch
Poderíamos usar o comando git branch seguido de uma nova branch que quisermos, referente a qualquer nova funcionalidade. Porém, se quisermos criar uma branch e já mover para ela, podemos usar dois comandos. O primeiro é o git checkout -b seguido do nome da nova branch nova-funcionalidade.

git checkout -b nova-funcionalidade
Além desse comando mais antigo, podemos utilizar o git switch, também seguido do nome da branch desejada. "Switch" significa trocar, ou seja, esse comando basicamente alterna entre branches.

Porém, se digitarmos simplesmente git switch nova-funcionalidade, será informado que essa branch não existe. Então, vamos executar git switch -c nova-funcionalidade (-c referente a "create").

git switch -c nova-funcionalidade
Agora temos uma nova ramificação do nosso trabalho. Podemos fechar o terminal e adicionar alguma modificação no código do arquivo index.html. Por exemplo: vamos adicionar uma quebra de linha na imagem (<img>) da linha 32, logo antes dos atributos alt e class.

index.html:
<img src="./img/ia.png" 
     alt="Uma pessoa olhando para a esquerda"
     class="container__imagem-pessoa" />
Essa é a nova funcionalidade que desenvolvemos, com alterações no código. Agora vamos abrir o terminal novamente e executar o comando git status.

git status
Com isso, ele mostra que estamos na branch nova-funcionalidade. Vamos adicionar o arquivo index.html com o comando git add, e depois adicionar um commit com a mensagem "Quebrando linha na imagem".

git add index.html
git commit -m "Quebrando linha na imagem"
Se fizermos um git log agora, temos um retorno um pouco diferente.

git log
Temos o commit anterior, do merge na branch main; temos o origin/main; agora o último commit é onde está o HEAD atual; e temos a branch nova-funcionalidade. Repare que a branch nova-funcionalidade ainda não foi para o origin, pois não enviamos.

Porém, antes de enviar, vamos fazer um switch e voltar para branch main:

git switch main
A funcionalidade que estamos desenvolvendo está nessa branch, isto é, o commit existe nela, não descartamos ele. Porém, voltamos a trabalhar na linha de trabalho principal main.

Portanto, se fechamos o terminal e acessamos a tag de imagem que alteramos no código, ela estará sem quebra de linha. Se voltarmos para o terminal e executarmos git log, o head terá voltado para main. Então, o HEAD é onde estamos no momento, é o commit atual onde o nosso projeto está.

Dito isso, vamos fazer um git switch para nova-funcionalidade:

git switch nova-funcionalidade
Mais uma vez, o código aparecerá atualizado com a quebra de linha que adicionamos. Assim, podemos fazer o git push para o repositório remoto, ou seja, origin da branch nova-funcionalidade.

git push origin nova-funcionalidade
Após teclar "Enter", a nova ramificação será criada e teremos uma nova linha de trabalho.

Conclusão
Repare que trabalhar com branches é relativamente simples. A parte complexa é entender por que fazer isso, mas já explicamos no vídeo anterior. O que ainda pode ser complexo é unir os trabalhos.

Na linha principal, alguém pode ter adicionado novos commits e novas funcionalidades. Enquanto isso, temos a linha de trabalho nova-funcionalidade, onde adicionamos as quebras de linha. Como podemos unir esses dois mundos? É sobre isso que vamos conversar no próximo vídeo!

@@03
Para saber mais: Visualizing Git

Nesta aula, utilizamos o Visualizing Git para exemplificar o comportamento do git em relação às ramificações (branches). Essa ferramenta, que funciona como um playground, simulando operações do Git, é um excelente auxílio para observar graficamente o que acontece por baixo dos panos em cada comando utilizado.
Explore também o Visualizing Git e realize os seus próprios experimentos.

https://git-school.github.io/visualizing-git/

@@04
Para saber mais: comando checkout

Nesta aula, mencionamos que o git checkout é um comando “antigo” e que há alternativas mais modernas. É importante ressaltar que o comando checkout continua funcionando e não há nenhum indício de que ele será removido do git, mas devido à sua grande complexidade, ele foi separado em dois comandos diferentes: o git switch, que também vimos nessa aula, e o git restore, que abordaremos em breve.
Você pode entender melhor a motivação por trás dessa separação e espiar um spoiler do git restore através do Alura+ Entenda os comandos git restore e switch.

https://cursos.alura.com.br/extra/alura-mais/entenda-os-comandos-git-restore-e-switch-c99

@@05
Unindo as ramificações

Transcrição

Olá! Boas-vindas de volta. Entendemos o problema que as branches (ramificações) vêm para resolver e como criar e alternar entre elas.
Note que fizemos o push de nova-funcionalidade, e no GitHub, ele exibe uma mensagem que indica que podemos criar uma pull request a partir da nossa nova branch.

O GitHub já identificou que existe uma nova branch e que, em algum momento, vamos querer unir a branch nova-funcionalidade com a main, que é a branch principal.

Vamos deixar um Para saber mais sobre pull requests quando colaboramos, por exemplo, em um projeto open source (de código aberto), ou até se colaboramos com uma equipe que utiliza GitHub.
Basicamente, queremos unir o trabalho da branch nova-funcionalidade à branch main.

Unindo as ramificações
Não precisamos utilizar o GitHub para esse objetivo, então vamos acessar o Visualizing Git. Em uma nova linha de trabalho, vamos adicionar dois commits com o comando git commit, criar a branch nova-funcionalidade com o comando git checkout -b, e adicionar mais dois commits a essa nova branch.

git commit
COPIAR CÓDIGO
git checkout -b nova-funcionalidade
COPIAR CÓDIGO
Em seguida, vamos fazer um git switch para a branch master:

git switch master
COPIAR CÓDIGO
Queremos pegar tudo o que foi feito em nova-funcionalidade e trazer para o ramo principal master. Existe um comando que faz isso de forma bastante simples: o git merge ("mesclar" em inglês).

Você se lembra que quando fizemos o pull e o push com dois usuários diferentes, chegamos nesse cenário de merge, isto é, de mescla de trabalhos? Podemos fazer isso ativamente.

Podemos dizer que estamos na branch main, a branch principal, pegar tudo o que tem na branch nova-funcionalidade e mesclar com o que já temos na main.

Se fizermos o merge de nova-funcionalidade, ele vai levar a main para o mesmo local.

git merge nova-funcionalidade
COPIAR CÓDIGO
O que é fast forward?
Existem algumas formas do merge ser feito. Nesse caso, ele executou o que é chamado de fast forward (mover adiante). Até o ponto da nova-funcionalidade ser criada, a master estava no terceiro commit. A partir desse ponto, criamos uma nova branch, e a branch nova-funcionalidade evoluiu na mesma linha, sem que a master tivesse novos commits.

Então, na hora de fazer o merge, é muito simples: não precisamos criar nenhum novo commit; o Git entende tudo e só move as coisas. Se queremos unir as coisas, a partir de agora, a branch principal estará no mesmo ponto que a nova-funcionalidade. Isso é o chamado fast forward.

Vamos fazer isso no terminal do Visual Studio Code. Começaremos fazendo o git switch para a branch principal main, e faremos um merge com nova-funcionalidade.

git switch main
COPIAR CÓDIGO
git merge nova-funcionalidade
COPIAR CÓDIGO
Com isso, ele fará exatamente o que dissemos: o fast forward. Isso quer dizer que ele não cria um novo commit, nem faz nada de diferente; ele simplesmente diz que, a partir de agora, a branch main está no mesmo lugar que a branch nova-funcionalidade.

Se executarmos o comando git log --graph, notaremos que não precisamos de uma nova ramificação.

git log --graph
COPIAR CÓDIGO
Realizando alterações
Vamos voltar para a branch nova-funcionalidade e alterar algo no código.

git switch nova-funcionalidade
COPIAR CÓDIGO
Podemos acessar o arquivo README.md, por exemplo, e fazer alguma alteração simples. Nesse caso, vamos adicionar uma quebra de linha entre cada uma das imagens a partir da linha 8.

README.md:
## 🚀 Tecnologias
<div>
  <img src="https://img.shields.io/badge/HTML-239120?style=for-the-badge&logo=html5&logoColor=white">

  <img src="https://img.shields.io/badge/CSS-239120?&style=for-the-badge&logo=css3&logoColor=white">

  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">
</div>
COPIAR CÓDIGO
Novamente, o comando git status vai nos mostrar que estamos na branch nova-funcionalidade:

git status
COPIAR CÓDIGO
Vamos adicionar o arquivo README.md com o comando git add e, na sequência, adicionar um novo commit com a mensagem "Quebra de linha entre imagens". Podemos até fazer o git push de nova-funcionalidade para ir ao repositório remoto.

git add README.md
COPIAR CÓDIGO
git commit -m "Quebra de linha entre imagens"
COPIAR CÓDIGO
git push origin nova-funcionalidade
COPIAR CÓDIGO
Feito isso, vamos voltar para a branch main.

git switch main
COPIAR CÓDIGO
Imagine que outras funcionalidades estão acontecendo e outras pessoas estão desenvolvendo. Dito isso, vamos ao arquivo style.css, por exemplo, e mudaremos a propriedade font-size da tag h1 de 50px para 51px, dentro do @media screen na linha 116.

style.css:
@media screen and (max-width: 1250px) {

    h1 {
        font-size: 51px;
    }
COPIAR CÓDIGO
Suponha que outras pessoas estão trabalhando e vão adicionar essa modificação na branch principal main. Pense que elas já fizeram o trabalho delas em outra branch e mesclaram com a main.

É isso que vai acontecer: vamos adicionar o arquivo de estilo com o comando git add, e a mensagem do commit será "Aumentando a fonte".

git add style.css
COPIAR CÓDIGO
git commit -m "Aumentando a fonte"
COPIAR CÓDIGO
Agora, se executarmos o comando git log, temos o commit "Aumentando a fonte". Se alternarmos para a branch nova-funcionalidade com git switch, e executarmos novamente git log para verificar o que temos em nova-funcionalidade, o commit "Aumentando a fonte" não fará parte dessa linha de trabalho.

Fazendo um merge commit
Estamos no cenário onde as duas branches evoluíram de forma independente. Este é o cenário mais comum: trabalhamos na branch de alguma funcionalidade, e outras funcionalidades foram adicionadas à main, outras coisas foram feitas e já estão na linha de trabalho principal.

Sendo assim, quando fizermos um git switch para main e tentarmos fazer um git merge de nova-funcionalidade, o Git vai entender que esses dois trabalhos estão independentes e não evoluíram de forma igual. Dessa forma, ele irá unir criando um novo commit automaticamente. Ele criará um novo commit de merge, ou merge commit, como normalmente é chamado nas documentações.

git switch main
COPIAR CÓDIGO
git merge nova-funcionalidade
COPIAR CÓDIGO
Com esses comandos, será aberto um editor que permite a alteração da mensagem de commit de merge. No nosso caso, vamos deixar o commit como está.

Como o editor é o VI, basta executar :x para salvar e sair. Ao final, teremos um novo commit criado. Se executarmos o comando git log --graph, podemos observar o que acontece na main.

Primeiramente, temos o commit "Quebrando linha na imagem". Depois ele cria uma nova linha de trabalho, onde temos o commit "Aumentando a fonte". Na sequência, temos "Quebra de linha entre imagens", e por último o merge commit, isto é, o commit de mescla.

Reparem que bifurcamos o nosso trabalho e depois unimos. Lembrando que tudo isso é feito automaticamente pelo Git, mas é importante entender que existem essas duas estratégias: de fast forward e de criação do merge commit.

Dessa forma, conseguimos unir trabalho de duas branches diferentes para ter tudo na linha principal. Agora a nossa linha principal possui toda a nova-funcionalidade. O ramo nova-funcionalidade foi completo, unimos à linha principal, então agora podemos fazer deploy da nossa aplicação.

Ajustes finais
Para finalizar, vamos executar o comando git push origin main para atualizar a main com todo o trabalho novo. Em seguida, removeremos a branch nova-funcionalidade com git branch -d, para manter o projeto limpo e sem excesso de branches.

git push origin main
COPIAR CÓDIGO
git branch -d nova-funcionalidade
COPIAR CÓDIGO
Ainda podemos remover a branch nova-funcionalidade do repositório remoto no GitHub. Para isso, executamos o seguinte comando:

git push origin :nova-funcionalidade
COPIAR CÓDIGO
Os dois pontos (:) indicam que estamos removendo no repositório remoto.
Conclusão
Entendemos o motivo para ter branches, como lidar com branches e como unir o trabalho entre branches. Porém, em alguns cenários, não queremos criar o merge commit, mesmo que as duas linhas de trabalho tenham evoluído de forma individual. Vamos mostrar como reescrever a história com Git no próximo vídeo!

@@06
Para saber mais: pull requests

O GitHub possui uma funcionalidade chamada Pull requests, que é uma sugestão de alteração em determinado repositório. Outras ferramentas, como o GitLab, podem chamar essa mesma ferramenta de Merge requests.
Essa sugestão de alteração é, de forma resumida, a abordagem que adotamos ao colaborar com equipes para adicionar novas funcionalidades ou corrigir alterações. Ao invés de manualmente mesclarmos o código de nossa branch com a main, nós criamos um pull request (ou merge request), pois dessa forma a alteração fica mais visível para toda a equipe e permite que outras pessoas possam revisar esse trabalho.

Há muitas outras funcionalidades em pull requests, mas essa explicação já é um bom começo. Se você quiser ver um pull request na prática para um projeto de código aberto, no vídeo Contribuindo para projetos open source - Criando um pull request real no GitHub eu mostro exatamente isso.

https://youtu.be/cdL_F3FiSWI

@@07
Atualizando a branch

Transcrição

Já estamos começando a entender um pouco melhor sobre branches. Essa parte de mesclagens pode parecer complexa no início, então não se preocupem. Normalmente, trabalhamos com cenários mais tranquilos até evoluir para resolver conflitos maiores.
Atualizando a branch
No Visualizing Git, encontramos o cenário que reproduzimos na última aula.

Diagrama de fluxo representando o processo de controle de versão usando git, mostrando uma linha do tempo principal de commits na base com sete círculos cinza conectados por setas indicando a sequência dos commits.
Temos a branch principal, ramificamos uma nova funcionalidade, criamos dois commits e depois fizemos um merge, ou seja, um novo commit foi criado com a junção desses dois trabalhos. Basicamente, é isso que fazemos quando temos um merge, quando temos dois trabalhos bifurcados.

Agora, criaremos um novo cenário. Então, rodamos o comando clear para limpar o Visualizing Git.

clear
COPIAR CÓDIGO
Em sequencia, adicionamos uma nova branch chamada main, então passamos git checkout -b main.

git checkout -b main
COPIAR CÓDIGO
Em sequência, removemos a branch chamada master para já nos adaptarmos com os nomes corretos. Então passamos o comando git branch -d master.

git branch -d master
COPIAR CÓDIGO
Recapitulando, o git checkout é um comando antigo que faz muita coisa. Contudo, o Visualizing Git não foi atualizado para ter o comando git switch. Mas, normalmente, utilizamos o comando git switch, que é mais simples.
Continuando, adicionaremos alguns commits na branch main, faremos isso sem mensagem, só commits vazios. Passamos git commit duas vezes.

git commit
COPIAR CÓDIGO
Agora criaremos um novo branch passando git branch nova-funcionalidade.

git branch nova-funcionalidade
COPIAR CÓDIGO
Criamos um novo branch, mas ainda estamos na main, não na nova-funcionalidade. Após, adicionamos mais dois commits na branch main passando git commit.

Agora, voltamos para o git checkout nova-funcionalidade para trabalharmos nela.

git checkout nova-funcionalidade
COPIAR CÓDIGO
Em seguida adicionamos dois commits, passando duas vezes o código abaixo.

git commit
COPIAR CÓDIGO
O cenário que montamos no Visualizing Git, criamos uma nova branch chamada nova-funcionalidade e estamos trabalhando nela. Enquanto trabalho nessa branch, outras pessoas podem ter criado outros branches e já se uniram à linha principal, à main. Normalmente, essa main é o projeto final que pode ser enviado à produção. É o projeto com todas as funcionalidades que estejam completas.

Estamos criando uma nova funcionalidade, porém queremos testá-la na versão mais recente do projeto. Repare que, a partir do momento em que criamos a nova-funcionalidade, dois outros commits também foram criados, ou seja, duas funcionalidades foram adicionadas no projeto principal.

Queremos garantir que o que estamos desenvolvendo funcione, mesmo com as funcionalidades que as outras pessoas criaram. Queremos garantir que tudo se integre da forma correta.

Sendo assim, queremos fazer com que a branch nova-funcionalidade não seja criada a partir da versão antiga da branch maine sim da versão mais nova.

Portanto, queremos reescrever a história, fazendo com que o primeiro commit da nova funcionalidade venha logo após do momento atual da main atualizada. Queremos fazer com que a branch nova-funcionalidade, seja reescrito para ter todas as funcionalidades da main antes dela.

Isso pode ser feito com um comando mágico chamado git rebase, que faz muita coisa, como reescrever a história dos commits. Então, se estivermos em nova-funcionalidade e executarmos o comando git rebase main, ele pegará todos os commits da main que não estão na branch nova-funcionalidade, e tentar adicionar um a um antes da branch nova-funcionalidade.

git rebase main
COPIAR CÓDIGO
Ele pegará o primeiro commit e tentar adicionar antes do commit nova-funcionalidade. Pegará o próximo commit, que é o último da main, e tentar adicionar antes do commit nova-funcionalidade. Após isso, pega todos os commits da nova-funcionalidade e aplica depois do último da main.

Pode parecer bastante complexo, mas se visualizarmos o que está acontecendo, talvez fique um pouco mais fácil. Ele primeiro traz o head para a main e depois aplica tudo da nova-funcionalidade, cada um dos commits, depois. Vai aplicando commit a commit depois da última coisa que estiver na main.

Recapitulando novamente. Temos duas branches independentes, uma main e uma nova-funcionalidade. Se queremos garantir que essa nova-funcionalidade agora tenha tudo o que tem na main também, podemos fazer o rebase.

O rebase fará o quê? Se estamos na nova-funcionalidade e tentamos fazer o rebase com a main, ele vai alterar o branch para ir para a main. Depois da main, ele vai aplicando cada um dos commits da nova-funcionalidade. Isso é feito commit por commit, porque se tiver algum conflito em algum dos commits, vamos resolvendo um a um. Dessa forma, conseguimos reescrever a história.

Reparem que agora o nova-funcionalidade possui dois commits com hashes diferentes, porque vieram de outro lugar a partir de uma nova história. Vamos fazer isso, na prática.

Para isso, abrimos o projeto no VS Code, limpamos o terminal e passamos o comando git status.

git status
COPIAR CÓDIGO
Agora estamos na main. Então, passamos o comando git switch -c nova-funcionalidade. Vou criar mais uma nova-funcionalidade.

git switch -c nova-funcionalidade
COPIAR CÓDIGO
Agora, corrigiremos a indentação do link na linha 10 para que o atributo rel esteja na mesma coluna do meu atributo href. Fizemos uma alteração simples.

No terminal, adicionamos esse commit. Então, escrevemos git add index.html.

git add index.html
COPIAR CÓDIGO
Seguido de git commit -m "Corrigindo indentação".

git commit -m "Corrigindo indentação"
COPIAR CÓDIGO
Vamos quebrar também o <script> para que a abertura e o fechamento dessa tag fiquem em linhas diferentes.

//Código omitido

<script src="https://code.responsivevoice.org/responsivevoice.js">
</script>

//Código omitido
COPIAR CÓDIGO
Feito isso, no terminal passamos git add index.html, seguido de git commit -m "Quebrando linha do script".

git commit -m "Quebrando linha do script"
COPIAR CÓDIGO
Temos a nova-funcionalidade sendo desenvolvida. Agora, faremos o git switch para main. Imagine que alguma outra nova funcionalidade será adicionada no ramo principal.

Quebraremos a linha referente ao botão de chute para que o texto Chutar fique separado das tags de abrir e fechar <button>. Fazemos o mesmo em Novo Jogo.

//Código omitido

    <div class="chute container__botoes">
            <button onclick="verificarChute()" class="container__botao">
                Chutar
            </button>
            <button onclick="reiniciarJogo()" id="reiniciar" class="container__botao" disabled>
                Novo jogo
            </button>
    </div>
</div>

//Código omitido
COPIAR CÓDIGO
Feito isso, salvamos. No terminal, adicionamos git add index.html, seguido do git commit -m "Indentando botões".

git commit -m "Indentando botões"
COPIAR CÓDIGO
Na branch main, temos uma nova funcionalidade que indentou os botões. Se fazemos git switch nova-funcionalidade, temos a indentação das tags no início do arquivo. Só que queremos garantir que o arquivo index.html esteja correto mesmo se pegarmos tudo da última versão da main. Então, primeiro passamos o comando git log --.

git log --
COPIAR CÓDIGO
Assim é exibido que temos Corrigindo indentação, mostrando a linha do script depois do origin/main, mas não do main/local, pois tem um commit novo. Limpamos a tela e passamos o git rebase main.

git rebase main
COPIAR CÓDIGO
Isso faz um git switch para main, pega cada um dos commits que temos nessa nova-funcionalidade e tenta aplicar a partir desse novo momento. Depois, move novo branch para a nova linha. Então, fazemos o git rebase main.

git rebase main
COPIAR CÓDIGO
Repare que primeiro, estamos fazendo o rewind, ou seja, estamos voltando para o início dessa branch. Depois, estamos aplicando o commit de corrigir a indentação e aplicamos o commit de quebrando a linha do script. Deu tudo certo!

Se passarmos git log agora, reparem que o branch nova-funcionalidade começa a partir do branch main, do novo main que criamos localmente. Então, reescrevi a história. Agora, podemos fazer o git push origin main.

git push origin main
COPIAR CÓDIGO
Seguido de git push origin nova-funcionalidade.

git push origin nova-funcionalidade
COPIAR CÓDIGO
Estamos mandando tudo para o repositório remoto. Claro, podemos voltar para o git switch main e fazer um git merge nova-funcionalidade.

Com isso, ele vai conseguir fazer o fast-forward porque já fiz o rebase, então não precisa daquele commit de merge. Porque, novamente, ele já reescreveu a história garantindo que os dois branches não sejam mais separados e sim que podem estar juntos.

Reparem que quando fazemos o merge, conseguimos fazer o fast-forward. Então, agora, novamente fazemos o git push origin main que agora tem a nova-funcionalidade.

Um detalhe importante antes de finalizar e que fast-forward, commit de merge, parecem ser detalhes bem pequenos e, na verdade, são. Quando estamos trabalhando, podemos simplesmente executar o git merge sem saber se ele vai fazer o fast-forward ou se vai fazer um commit de merge.

Porém, em algumas empresas, podem ter políticas onde todos os merges precisem ser feitos com o fast-forward. Então, antes de qualquer merge, é preciso fazer um rebase.

Também pode ser o contrário, precisamos garantir que nunca utilizaremos o fast-forward para sempre ter no grafo do log as ramificações. Então, podemos utilizar estratégias para isso também.

Mas, para o nosso cenário, já é o suficiente conhecer os comandos merge para mesclar trabalhos e o comando rebase para reescrever a história e garantir que uma nova branch possa ser atualizada a partir de uma branch anterior.

Já temos bastante conteúdo sobre o trabalho com branches. Agora, falaremos sobre manipular o que temos de versão. Por exemplo, se temos um trabalho que teremos que abandonar para corrigir um bug ou situações semelhantes, como podemos guardá-lo para depois e desfazer trabalhos?

É isso que aprenderemos na aula seguinte. Até lá!

@@08
Rebase vs Merge

Você faz parte de um time de desenvolvimento em uma empresa de software que atualmente está trabalhando em uma nova aplicação de gerenciamento de projetos. A equipe utiliza o Git como sistema de controle de versão e o GitHub para hospedar os repositórios.
Recentemente, a equipe dividiu as tarefas em diferentes branches para implementar novos recursos e correções de bugs, assim cada desenvolvedor trabalhou em sua própria branch dedicada para garantir a independência do trabalho.

Mas, agora chegou o momento de integrar as alterações de diferentes branches ao branch principal, que representa a versão estável do projeto. No entanto, surgiram dúvidas sobre qual abordagem usar: merge ou rebase.

Neste cenário, qual a diferença entre esses comandos?

O merge sempre cria um merge commit ao unir o trabalho de duas branches enquanto o rebase une duas branches usando fast forward.
 
Há dois erros nessa alternativa. Primeiro, o merge nem sempre vai criar um merge commit. Inclusive a abordagem padrão é justamente de evitar merge commits fazendo o fast forward. O segundo erro é ao afirmar que o rebase une duas branches quando na verdade ambas as branches utilizadas no rebase continuam independentes. Ele apenas “reescreve a história” de uma das branches aplicando os commits de outra.
Alternativa incorreta
Ambos são sinônimos, ou seja, não há diferença.
 
Alternativa incorreta
O rebase junta os trabalhos e gera um commit de junção. O merge aplica os commits de outra branch na branch atual..
 
Alternativa incorreta
O merge junta os trabalhos de duas branches, podendo gerar um merge commit. Já o rebase aplica os commits de outra branch na branch atual.
 
O trabalho do rebase é equivalente ao que vimos na prática como fast forward do merge. Ao realizar o rebase, todos os commits da outra branch são adicionados antes do primeiro commit da nossa branch atual, reescrevendo a história. Isso faz com que novas alterações possam ser integradas à nossa branch e permite que quando formos realizar o merge, não seja necessário um merge commit, garantindo o fast forward.

@@09
Faça como eu fiz: trabalhando com branches

Nesta aula, nós aprendemos sobre um dos conceitos mais importantes quando o assunto é git: branches.
Agora é com você! Chegou a sua vez de criar e unir novas branches utilizando o nosso projeto base ou um projeto de sua preferência.

Já teve a chance de praticar os comandos necessários para criar e unir novas branches? Oferecemos algumas sugestões na seção Opinião do instrutor.

Opinião do instrutor

Execute o comando git branch para visualizar que apenas a branch main existe em seu repositório local;
Com o comando git switch -c {nome_da_branch}, crie uma nova branch. Nela você pode adicionar novos commits;
Após adicionar os commits na nova branch, volte para a main com git switch main;
Adicione novos commits na main simulando uma nova funcionalidade que foi mesclada;
Volte para a sua branch criada no Passo 2 e a atualize com git rebase main. Isso aplicará os novos commits da main no início dessa branch;
Volte para a main e mescle o trabalho com o git merge. Se quiser forçar um merge commit, mesmo sendo possível realizar o fast forward, execute git merge --no-ff {nome_da_branch}.
Se surgirem dúvidas, não hesite em recorrer ao nosso Fórum.

@@10
O que aprendemos?

Nessa aula, nós:
Entendemos o problema que branches resolvem ao colaborar com uma equipe em um projeto, organizando a colaboração, evitando conflitos e garantindo que uma funcionalidade seja enviada apenas quando estiver pronta;
Conhecemos os comandos git branch e git switch para manipular as branches existentes;
Vimos como unir o trabalho de duas branches com o comando git merge;
Aprendemos sobre as abordagens de merge commit e fast forward do git merge;
Conseguimos reescrever a história de uma branch utilizando o comando git rebase.

#06/11/2025

@03-Manipulando as versões

@@01
Guardando para depois

Transcrição

Olá, pessoal! Boas-vindas de volta a mais uma aula deste curso, onde estamos nos aprofundando nos conhecimentos de Git.
Agora, imagine o seguinte cenário: Estamos desenvolvendo uma funcionalidade grande. Estamos no meio da implementação dela, ela ainda não está pronta. No entanto, precisamos interromper o trabalho nela para resolver um bug urgente ou mudar nosso foco para alguma correção pequena que seja urgente. Ou seja, queremos interromper nosso trabalho.

Como estamos no meio de uma funcionalidade, nosso código pode não estar compilando ou não estar em um estado que possamos criar um commit.

Lembre-se: sempre criamos commits quando o nosso projeto está em um estado funcional.
Se o código está compilando, se está, pelo menos, executando da forma esperada. Portanto, não vamos criar um commit com nosso código em um estado incompleto.

O que fazemos se nos deparamos com um cenário onde estamos no meio da implementação de uma funcionalidade, mas precisamos interromper aquele processo? Vamos simular o cenário da criação de uma nova funcionalidade.

Criando uma nova funcionalidade
Primeiro, se estamos criando uma nova funcionalidade, vamos criar um novo branch. Portanto, escreveremos no terminal git switch -c movendo-detalhes.

Estamos em uma nova branch, podemos criar nossa nova funcionalidade. Abrimos então o arquivo app.js e queremos mover a chamada de função exibirMensagemInicial(), que está na linha 17 para a linha 5 para deixar a declaração das variáveis, depois a chamada de função e depois as declarações das funções.

Como podemos fazer isso? Vamos recortar a linha exibirMensagemInicial() e movê-la para cima. Só que fomos interrompidos: Um bug muito urgente surgiu, então precisamos trabalhar em outra coisa. O que acontece?

Não podemos criar um commit agora. Nosso projeto está em um estado inválido, removemos a chamada de função. Além disso, se executarmos um git status, temos modificações. Portanto, não podemos começar a trabalhar em outra coisa e ir para outro branch, porque o arquivo app.js está modificado. Precisamos desfazer essa alteração, mas guardar o que já alteramos.

Guardando as alterações feitas
O que queremos fazer é engavetar a alteração que fizemos até agora, mas sem criar um commit. Queremos guardar ela para depois, queremos estocar ela para depois poder recuperar e continuar trabalhando. E é exatamente isso que o comando git stash faz. Ele guarda uma alteração para continuarmos trabalhando nela depois.

Se executarmos o comando git stash, ele vai pegar tudo o que está no nosso estado atual e estocar. Ele vai guardar para que possamos recuperá-lo depois. Portanto, ele vai guardar essa alteração que fizemos de recortar a linha exibirMensagemInicial() e desfazê-la.

Está guardada a alteração, mas a partir disso podemos voltar a trabalhar. O git stash nos diz que salvou o nosso estado na nossa gaveta, no nosso estoque ("Saved working directory and index state WIP on movendo-detalhes: linha do script"). Portanto, se voltarmos para o nosso arquivo, repare que ele está no seu estado válido, ele voltou lá com a nossa alteração.

Digamos que já cuidamos do bug e queremos voltar para esse branch de nova funcionalidade e retomar o trabalho. Como podemos recuperar o que está no nosso stash?

Recuperando as alterações
Podemos executar o comando git stash pop. Esse pop, ele aplica o que tiver na nossa gaveta, no nosso estoque.

Após executarmos o git stash pop, a função não está mais na linha 12. Então, podemos continuar a implementação e trazê-la para cima. Agora temos o nosso estado finalizado.

Portanto, o git stash guarda uma alteração para que ela possa ser retomada depois.
Ele guarda um estado para que possamos retomá-lo depois. E normalmente é utilizado quando estamos no meio de uma alteração, queremos guardar algo rapidamente para corrigir um bug e trabalhar em outra coisa rapidamente e depois voltar a trabalhar nisso. Portanto, não podemos criar um commit.

Um detalhe: vamos criar esse stash novamente. Vamos limpar o nosso terminal e rodar o git stash. Se executarmos o comando git stash list, ele lista tudo o que está nesse nosso estoque. E repare que temos duas coisas no nosso stash, já tínhamos adicionado algo antes.

$ git stash list
stash@{0}: WIP on movendo-detalhes: c53eb16 Quebrando linha do script
stash@{1}: WIP on main: c53eb16 Quebrando linha do script
$
COPIAR CÓDIGO
Digamos que não queremos mais nada na stash. Ou então, queremos fazer o git stash pop primeiro para recuperar essa nossa alteração. Feito o git stash pop, a nossa alteração voltou a aparecer e estamos com o nosso código no estado correto.

Mas repare que os nomes que esse nosso git stash list nos mostra não são muito descritivos. Ele coloca um work in progress (WIP) na branch que estávamos e o último commit antes de adicionarmos esse stash. Portanto, isso não é muito útil.

Limpando as alterações guardadas
Vamos mostrar duas coisas. A primeira é que temos aqui no nosso git stash list algo anterior que fizemos alguns testes que não fazem parte dessa aula. Portanto, como podemos limpar a nossa stash, apagar tudo? Podemos fazer um git stash clear, limpamos a nossa stash. Portanto, se fizermos o git stash list, não tem mais nada lá.

Acrescentando uma descrição à stash
Agora, se quisermos adicionar algo a nossa stash, mas com um nome mais descritivo, podemos fazer, ao invés de só git stash, vamos escrever git stash push -m. E aí, podemos adicionar uma mensagem qualquer, será "Movendo chamada de função".

git stash push -m "Movendo chamada de função"
COPIAR CÓDIGO
Quando voltamos lá para o nosso código, a alteração foi desfeita. E se fizermos um git stash list, temos um nome bem mais descritivo: Movendo chamada de função. Agora, sabemos o que isso significa. E podemos adicionar várias coisas na stash, como mostramos.

Por exemplo, temos algo na nossa stash e vamos adicionar algo mais. Como, por exemplo, vamos remover todas essas quebras de linhas no final. Fizemos várias quebra de linha, estamos no meio da implementação, tivemos que parar de novo. Usamos o comando git stash novamente.

Fizemos um git stash, adicionamos essa modificação lá na nossa lista de modificações que queremos rever depois. Se escrevermos git stash list, ele listará o movendo chamada de função e a última stash que não tem um nome específico. Portanto, ela aparece como WIP on movento-detalhes: c53eb16 Quebrando linha do script.

Entendendo a pilha de modificações
Se fizermos um git stash pop, ele sempre vai aplicar a última alteração que adicionamos. Portanto, ele sempre pega esse de índice zero. Ele sempre vai empilhando modificações.

O que isso quer dizer? Imagina que essa nossa stash é uma gaveta e nessa gaveta estamos guardando pratos. Portanto, abrimos a gaveta, colocamos um prato. Na gaveta, adicionamos outro prato em cima. Se vamos pegar um prato, pegamos o prato que está em cima, certo? Portanto, é o último que adicionamos. Isso é o conceito de pilha.

Temos aqui na stash uma pilha de modificações. Portanto, quando fazemos pop, sempre aplicamos a última que adicionamos. Fizemos um git stash pop, temos a remoção das quebras de linha.

Portanto, se fizermos nosso git stash list de novo, só temos um e agora o nosso índice zero é aquela movendo chamada da função. Só que, imagina o seguinte cenário: Removemos todas as quebras de linha e vamos fazer o git stash de novo.

Retomando alterações anteriores à versão mais recente
No nosso git stash list, temos lá a movendo chamada da função, que agora é o índice 1. E o novo índice zero é essa remoção de quebras de linha lá do final. Só que o que queremos voltar a trabalhar no que está guardado nesse índice 1.

$ git stash list
stash@{0}: WIP on movendo-detalhes: c53eb16 Quebrando linha do script
stash@{1}: On movendo-detalhes: Movendo chamada de função
$
COPIAR CÓDIGO
Portanto, se fizermos o git stash pop, não vai funcionar. Vamos pegar a última alteração que não é o que queremos. Portanto, nesses cenários, quando queremos aplicar algo que está na stash anterior à versão mais recente, podemos fazer o git stash apply e o índice, no nosso caso, o índice 1, que é o movendo chamada da função.

Antes de executar, temos todas as quebras de linha no final do arquivo e a chamada da função está na linha 17. Vamos executar agora no nosso terminal, git stash apply 1. O que vai acontecer? Temos a nossa função sendo movida, mas todas as quebras de linha continuam lá no final.

Se quisermos, podemos aplicar mais de um item de stash. Portanto, podemos fazer aqui o nosso git stash pop sem problema. Só que aí vamos ter um conflito.

Podemos aplicar várias stashes se elas não estiverem no mesmo arquivo, se elas não forem conflitar com o que temos.
Temos modificações no arquivo que seriam sobrescritas. Portanto, não vamos aplicar essa stash mais. Portanto, se fizermos um stash list, ele adicionou um novo detalhe lá na nossa stash.

Para recapitular, se temos alguma alteração que precisamos adicionar ou salvar para depois, chamamos o comando git stash. O comando git stash vai adicionando mensagens no formato de pilha.

Recapitulando:

Se queremos pegar algo e aplicar uma alteração à última stash que adicionamos, usamos git stash pop;
Se queremos aplicar alguma específica, usamos git stash apply;
Se queremos adicionar algo na nossa stash com mensagem, usamos git stash push;
Se queremos limpar a nossa stash, usamos git stash clear.
Vamos desfazer a alteração de mover. Não queremos mover essa mensagem, queremos fazê-la voltar para onde ela estava originalmente. Portanto, agora temos o nosso código no estado original, certo?

No entanto, se fizermos um git status, temos uma alteração ainda. Se fizermos um git diff, repare que essa alteração é invisível para nós.

Portanto, provavelmente, o nosso Visual Studio Code apagou alguns espaços que estavam em uma linha. Só que não queremos comitar isso, queremos desfazer essa alteração. Como podemos desfazer alterações que estão prontas para serem adicionadas a um commit? Através do git. É isso que vamos fazer no próximo vídeo.

@@02
Limpando a stash

Ao trabalhar em uma nova funcionalidade para um sistema, você precisou interromper o trabalho para uma correção urgente de um bug. Para guardar o trabalho em progresso que você estava desenvolvendo, o git stash foi utilizado. Após corrigir o bug em questão, você foi informado que a funcionalidade não será mais implementada, portanto, aquele trabalho que você guardou poderá ser descartado.
Qual comando você utilizaria para apagar tudo que foi armazenado com o comando git stash?

git stash clear --all.
 
Alternativa incorreta
git stash pop.
 
O pop aplica determinado item da stash em nosso repositório e o remove da stash, mas não limpa nossa stash.
Alternativa incorreta
git stash drop.
 
Alternativa incorreta
git stash clear.
 
O comando git stash clear limpa a stash, ou seja, apaga tudo que foi salvo com o comando git stash. Caso você queira remover apenas um único item da stash, você pode utilizar git stash drop.

@@03
Para saber mais: pop, drop e apply

Os comandos pop, drop e apply do git stash possuem semelhanças e diferenças bem importantes, então vamos fazer um pequeno resumo de suas funcionalidades aqui:
Apply
O comando git stash apply espera um índice de um item na stash e o aplica ao repositório, porém, esse comando não remove o item da stash, ou seja, se após executar o comando git stash apply 1 você executar git stash list, o item referente ao índice 1 continuará na stash.

Pop
O git stash pop faz exatamente a mesma coisa que o git stash apply, porém, além de aplicar o item da stash, ele também o remove de lá. Esse comando, sem nenhum parâmetro extra, vai aplicar o último item adicionado à stash, mas nós também podemos informar um índice para ele, como git stash pop 1.

Drop
O git stash drop funciona exatamente como o pop, mas com uma simples diferença: ele apenas remove o item da stash, sem aplicá-lo em nosso repositório. Dessa forma, git stash drop remove o último item adicionado à stash, enquanto o git stash drop 1 remove da stash o item com índice 1.


@@04
Desfazendo alterações

Transcrição

Olá! Boas-vindas de volta. No último vídeo, nós falamos um pouco sobre a stash. E, no final, deixamos um pequeno problema não resolvido para levantar o cenário a seguir.
Imaginem que nós estamos criando alguma modificação. Então, nós removeremos todas as linhas do final. Nesse ponto, temos vários arquivos modificados e alterados. Porém, nós percebemos que a implementação está incorreta ou a funcionalidade não será mais implementada. Basicamente, queremos descartar o que foi feito.

Se temos apenas um arquivo, para descartar essa modificação, podemos fazer um Ctrl + Z. Mas, se temos vários arquivos, sair fazendo Ctrl + Z em muitos lugares pode ser bastante cansativo. Para isso, podemos utilizar o git.

Descartando várias alterações
Vamos limpar o terminal e executar um git status. Temos um arquivo que foi modificado, mas poderíamos ter vários. Por exemplo, também vamos modificar algo no index.html. Algo inválido: adicionamos várias quebras de linha.

Então, nosso git status tem modificações. E o que queremos fazer é desfazer essas modificações. Nós não fizemos git add e não commitamos isso. Como não foi commitado, não é um revert, nem um reset. Não é um comando que já aprendemos no curso anterior.

O que queremos fazer é restaurar o nosso local de trabalho para um estado válido, sem essas modificações. Então, queremos fazer um git restore.

Podemos fazer o restore para algum estado específico, mas se não informarmos o estado, isso significa que a restauração será feita sem o que foi modificado. Ou seja, o último commit do nosso branch atual.
Então, queremos fazer o restore de quê? Podemos fazer de app.js e de index.html um de cada vez. Ou fazer do ponto (git restore .). Assim como já aprendemos que o git add . adiciona o projeto todo, o git restore . restaura todo o projeto também. E esse ponto não é um significado especial do git.

Na linha de comando, o ponto significa o diretório atual. Então, estamos fazendo o restore de tudo na pasta atual.
Então, esse git restore vai fazer um Ctrl + Z no nosso projeto. Assim, as linhas que adicionamos no index sumiram, e aquelas alterações no nosso app.js também sumiram. Então, com isso, se fazemos um git status, temos o nosso projeto limpo novamente.

E o git restore é um dos comandos que veio para substituir o git checkout. Então, o git checkout, como dissemos, faz muitas coisas. Uma das coisas que ele fazia é o restore. Com o git checkout -- ., temos o mesmo resultado.

Então, novamente, vamos remover as quebras de linha e salvar. Se fizermos o git checkout -- ., ele desfaz as alterações. Então, temos todas as nossas linhas adicionadas de novo.

Como falamos, esse restore restaura o projeto ou restaura arquivos específicos para algum ponto específico. Por padrão, ele faz o restore para head, ou seja, para o nosso último commit, que no nosso caso aqui é quebrando a linha do script.

Mas e se quisermos fazer o restore para ver o nosso projeto ou ver um arquivo específico antes de corrigir a indentação, ou seja, indentando os botões? Queremos ver como o arquivo era em dado commit, como o nosso projeto todo era nesse outro commit.

Então, conseguimos "viajar no tempo" também utilizando o git restore. E isso nós veremos no próximo vídeo.

@@05
Viajando no tempo

Transcrição

Olá, pessoal! Boas-vindas de volta. Como mencionamos anteriormente, o comando git restore pode restaurar estados de um arquivo ou de um projeto inteiro. Dissemos que queríamos "viajar no tempo", mas antes precisamos mostrar um detalhe interessante.
Vamos supor que removemos todas as quebras de linhas extras que inserimos no arquivo. Estamos prontos para adicionar nosso app.js para fazer o commit.

Adicionamos com o comando git add app.js, então, ele está no "stage", pronto para ser comitado. Isso é o que chamamos de "stage" ou "staging area". Mas, o que acontece se quisermos desfazer isso? Não estamos prontos para comitar. Queremos fazer mais alterações ou simplesmente desistir dessa modificação.

Note que o próprio git já nos mostra que podemos fazer um restore do que está em nossa "staging area". Se fizermos git restore --staged, significa que estamos modificando algo que está dentro dessa "staging area", dentro de algo que fizemos com o git add.

Assim, com git restore --staged app.js, não desfazemos a alteração, mas retornamos ao estado anterior. Agora, é como se não tivéssemos feito o git add. Observe que ele está pronto para fazermos o git add e as linhas, ainda estão removidas.

Agora, se quisermos desfazer as alterações, fazemos o git restore app.js. Sendo assim, desfizemos as alterações. Repare a diferença entre o --staged e o staged.

Um outro parâmetro que podemos passar para o restore é, suponha que queremos mover nosso index.html para o estado que estava quando fizemos o Merge branch 'nova-funcionalidade' into main.

O que podemos fazer? Podemos copiar o hash do commit, fazer o git restore --source = e colá-lo em seguida. Queremos restaurar para esse estado nosso index.html. O comando inteiro ficará parecido com o seguinte:

git restore --source = 5081a55bc92af2917c8519f16a7412b86ba3b1c2 index.html
Quando fazemos isso, ele pega o index e o coloca no estado que estava nesse commit.

Ao acessar o index, observe que tem algumas alterações: O nosso script está em uma linha só, a nossa tag de link não está indentada e os botões também não estão indentados. Ele retornou para esse estado. Se fizermos um git status, podemos modificar o arquivo a partir daquele estado e adicionar um novo commit, se quisermos.

Mas, se quisermos apenas visualizar o arquivo e entender como ele estava naquele estado, podemos desfazer esse trabalho, ou seja, restaurar para o estado normal dele com o git restore index.html, que é equivalente a fazer --source = head.

Fazer o restore sem esse --source é equivalente a fazer --source = head, que corresponde ao último commit que temos no branch atual.
Agora, se fizermos o git status, temos nossa branch movendo-detalhes correta. Se fizermos um git log, nossa branch movendo-detalhes está no mesmo lugar que a branch main.

Vamos voltar para a nossa branch com git switch main e vamos remover com git branch -d movendo-detalhes, que foi um branch que criamos apenas para simular a criação de uma nova funcionalidade, mas não chegamos a comitar nada lá.

Nesse vídeo, aprendemos a manipular nossa "working tree", que é o que estiver em nosso projeto, mesmo que não tenhamos adicionado para commit.

Quando temos algo indicado com modified, isso está na nossa "working tree", o nosso projeto, basicamente. Manipulamos também nossa staging area, que é o que está verde quando fazemos o git status, o que modificamos quando fazemos nosso git add.

Aprendemos a manipular esses dois status com o git restore, seja removendo algo da nossa staging area com o git restore staged ou removendo algo da nossa working tree com o git restore sem o staged. Assim, aprendemos a manipular nosso código, a working tree e a staging area.

Suponha que esse projeto, no estado que está, está aceitável. Queremos apontar que temos uma nova versão (a 0.1.0). Como podemos gerenciar versões ou marcar um checkpoint, um ponto onde queremos salvar e dar um nome para esse estado? Vamos falar sobre isso, sobre criar versões e gerar releases na próxima aula.

@@06
Faça como eu fiz: desfazendo alterações com Git

Nesta aula, nós aprendemos sobre a stash e sobre o comando restore.
Agora é sua vez! Chegou a hora de guardar o seu trabalho para o futuro e viajar no tempo com git utilizando o nosso projeto base ou um projeto de sua preferência.

Já teve a chance de praticar os comandos necessários para salvar alterações, aplicá-las descartá-las ou reverter arquivos para um estado anterior? Oferecemos algumas sugestões na seção Opinião do instrutor.

Opinião do instrutor

Salve alterações não adicionadas para commit utilizando o comando git stash;
Utilize o comando git stash list para visualizar os itens adicionados à stash;
Faça uso dos comandos git stash pop e git stash drop para aplicar ou descartar itens da stash;
Com o comando git restore, desfaça as alterações tanto da working tree quanto da staging area;
Utilize o parâmetro --source, do comando git restore, para deixar determinado arquivo no estado específico de um commit que você escolher.
Se surgirem dúvidas, não hesite em recorrer ao nosso Fórum.

@@07
O que aprendemos?

Nessa aula, nós:
Conhecemos o conceito de stash, que permite que guardemos trabalhos em progresso sem precisarmos fazer o commit, de forma que possamos retomar esse trabalho no futuro;
Aprendemos a manipular a stash adicionando, aplicando e removendo itens dela com os comandos git stash pop, git stash drop, git stash apply e git stash clear;
Conhecemos o comando restore, que altera o estado de determinado arquivo;
Aprendemos o significado de working tree, que é o nome do estado atual do nosso código com todas as alterações, incluindo as não adicionadas para commit, e de staging area, que é onde ficam os arquivos ao realizarmos o git add.