# Documentação: Docker + Django + Postgresql

## Semana 01:

Baseando-se [neste tutorial básico](https://github.com/docker/awesome-compose/tree/master/official-documentation-samples/django), foi feito um setup inicial de Django + Postgresql. Utilizando o Compose, subi dois serviços/containers: banco de dados e web. O primeiro utiliza uma imagem oficial do Postgresql e o segundo, uma imagem própria construída a partir do Dockerfile. Esta última contém, basicamente, o Django e suas dependências.
Foi preciso alterar os dados de acesso ao banco em settings.py: agora, o *name*, *user* e *passoword* são as variáveis de ambiente criadas pelos containers. Além disso, o host agora é o 'db', ou seja, o container do banco, e não mais o *localhost*.

### Como subir os containers:

Estando no diretório 'mysite', digite o comando:

```bash
sudo docker-compose up
```

Esse comando dá *pull* e/ou constrói as imagens solicitadas e dá *run* nos serviços. O container 'web' já executa um script que aplica as migrações e inicia o servidor Django.
Para encerrar os serviços, basta digitar o seguinte comando:

```bash
sudo docker-compose down
```

## Semana 02: