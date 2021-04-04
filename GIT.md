# GIT

Para clonar um repositório:
```
git clone <url>
```

Commit: um commit funciona basicamente como um checkpoint do seu projeto. Ela gera uma espécie de "snapshot" do estado dos seus arquivos naquele momento. Isso permite que seja possível navegar em diferentes estados, inclusive voltar a versões anteriores.

<br>

Ao se realizar alterações em um arquivo, antes de commitá-lo, é necessário trackear os arquivos que terão seus estados alterados no commit. Para isso, utilizamos o comando:
```
git add <filename>
```

<br>

Após selecionar os arquivos que serão gravados no commit, podemos realizar o commit através do comando:
```
git commit -m "message"
```
Neste comando, ainda é possível definir uma mensagem, que será basicamente uma descrição resumida de quais alterações foram feitas no arquivo.

<br>

Podemos ver o status do repositório local em comparação com o repositório em um servidor público utilizando o comando :
```
git status
```

<br>

Para realizarmos um merge nos repositórios e adicionamos as modificações realizadas, ou seja, subir o repositório local para o remoto, usamos o comando:
```
git push
```

<br>

É possível abreviar os commits (quando se quer commitar todos os arquivos que foram alterados), onde em vez de ter que se executar ```git add <filename>``` e em seguida ```git commit -m "message"```, pode-se usar apenas o comando abaixo:
```
git commit -am "message"
```
onde o ao se usar ```-am``` o git entende que precisa trackear (adicionar) ao commit todos os arquivos que foram modificados e já executar o commit.

<br>

Quando a versão do projeto que está no repositório remoto é mais recente que a versão local, podemos usar o comando abaixo para aplicar as alterações mais atuais para o repositório remoto:
```
git pull
```

<br>

## Merge Conflicts

Quando houver conflito de estados dos arquivos entre o repositório local e o repositório local, ao se tentar realizar um git pull, o git retornará um aviso de conflito, indicando qual arquivo possui conflito e qual o hash (código único) do commit está conflitando.

O Visual Studio Code recebe a informação do git e informa no arquivo conflitante, quais os estados que possuem conflito no formato abaixo. Cabe ao programador decidir qual versão será preservada (pode-se adaptar o código para preservar as duas) e alterar o arquivo.
```
<<<<<<< HEAD
a = 5
=======
a = 0
>>>>>>> <hash commit>
```

## Comandos úteis

É possível rastrear todas as alterações registradas (commitadas) através do comando:
```
git log
```

Caso queira desfazer as alterações e retornar ao último commit, pode se usar o comando:
```
git reset
```
Caso queira retornar ao um commit em específico, pode-se usar o comando abaixo, onde --hard significa resetar tudo até o commit especificado.
```
git reset --hard <hash commit>
```
Caso queira retornar ao estado inicial da branch criada, pode-se usar o comando:
```
git reset --hard origin/main
```

## Branchs

Quando estamos trabalhando em um projeto, é comum termos que voltar a etapas antigas para corrigir bugs ou fazer alterações. Porém, se utilizamos uma forma de trabalho totalmente linear, ao necessitarmos retornara um estado anterior dos arquivos, acabaremos perdendo alterações úteis que foram feitas posteriormente àquele commit.

Dessa forma, o Git permite que criemos as **Branchs**. Que podem ser interpretadas como diferentes esteiras de trabalho no seu projeto.

Ao se utilizar mais de uma branch, podemos trabalhar paralelamente em diferentes pontos do projeto e retornar a commits anteriores para corrigir bugs com mais facilidade. Feitas as alterações, é possível por fim realizar um *merge* das branchs e unificá-las novamente.

Para saber em qual branch a sua HEAD (uma espécie de cursor que aponta em qual esteira se está trabalhando no projeto) está atualmente, usamos o comando:
```
git branch
```

Para mover a HEAD para uma **nova** branch, pode se usar o comando:
```
git checkout -b <name_new_branch>
```

Para apenas mover a HEAD entre as branchs já existentes, usamos apenas:
```
git checkout <name_branch>
```

Para unificar branchs, usamos:
```
git merge <name_branch>
```
O merge será realizado entre a branch chamada no comando e branch atual, na qual a HEAD se encontra.

Caso haja conflito entre as branchs, ou seja, arquivos foram editados nas mesmas linhas de código, então o Git retornará um aviso. O Git costuma resolver os conflitos, porém, não consegue fazemos caso haja alterações na mesma parte do código. Assim, será necessário avaliar o conflito e resolvê-lo escolhendo e unificando as alterações que serão definitivas. Após isso, é só realizar o commit.

<br>

## Como colaborar em projetos Open-Source

Para colaborar em projetos Open-source, o fluxo é levemente diferente. Os projetos são abertos e públicos, porém isso não significa que qualquer um possa fazer um git push no repositório. O que acontece nesse caso, é que é necessário ser feito um **fork** do projeto. Ao se realizar um fork, uma cópia idêntica do projeto será gerada no seu GitHub e ali você pode começar a trabalhar em suas contribuições.

Quando achar que suas contribuições estão prontas, você pode realizar um pull request (a informação dos pull requests fica disponível no repositório original do projeto) e ali, as suas alterações serão analisadas e avalidadas tanto pela comunidade quanto pela equipe de pessoas mantenedora do projeto. Feitas as avaliações, eles podem rejeitar ou aprovar as suas contribuições.