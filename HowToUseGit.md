# Guia e Documentação para uso do Git e GitHub - AeroRiver

O Git é uma ferramenta extremamente poderosa para versionamento e controle de código.
Quando integrado com o GitHub, ele permite o controle remoto e local do código, facilitando o trabalho colaborativo
e a organização do projeto. Este guia apresenta os principais comandos e dicas para uso do Git no cotidiano de desenvolvimento da AeroRiver.

## Git x GitHub

Antes de tudo é interessante entender a diferença entre Git e GitHub e como essas ferramentas desempenham papéis diferentes mas importantes
no processo de controle de versão e colaboração:

**Git:** É um sistema de controle de versão distribuido que permite rastrear as mudanças no código-fonte ao longo do tempo. Ele funciona localmente no computador
permitindo o controle e versionamento local, mesmo desconectado da internet. Com o git é possível criar commits, branches, mesclar códigos e reverter alterações.

**GitHub:**  É uma plataforma online de hospedagem de código que utiliza o Git como sistema de controle de versão. O GitHub oferece recursos adicionais, como rastreamento de problemas,
solicitações de pull e integração contínua, mas principalmente facilita a colaboração entre os membros da equipe por promover o projeto online e acessível a todos que irão trabalhar nele.

**---**

A partir dessa definição inicial, vamos conhecer quais são os principais comandos do git e quais os mais úteis para o trabalho de desenvolvimento

## ```git init```:

Esse comando inicializa no diretório atual o reposítorio git. Após executar esse comando, note a criação da pasta .git no diretório do seu projeto.

## ```git add```:

O ```git add``` é o comando utilizado para adicionar as mudanças feitas no diretório de trabalho ao índice do Git, ou **staging area**. Isso prepara as mudanças para serem incluídas no próximo **commit**
### Sintaxe:

```bash
git add <arquivo-modificado-1> <arquivo-modificado-2> ... -- Adiciona apenas os arquivos referenciados no comando.
git add . -- Adiciona todos os arquivos modificados 
```

A escolha entre usar o ```git add .``` ou adicionar manualmente depende de como deseja salvar as modificações. Adicionar manualmente pode ser útil quando as alterações não estão relacionadas ao mesmo commit,
ou quando deseja separar o flux de trabalho em etapas distintas. Por outro lado, o ```git add .``` é útil quando deseja-se adicionar todas as modificações no mesmo contexto, agrupando tudo em um único commit.

## ```git commit```:

O comando ```git commit``` é o comando utilizado para criar um **commit** com todas as mudanças em **stage**. É o comando usado para criar um ponto de salvamento no histórico do projeto, capturando o estado
atual dos arquivos que foram preparados pelo ```git add``` e adicionando uma mensagem descritiva que geralmente resume as alterações feitas.

### Sintaxe:

```bash
git commit -m "Mensagem de commit"
```

Não há uma regra definida para o texto à ser adicionado na mensagem de commit, contúdo é comum adotar convenções para facilitar a compreensão do que o commit representa. As mais comuns são:

```bash
[FEAT] Para novas funcionalidades ou recursos adicionados.
[FIX] Para correções de bugs.
[REFAC] Para refatoração de código, ou seja, alterações que melhoram a estrutura, legibilidade ou lógica do código sem alterar sua funcionalidade.
[DOCS] Para alterações na documentação.
[STYLE] Para alterações relacionadas a formatação, espaçamento, ou estilos de código que não afetam sua funcionalidade.
[TEST] Para adição ou modificação de testes.
[CHORE] Para tarefas de manutenção, como atualização de dependências, configurações de ambiente ou outras tarefas relacionadas a estrutura do projeto e que não se enquadram nas outras categorias.
```

## ```git branch```:

Esse é o comando utilizado para gerenciamento do estado das **branches**, como listar, renomear, criar e deletar.

### Sintaxe:

```bash
git branch -- Sem nenhum argumento, lista todas as ramificações presentes no repositório. A branch atual é destacada por *.
git branch <nome-da-nova-branch> -- Para criar uma nova branch basta executar o ```git branch``` passando como argumento o nome da nova branch.
git branch -M <nome-da-branch> -- Para criar uma nova branch e definir como branch default.
git branch -d <nome-da-branch> -- Para deletar uma ramificação que não é mais necessária. !!CUIDADO!! Comando irreversível.
git branch -D <nome-da-branch> -- Para forçar a exclusão de uma branch. Note que caso haja commits na branch que nao foram mesclados, o parâmetro -d não permite a exlusão. !!CUIDADO!! Comando irreversível.
git branch -m <novo-nome-da-branch> -- Para "renomear" uma branch. Esse comando irá criar uma nova branch com o novo nome e excluir a antiga.
```

## ```git checkout```:

Ao trabalhar com um repositório com várias ramificaões, o comando ```git checkout``` é o responsável por alternar entre essas ramificações.

### Sintaxe:

```bash
git checkout <nome-da-branch-alvo> -- Esse comando irá alternar a branch atual para a branch alvo, para checar o funcionamento execute ```git branch``` e verifique qual a branch atual.
git checkout -b <nome-da-nova-branch> -- Utilizando o git checkout também é possível criar uma nova ramificação. Esse comando cria e alterna para a nova branch.
```

## ```git merge```:
    
O comando git merge é utilizado para mesclar as alterações realizadas em duas branches em uma única. Ele combina as alterações de duas branches diferentes e cria um novo commit de merge.

### Sintaxe:

```bash
git merge <nome-da-branch> -- Esse comando ira mesclar as alterações da branch especificada na branch atual.
```

## ```git stash```:
    
Esse comando é poderoso para armazenar de forma temporária as alterações não commitadas, permitindo trabalhar em outras tarefas sem necessariamente fazer um commit das mudanças atuais, alternar rapidamente
para outra branch ou resolver um problema urgente sem perder o trabalho realizado até o momento. Quando executada, o Git salva as mudanças em um ambiênte temporário chamado "stash", sendo possível armazenar múltiplos
conjuntos de mudanças.

### Sintaxe:

```bash
git stash -- Cria um stash das mudanças atuais.
git stash -m "Mensagem do stash" -- Cria um stash com uma mensagem personalizada.
git stash list -- Lista todos os stashs salvos.
git stash apply <identificador-do-stash> -- Aplica no repositório local o stash sem excluí-lo.
git stash pop <identificador-do-stash> -- Aplica o stash e o exclui da lista.
git stash drop <identificador-do-stash> -- Remove um stash da lista.
```

## ```git diff```

Na série de comandos úteis, o git diff é usado para mostrar as diferenças entre as mudanças que foram feitas em arquivos no seu diretório e as versões anteriores desses arquivos que estao **staged**
ou que ja sofreram commit.

### Sintaxe:

```
git diff -- Mostra todas as diferenças de todos os arquivos
git diff <arquivo> -- Mostra as diferenças apenas do arquivo especificado.
```

## Trabalhando com repositórios remotos
    
Até o momento, os comandos descritos não necessariamente precisam de um reposítorio remoto ou GitHub para serem executados. Eles funcionam e oferecem um ótimo suporte para versionamento local
de código. No entando, podemos potencializar ainda mais o trabalho utilizando esses comandos em sincronia com um repositório online no GitHub. A seguir, iremos ver alguns comandos git para trabalhar e sincronizar
o estado atual do repositório local com o repositório remoto.

## ```git remote```:

O ```git remote``` é usado para gerenciar repositórios remotos de um projeto Git. Repositórios remotos são aqueles hospedados em outro local como um servidor na internet, que pode ser acessado por várias pessoas.
Esse comando permite adicionar, criar ou visualizar os repositórios remotos associados ao projeto.

### Sintaxe:

```bash
git remote add <nome-remoto> <URL> -- Comando utilizado para adicionar um repositório remoto ao projeto, o qual deseja sincronizar. Os parâmetros são o nome do repositório remoto (origin, por exemplo) e a url remota.
git remote rm <nome-remoto> -- Esse comando remove um repositório remoto do seu projeto.
git remote -v -- Lista os nomes e URL's dos repositórios remotos associados ao projeto.
```
    
## ```git clone```:
O ```git clone``` é o comando utilizado para criar uma cópia local de um respositório remoto do GitHub. Isso permite ter uma versão local do projeto na qual pode-se fazer alterações, trabalhar
e contribuir sem afetar diretamente o repositório remoto.

### Sintaxe:

```bash
git clone <URL-do-repositório> -- Para clonar um repositório de maneira simples
git clone <URL-do-repositório> <diretorio-destino> -- Para clonar o repositorio dentro de uma pasta específica
git clone <URL-do-repositorio> -b <nome-da-branch> -- Para clonar o conteúdo de uma branch específica 
```

## ```git fetch```:
    
O comando git fetch é utilizado para buscar todas as atualizações das branches remotas. Ele não faz alterações no código, mas traz as últimas alterações das ramificações, permitindo a inspeção e a incorporação
das alterações no projeto local.

### Sintaxe:

```bash
git fetch <nome-remoto> -- Para espeficiar um local remoto
git fetch -- Para buscar alterações em todos as ramificações.
```

## Atualizando e sincronizando os repositórios remotos e locais

Entendido os comandos de git para salvar as alteraçaões locais e adicionar um repositório remoto ao projeto podemos partir para a sincronização do trabalho remoto com o local.

## ```git push```:
    
Esse é o comando utilizado para salvar as alterações e enviar as alterações locais do repositório git para o repositório remoto. Depois de adicionar as alterações com git add e criar o commit com git commit
usamos o git push para enviar o(s) commit(s) para o repositório remoto.

### Sintaxe:

```bash
git push origin <branch-local>:<branch-remota> -- Esse comando ira enviar as alterações da branch local para a branch remota no repositório "origin"
git push origin <branch-remota> -- Se estiver trabalhando em uma branch local que tenha o mesmo nome que a branch remota, esse é o comando simplificado para dar push no repositório "origin"
```

## ```git pull```:

O comando git pull é utilizado para recuperar todas as alterações de um repositório remoto e incorpara-las automaticamente ao repositório local. Basicamente, ele combina os comandos git fetch e git merge integrando as alterações
à branch local.

### Sintaxe:

```bash
git pull origin <branch-remota> -- Esse comando irá buscar e integrar as alterações da branch remota à sua branch local.
```

---

## Usando na prática:

Os repositórios de desenvolvimento da AeroRiver possuem um fluxo de trabalho proprio com branches e ramificações específicas. A seguir, veremos em um cenário prático de como utilizar o git para trabalhar com esses repositórios:

- ```git clone``` para clonar o repositório e ```git checkout develop``` para trocar para a branch de desenvolvimento.
- Caso já tenha o repositório clonado: ```git checkout develop``` e  ```git pull origin develop``` para rastrear e trabalhar com a versão mais recente do código.
- Vai precisar trocar de branch? ```git stash``` para não perder o trabalho até o momento e depois ```git stash apply``` para continuar de onde parou.
- Ao termino do desenvolvimento dos códigos é hora de atualizar a branch remota, respeitando as regras de negócio do repositório: ```git checkout -b <solução>_develop``` para criar
a branch com a solução desenvolvida, depois ```git add``` para adicionar os arquivos que vão pro commit e por fim ```git commit -m "<mensagem>"```. Commit criado, use ```git push origin <solução>_develop```
para enviar as alterações para a nova branch.
- Com isso, basta criar o Pull request da nova branch para a develop no GitHub e para manter a sua branch develop sempre atualizada:
```bash
git checkout develop
git merge <solução>_develop
git branch -d <solução>_develop
```

---

O Git e GitHub são ferramentas muito interessantes e possuem muito mais funcionalidades e caracteristicas além dessas descritas nesse guia e para dominar e entender melhor o funcionamento é necessário sempre acompanhar a documentação
das mesmas. Outros comandos que aqui nao foram descritos mas que podem ser úteis em vários contextos são o git rebase e git reset. Esse é apenas um guia simples e prático sobre os principais comandos de git para uso rotineiro no desenvolvimento
de projetos na AeroRiver.

**!!** Alguns desses comandos são irreversíveis e potencialmente resultar na perda de arquivos e alterações. **!!** 

**===**

- Pedro Masteguin.
