# Como contribuir e utilizar os repositórios do Portal LD

## Inicio:

Certifique-se de ter o [Git](https://git-scm.com/) instalado em sua máquina.

## Passo 1: Clone
Clone o repositório que queira trabalhar da organização [Portal LD](https://github.com/orgs/PortalLD/repositories) para sua máquina.

**Exemplo:** Clonando o repositório do App-Backend

Entre na página do repositório clique em **Code** e copie o link do repositório.

![Imagem - Tela1](https://marlonhenq.dev/repositorio/imagens/images-portalld/image.png)


No seu terminal digite o comando:

```bash
git clone link_do_repositorio
```

Estando com o repositório clonado em sua máquina criaremos uma branch para trabalhar.

## Passo 2: Branch
Crie uma branch com o nome da feature que irá desenvolver.
(Por padrão utilizaremos o nome, ou apelido do desenvolvedor, porém correções de bugs ou features específicas podem receber suas branches individuais para o melhor controle do projeto.)

```bash
git checkout -b nome_da_branch
```

Estando em sua branch, você pode começar a desenvolver.

## Passo 3: Commit
Após desenvolver a feature ou corrigir um bug, você deve commitar as alterações feitas.

```bash
git add . # Adiciona todas as alterações feitas
```

PS: O "." após o add significa que você está adicionando todas as alterações feitas, caso queira adicionar apenas um arquivo, basta colocar o nome do arquivo.

Agora basta commitar as alterações.

```bash
git commit -m "Mensagem do commit" 
```

Para a criação de boas mensagens em commits será interesante seguir o padrão do [Conventional Commits - EN](https://www.conventionalcommits.org/en/v1.0.0/), aconselho que todos leiam (é algo bem rápido). Versão em português [Conventional Commits - PT](https://www.conventionalcommits.org/pt-br/v1.0.0/).

## Passo 4: Push

Após commitar as alterações, basta enviar para o repositório remoto.

```bash
git push
```

No geral o comando acima já é o suficiente, porém as vezes o git pode pedir para que você especifique a branch que deseja enviar. Ai basta copiar o comando que o git irá te dar e enviar.

## Passo 5: Pull Request

Após enviar as alterações para o repositório remoto, você deve criar um Pull Request para que as alterações sejam revisadas e aprovadas.

Para criar um Pull Request, basta entrar na página do repositório, clicar na aba **Pull Requests** e clicar em **New Pull Request**.

![Imagem - Tela2](https://marlonhenq.dev/repositorio/imagens/images-portalld/image-1.png)

Certifique-se de que a branch para a qual você está enviando é a branch correta (geralmente a main, talvez no futuro a dev para desenvolvimento) e certifique-se que a branch que você está enviando é a branch que você criou para desenvolver a feature (geralmente a branch com o seu nome).

De forma rápida muitas vezes após o push o Github já lhe informa que houve uma alteração e sugere que você crie um pull request para a branch main, caso isso aconteça, basta clicar em **Compare & pull request**.

![Imagem - Tela3](https://marlonhenq.dev/repositorio/imagens/images-portalld/image-2.png)

Pronto! Seu código foi enviado para análise e em breve será revisado e aprovado (ou não hehe).