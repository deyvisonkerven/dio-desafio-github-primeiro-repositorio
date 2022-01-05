# Principais Comandos do Git

## Principais Comandos do Git

- `git config -–list` » Lista as configurações do Git, se estiver dentro do repositório, lista mais itens
- `git config -–global user.name "Meu Nome"` » Define o nome de usuário para o Git
- `git config -–global user.email "email@dominio.com"` » Define o e-mail de usuário para o Git (tem de ser o cadastrado no GitHub)
- `git config -–global core.editor vim` » Define o editor de texto padrão para abrir automaticamente arquivos informados pelo Git
- `git init` » Inicializa um repositório Git
- `git status` » Vê o estado atual do projeto
- `git add arquivo.txt` » Adiciona o arquivo arquivo.txt ao projeto

> Opções do parâmetro **add**

```
git-add # mesmo comando que 'git add'

# O comando git-add não irá adicionar arquivos ignorados por padrão a menos que seja utilizado o parâmetro '-f'

git add -A # Adiciona todos arquivos que foram modificados, mesmo que: --all, --no-ignore-removal

git add *.txt # Adiciona todos os arquivos '.txt' que foram modificados

man git-add # manual completo sobre git-add
```

- `git commit -m "Minhas mudanças efetuadas"` » Armazena as mudanças efetuadas e descreve o que foi alterado

- `git log` » Mostra todas as mudanças que já foram efetuadas: commit, autor e data

- ```plaintext
  git push -u origin master
  ```

   

  » Envia todos os arquivos modificados e “commitados” para o repositório no github

  - `-u` - faz com que o Git armazene esse comando e da próxima vez basta utilizarmos `git push`
  - `origin`- diz que o repositório no github possui o mesmo nome do projeto/diretório que você está enviando
  - `master` - é o nome da *branch* (**indicador**) [Clique aqui para saber mais sobre branches](https://goo.gl/2ZT5Cd)

- `git pull origin master` » Verifica as mudanças efetuadas por outros colaboradores do projeto

- `git diff HEAD` » Verifica as partes dos arquivos alterados no último commit, **veja mais opções em** `man git-diff`

- `git reset arquivo.txt` » Remove um arquivo do projeto

- `git checkout – arquivo.txt` » Desfaz a última alteração feita num arquivo

- `git rm "*.txt"` » Remove 1 ou mais arquivos utilizando “curinga”

- `git clone https://github.com/user/project.git` » Copia um projeto pro seu PC

- `info git` » Obtém a Documentação do git

- `man git` » Obtém o Manual do git

  

## O que é GitHub?

Se você vai utilizar Git, é necessário armazenar seu repositório em algum lugar. Existem duas formas de se fazer isso, offline, no seu próprio computador, ou online, em alguma plataforma como [GitHub](https://github.com/), [BitBucket](https://bitbucket.org/) ou [GitLab](https://gitlab.com/explore).

É exatamente para isso que o GitHub serve, para armazenar seus repositórios, ele é o “Google Drive dos códigos”.

## Fluxo de trabalho 1

Geralmente, o fluxo de trabalho com Git e GitHub é realizando um *fork* de um determinado repositório de outra pessoa. Dessa forma, vamos criar uma cópia deste repositório no nosso perfil. Após fazer o *clone* do *fork* para a nossa máquina local, podemos realizar alterações, e publicar as alterações feitas em seu repositório *fork* no GitHub. Por fim, poremos criar um *pull request* do seu *fork* para o repositório principal (*upstream*).

### Fork

Vamos começar realizando o *fork* de um repositório base no GitHub. Veja nosso repositório [artigo-tutorial-git](https://github.com/buteco-tech/artigo-tutorial-git) e clique no botão ***Fork\*** no canto superior direito. Ao clicar, será feita uma cópia do repositório do Buteco em seu perfil no GitHub.

Agora em seus repositórios você tera uma cópia de **artigo-tutorial-git**. Lembre-se, você não está no repositório principal, você está no seu, as alterações feitas ali, não terão impacto no principal.

Você deve criar um *Pull Request* para enviar suas alterações, que é o que iremos ver daqui a pouco.

### Git Clone

Vamos clonar o repositório para a sua máquina local para que você possa realizar alterações. Na página do seu repositório no GitHub, existe um botão chamado ***Code\***, clique nele, selecione a opção ***SSH\***, e depois clique no botão de copiar.

![ssh add](https://butecotecnologico.com.br/tutorial-git-e-github/git-clone-btn_huaf13d02f0fa07dc72e122b8016fd4106_21533_508x389_resize_q90_bgffffff_linear_2.jpg)



Agora abra o seu terminal no local que deseja baixar o repositório, e execute (use o endereço que você copiou):

| `1 ` | `git clone git@github.com:buteco-tech/artigo-tutorial-git.git ` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Será pedido para que você informe a sua *passphrase* de quando criou a sua chave SSH. Após, o clone do repositório você terá uma nova pasta chamada `artigo-tutorial-git`.

Entre na nova pasta com o comando:

| `1 ` | `cd artigo-tutorial-git ` |
| ---- | ------------------------- |
|      |                           |

Você deverá ter algo similar a imagem abaixo:

![git clone](https://butecotecnologico.com.br/tutorial-git-e-github/git-clone_hucbe69348fc8342ded8ede1f442605b9b_22322_890x435_resize_q90_bgffffff_linear_2.jpg)



Perceba que existe ali, uma pasta chamada **.git**, é nela que o Git guarda todas as informações do seu repositório, todas as alterações, o endereço do repositório remoto e tudo o que é relacionado ao controle de versão.

> No Windows talvez você não consiga visualizar esta pasta pois ela é um arquivo oculto, então é só seguir [esse tutorial](https://support.microsoft.com/pt-br/help/14201/windows-show-hidden-files) para alterar as configurações.

### Git Status e Git Add

Vamos criar um novo arquivo para que possamos adicionar ele depois, então, crie um arquivo de texto qualquer dentro do diretório do repositório.

| `1 ` | `echo "Tutorial de Git e GitHub" > arquivo.txt ` |
| ---- | ------------------------------------------------ |
|      |                                                  |

Voltando para o terminal, digite `git status`. Você verá essa mensagem:

![git status](https://butecotecnologico.com.br/tutorial-git-e-github/git-status_hu85165349e07a02a5d8c8edcf2f4e3d3a_29729_857x518_resize_q90_bgffffff_linear_2.jpg)



*Untracked files* são as alterações pendentes, nós precisamos adicionar elas à área de *staging*. As alterações que estão no *staging* são as que serão *commitadas* futuramente.

Para adicionar apenas um arquivo execute o comando:

| `1 ` | `git add nome-do-arquivo ` |
| ---- | -------------------------- |
|      |                            |

Ou para adicionar todos os arquivos execute o comando:

| `1 ` | `git add . ` |
| ---- | ------------ |
|      |              |

O `git add` não afeta diretamente o repositório, pois ele ainda não “salvou” as alterações, apenas às moveu para a área de *staging*, quando executamos `git commit` essas as alterações serão salvas.

Agora sim, podemos confirmar as alterações, para isso execute o comando:

| `1 ` | `git commit -m "Meu primeiro commit" ` |
| ---- | -------------------------------------- |
|      |                                        |

O `-m` é para informar uma mensagem que será gravada junto ao *commit*.

Se você executar o comando `git status` novamente, o seu terminal deverá estar parecido com o abaixo.

![git commit](https://butecotecnologico.com.br/tutorial-git-e-github/git-commit_hud75f582002dad73c49ece52a88e7ca2e_30658_846x539_resize_q90_bgffffff_linear_2.jpg)



Agora é hora de subir as alterações feitas no seu repositório local para o seu repositório remoto, nesse caso, o do GitHub.

### Git Push

Quando estamos com alguma alteração *commitada* localmente e queremos subir elas para o repositório remoto, precisamos publicá-las, para isso execute o comando:

| `1 ` | `git push ` |
| ---- | ----------- |
|      |             |

Após, visite a página do seu repositório no GitHub. Você percebera que as alterações feitas localmente, já estão lá, mas atenção, quando você fez o *push*, as alterações foram para o seu *fork*, não para o repositório principal.

### Criando um Pull request

No seu repositório, após feito um *push*, você verá um botão escrito ***Pull request\***. Clique nele.

![pull request](https://butecotecnologico.com.br/tutorial-git-e-github/pull-request-btn_hu40e14ef66307a9655132f77e18184866_56680_1887x775_resize_q90_bgffffff_linear_2.jpg)



Isso irá abrir uma página mostrando os arquivos alterados e um botão ***Create pull request\***. Clique nele, informe o título e um comentário para esse *pull request* e clique no botão ***Create pull request\***.

Pronto, seu PR foi criado com sucesso.

Se você for até a página de [pull requests do repositório principal](https://github.com/buteco-tech/artigo-tutorial-git/pulls), o seu PR estara lá. Agora, para a sua alteração entrar de fato no repositório principal, o se *pull request* deve ser aceito por algum mantedor do repositório. Esse processo de aceitar um *pull request* é chamado de *merge*.

### O que é Pull Request?

Desde o começo desse artigo, tudo girou em torno deste momento, em que você cria o seu *pull request*, mas afinal, o que é um *pull request*?

Para entendermos o que é um *pull request* precisamos entender o que é um *pull*. Quando existe alguma alteração no repositório remoto, e você quer baixar essa alteração para o seu repositório local, ou seja, o seu repositório local está atrasado em relação ao remoto, você digita `git pull` no terminal (olha só, mais um comando novo). Um *pull request* é uma sugestão de uma alteração, ou seja, você está pedindo para que aquele repositório que você enviou o *pull request* faça um *pull* com as suas alterações.

## Fluxo de trabalho 2

Como dito anteriormente, vamos ver outra maneira de se utilizar o Git e GitHub.

Desta vez, vamos começar com o comando `git init` para criar o nosso repositório localmente, depois iremos conectar ele ao GitHub e enviar os nossos *commits*.

### Git Init

Crie uma pasta em qualquer lugar do seu computador e navegue até ela com o seu terminal. Digite então dentro dela, o comando:

| `1 ` | `git init ` |
| ---- | ----------- |
|      |             |

Você perceberá que foi criado uma pasta **.git**, que mapeia as alterações e *commits* do repositório como mencionado anteriormente.

Realize agora alguma alteração. Crie um arquivo de texto, por exemplo. Depois, execute o comando `git add` que foi falado anteriormente e `git commit -m`, agora você já está craque nisso.

![git init](https://butecotecnologico.com.br/tutorial-git-e-github/git-init_hub89ed552460a947b504390a6aec9e88f_27081_875x456_resize_q90_bgffffff_linear_2.jpg)



Feito isso, é hora de subirmos essas alterações para o repositório remoto (que ainda não foi criado).

Precisamos [criar um repositório no GitHub](https://github.com/new). Nesta página informe algumas informações sobre o repositório, como o nome, descrição, e clique em ***Create repository\***.

Pronto, um novo repositório foi criado.

### Vinculando o repositório local, ao remoto

Veja que existem ali três opções:

- ***…or create a new repository on the command line\***
- ***…or push an existing repository from the command line\***
- ***…or import code from another repository\***

![Repositório no GitHub](https://butecotecnologico.com.br/tutorial-git-e-github/repositorio-github-criado_hu3ef0b2cacba4d3c2ef4dca8ccb9fb3da_49040_1429x826_resize_q90_bgffffff_linear_2.jpg)



A primeira opção, é para criar um repositório local, vincular ele ao GitHub, e fazer um *push* das alterações. A segunda é para apenas conectar um repositório local já existente, e fazer um *push* dele. E a terceira, é para importar o código de algum repositório que esteja utilizando um sistema de versionamento de código diferente do Git.

Nós já temos o nosso repositório criado, queremos apenas subir ele ao GitHub, portanto, vamos realizar os passos da segunda opção.

Com o seu terminal aberto na pasta do seu repositório local, execute então os seguintes comandos:

| `1 ` | `git remote add origin git@github.com:seu-nome/git-init-exemplo.git ` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

Esse comando define para onde enviaremos nossos *commits*, nesse caso o GitHub.

| `1 ` | `git branch -M main ` |
| ---- | --------------------- |
|      |                       |

Esse comando cria uma *branch* com o nome `main`, padrão do GitHub.

| `1 ` | `git push -u origin main ` |
| ---- | -------------------------- |
|      |                            |

Esse comando envia as alterações *commitadas* ao seu repositório remoto no GitHub.

Pronto, se você for até a página do seu repositório no GitHub as alterações já estarão lá.
