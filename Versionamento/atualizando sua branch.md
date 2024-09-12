# Atualizando sua branch

Você realizou sua alterações e após alguns dias verificou que a main está mais atualizada que a sua branch? Deseja continuar trabalhando na sua branch? Então esse tutorial é para você!

## Passo 1: Atualizando a main
Certifique-se que você está na branch main, caso não esteja, execute o comando abaixo:

```bash
git checkout main
```

Agora vamos atualizar a main com as alterações que estão no repositório remoto, para isso execute o comando abaixo:

```bash
git pull
```

## Passo 2: Atualizando sua branch
Agora que a main está atualizada, vamos atualizar a sua branch com as alterações que estão na main, para isso execute o comando abaixo:

```bash
git checkout <nome da sua branch>
git merge main <nome da sua branch>
```
Voalá! Sua branch está atualizada com as alterações da main, agora você pode continuar trabalhando nela.

## Passo 4: Deu ruim 
Se você tem alterações locais e até commits pode descartar tudo com os commandos a seguir:

```bash
git fetch origin main
git reset --hard origin/main
```
