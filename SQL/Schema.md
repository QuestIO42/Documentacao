# O que é um Schema?

É uma coleção lógica de objetos dentro de um banco de dados, ou seja, tem como funcionalidade agrupar objetos que tenham similaridades entre si. Isso é feito tanto por questões organizacionais e de performance, quanto para melhorar o gerenciamento da segurança do banco de dados. 

As databases PostgreSQL têm por padrão um schema chamado "public", e as tabelas que são criadas sem referência a nenhum schema específicos são inseridas nele.

# Visualização de um Schema com o comando \d

Primeiramente, é preciso estar conectado ao banco de dados através do **psql**, que é uma interface do PostgreSQL que pode ser acessada através do terminal e é usada para interagir com databases de maneira rápida e direta. 

Para isso, é preciso baixar o [PostgreSQL](https://www.postgresql.org/download/). Depois, para que o sistema entenda 'psql' como um comando, adicionar o seguinte caminho às variáveis de ambiente (variáveis de ambiente -> variáveis do sistema -> Path (editar) -> Novo):

    C:\Program Files\PostgreSQL\16\bin

Para se conectar ao banco de dados desejado no psql, pode-se usar o seguinte comando no terminal do sistema operacional:

     psql -U seu_usuario -d seu_banco_de_dados 

Outra opção é apenas digitar

    psql -U seu_usuario

E se conectar à tabela desejada usando o comando:

    \c seu_banco_de_dados

<!-- Para listar todas as databases existentes:

    \l 
-->

**Comando \d**

O comando '\d' signica 'describe' e tem a funcionalidade de listar as relações da database, sendo uma forma rápida e útil de visualizar o schema. Portanto, digitando apenas o comando \d, são retornados todos os objetos (tabelas, views, sequências e índices) daquela database.

Exemplo (corresponde à database criada pelo backend Django):

```sql
apidjango=# \d
                           List of relations
 Schema |                  Name                   |   Type   |  Owner   
--------+-----------------------------------------+----------+----------
 public | app_answer                              | table    | apiadmin
 public | app_category                            | table    | apiadmin
 public | app_course                              | table    | apiadmin
 public | app_post                                | table    | apiadmin
 public | app_question                            | table    | apiadmin
 public | app_quiz                                | table    | apiadmin
 public | app_quizquestion                        | table    | apiadmin
 public | app_quizquestion_id_seq                 | sequence | apiadmin
 public | app_user                                | table    | apiadmin
 public | app_user_groups                         | table    | apiadmin
 public | app_user_groups_id_seq                  | sequence | apiadmin
 public | app_user_user_permissions               | table    | apiadmin
 public | app_user_user_permissions_id_seq        | sequence | apiadmin
 public | app_usercourse                          | table    | apiadmin
 public | app_usercourse_id_seq                   | sequence | apiadmin
 public | app_userquizquestion                    | table    | apiadmin
 public | auth_group                              | table    | apiadmin
 public | auth_group_id_seq                       | sequence | apiadmin
 public | auth_group_permissions                  | table    | apiadmin
 public | auth_group_permissions_id_seq           | sequence | apiadmin
 public | auth_permission                         | table    | apiadmin
 public | auth_permission_id_seq                  | sequence | apiadmin
 public | django_admin_log                        | table    | apiadmin
 public | django_admin_log_id_seq                 | sequence | apiadmin
 public | django_content_type                     | table    | apiadmin
 public | django_content_type_id_seq              | sequence | apiadmin
 public | django_migrations                       | table    | apiadmin
 public | django_migrations_id_seq                | sequence | apiadmin
 public | django_session                          | table    | apiadmin
 public | token_blacklist_blacklistedtoken        | table    | apiadmin
 public | token_blacklist_blacklistedtoken_id_seq | sequence | apiadmin
 public | token_blacklist_outstandingtoken        | table    | apiadmin
 public | token_blacklist_outstandingtoken_id_seq | sequence | apiadmin
(33 rows)
```

Adicionando o nome de uma tabela após o comando \d, são retornadas informações como os nomes e os tipos das colunas da tabela especificada.

```sql
apidjango=# \d app_user
                           Table "public.app_user"
      Column      |           Type           | Collation | Nullable | Default 
------------------+--------------------------+-----------+----------+---------
 password         | character varying(128)   |           | not null | 
 last_login       | timestamp with time zone |           |          | 
 is_superuser     | boolean                  |           | not null | 
 username         | character varying(150)   |           | not null | 
 first_name       | character varying(150)   |           | not null | 
 last_name        | character varying(150)   |           | not null | 
 is_staff         | boolean                  |           | not null | 
 is_active        | boolean                  |           | not null | 
 date_joined      | timestamp with time zone |           | not null | 
 id               | uuid                     |           | not null | 
 full_name        | character varying(255)   |           | not null | 
 college_register | character varying(10)    |           |          | 
 role             | smallint                 |           | not null | 
 account_status   | smallint                 |           |          | 
 xp_count         | integer                  |           |          | 
 email            | character varying(254)   |           | not null | 
```

Além disso, há outras variações de comandos de descrição que servem para retornar outros tipos de informações. Elas podem ser vistas [aqui](https://www.commandprompt.com/education/postgresql-basic-psql-commands/).

O comando \dt, por exemplo, mostra apenas as tabelas do banco de dados (sendo uma versão mais enxuta do comando \d):

```sql
apidjango-# \dt
                      List of relations
 Schema |               Name               | Type  |  Owner   
--------+----------------------------------+-------+----------
 public | app_answer                       | table | apiadmin
 public | app_category                     | table | apiadmin
 public | app_course                       | table | apiadmin
 public | app_post                         | table | apiadmin
 public | app_question                     | table | apiadmin
 public | app_quiz                         | table | apiadmin
 public | app_quizquestion                 | table | apiadmin
 public | app_user                         | table | apiadmin
 public | app_user_groups                  | table | apiadmin
 public | app_user_user_permissions        | table | apiadmin
 public | app_usercourse                   | table | apiadmin
 public | app_userquizquestion             | table | apiadmin
 public | auth_group                       | table | apiadmin
 public | auth_group_permissions           | table | apiadmin
 public | auth_permission                  | table | apiadmin
 public | django_admin_log                 | table | apiadmin
 public | django_content_type              | table | apiadmin
 public | django_migrations                | table | apiadmin
 public | django_session                   | table | apiadmin
 public | token_blacklist_blacklistedtoken | table | apiadmin
 public | token_blacklist_outstandingtoken | table | apiadmin
(21 rows)
```

# Comparando as visualizações para cada backend

>Para cada backend, haverá em sua respectiva seção a visualização de seu schema e de sua tabela User. Decidi não colocar de todas as tabelas porque ficaria muita informação, mas, quando as databases estiverem completas, farei um resumo das diferenças percebidas em cada database.

# Django para uma database em PostgreSQL

**Explicação de como tabelas são criadas com Django**

As tabelas são criadas em um arquivo chamado ['models.py'](https://github.com/QuestIO42/App-backend-django/blob/main/app/models.py). Cada modelo é uma classe que representa uma tabela no banco de dados. 

```python
class User(AbstractUser):
    id = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False)
    full_name = models.CharField(max_length=255)
    college_register = models.CharField(max_length=10, null=True, blank=True)
    role = models.SmallIntegerField(default=0, choices=USER_ROLE)
    account_status = models.SmallIntegerField(default=0, null=True)
    xp_count = models.IntegerField(null=True)
    email = models.EmailField(("email address"), blank=False)
    def __str__(self):
        return self.username
```

Essa é a classe da tabela User do banco de dados e cada variável é equivalente a um atributo da tabela. Os parâmetros dão informações sobre os atributos, como o número máximo de caracteres, o valor default e se o campo pode ser nulo ou não.

Para que a tabela realmente seja criada no banco de dados, é preciso executar os chamados comandos de migração em um terminal:

    python manage.py makemigrations
    // Gera automaticamente um arquivo que descreve as mudanças a serem realizadas no esquema do banco de dados

    python manage.py migrate
    // Aplica as mudanças no banco de dados

**Visualização da database**

Eu segui o [tutorial](https://github.com/QuestIO42/App-backend-django/blob/main/README.md) de como rodar a aplicação e, depois de fazer o passo-a-passo necessário, a visualização obtida com o comando \d pode ser vista nos exemplos [dessa seção](#visualização-de-um-schema-com-o-comando-d).


# Node para uma database em PostgreSQL

1º passo: Clonei o repositório 'App-backend-Node.js'

2º passo: Em seguida, para configurar o que era necessário, eu segui [a documentação do Prisma](https://www.prisma.io/docs/getting-started/setup-prisma/start-from-scratch/relational-databases-typescript-postgresql). (Como eu não sabia o que precisava e o que já estava feito no projeto, eu apenas segui todos os passos até a migração, com exceção do primeiro passo de criar um diretório, porque isso já é feito clonando o repositório).

3º passo: Criei o banco e o usuário com as seguintes linhas:

```sql
CREATE DATABASE apidb_node;
CREATE USER apiadmin WITH ENCRYPTED PASSWORD 'adminadmin';
GRANT ALL PRIVILEGES ON DATABASE apidb_node TO apiadmin;

ALTER USER apiadmin WITH CREATEDB;
```

> As três primeiras linhas são iguais às existentes no projeto em Django. A quarta eu adicionei porque estava tendo problemas com permissão durante a etapa de migração.

4º passo: Criei um arquivo '.env' e defini a url da database para poder conectar o projeto ao banco de dados. Para que os backends sejam o mais similiar possível entre si, o ideal é que ela fique assim:

```sql
DATABASE_URL = "postgresql://apiadmin:adminadmin@localhost:5342/apidb?schema=public"
```

> Usei como base o arquivo .env.example

5º passo: Executei as migrações com o comando:

    npx prisma migrate dev --name init

**Visualização da database** 

Visualização do schema:

```sql
apidb_node=# \d
                  Lista de relaþ§es
 Esquema |        Nome        |   Tipo    |   Dono
---------+--------------------+-----------+----------
 public  | User               | tabela    | apiadmin
 public  | User_id_seq        | sequÛncia | apiadmin
 public  | _prisma_migrations | tabela    | apiadmin
(3 linhas)
```

Visualização da tabela User: (Precisa digitar o nome da tabela com aspas)

```sql
apidb_node=# \d "User"
                                                Tabela "public.User"
      Coluna      |              Tipo              | OrdenaþÒo | Pode ser nulo |               PadrÒo
------------------+--------------------------------+-----------+---------------+------------------------------------
 id               | integer                        |           | not null      | nextval('"User_id_seq"'::regclass)
 fullname         | character varying(255)         |           | not null      |
 username         | text                           |           | not null      |
 password         | character varying(64)          |           | not null      |
 college_register | character varying(10)          |           | not null      |
 user_role        | "UserRole"                     |           | not null      | 'USER'::"UserRole"
 entry_type       | timestamp(3) without time zone |           | not null      | CURRENT_TIMESTAMP
 account_status   | "AccountStatus"                |           | not null      | 'ACTIVE'::"AccountStatus"
 xp_count         | integer                        |           | not null      | 0
═ndices:
    "User_pkey" PRIMARY KEY, btree (id)
    "User_username_key" UNIQUE, btree (username)
```

# Spring para uma database em PostgreSQL

1º passo: Clonei o repositório "App-backend-Spring"

2º passo: Baixei a [IDEA IntelliJ](https://www.jetbrains.com/idea/download/?section=windows) (baixei a Community Edition, que é gratuita, mas dá para baixar a Ultimate, que é paga, e conseguir uma licença com o e-mail da UFSCar)

3º passo: Criei a database e o usuário 'apiadmin', aplicando as seguintes linhas no psql:

```sql
CREATE DATABASE apidb;
CREATE USER apiadmin WITH ENCRYPTED PASSWORD 'adminadmin';
GRANT ALL PRIVILEGES ON DATABASE apidb TO apiadmin;
```

4º passo: Rodei o arquivo 'QuestioApplication.java'. Isso faz com que as mudanças sejam aplicadas automaticamente ao banco de dados, não precisa fazer nenhuma migração

5º passo: Entrei no pgAdmin (ferramenta do PostgreSQL) e verifiquei se a tabela foi criada lá

**Visualização:**

Visualização do schema com comando \d:

```sql
apidb_spring=# \d
                  Lista de relaþ§es
 Esquema |        Nome         |   Tipo    |   Dono
---------+---------------------+-----------+----------
 public  | user_tb             | tabela    | apiadmin
 public  | user_tb_seq         | sequÛncia | apiadmin
 public  | xp_increment_tb     | tabela    | apiadmin
 public  | xp_increment_tb_seq | sequÛncia | apiadmin
(4 linhas)
```

Visualização da tabela User:

```sql
apidb_spring=# \d user_tb
                                Tabela "public.user_tb"
      Coluna      |              Tipo              | OrdenaþÒo | Pode ser nulo | PadrÒo
------------------+--------------------------------+-----------+---------------+--------
 id               | integer                        |           | not null      |
 account_status   | bytea                          |           |               |
 college_register | character varying(10)          |           |               |
 email            | character varying(255)         |           | not null      |
 entery_type      | timestamp(6) without time zone |           |               |
 full_name        | character varying(255)         |           |               |
 password         | character varying(64)          |           | not null      |
 user_role        | bytea                          |           |               |
 username         | character varying(25)          |           | not null      |
 xp_count         | integer                        |           | not null      |
═ndices:
    "user_tb_pkey" PRIMARY KEY, btree (id)
    "uk2dlfg6wvnxboknkp9d1h75icb" UNIQUE CONSTRAINT, btree (email)
    "uklvx22t2upvjxxc86vf5daxc71" UNIQUE CONSTRAINT, btree (username)
Referenciada por:
    TABLE "xp_increment_tb" CONSTRAINT "fkgoxfolpdvsw7n9qt9wl3fdpi8" FOREIGN KEY (id_user) REFERENCES user_tb(id)
```

# Laravel para uma database em PostgreSQL

**Explicação de como tabelas são criadas com Laravel**

Em Laravel, as tabelas são criadas em arquivos de migração e, para criar uma nova migração, é usado o seguinte comando no terminal:

    php artisan make:migration nome_migracao

Isso cria um arquivo de migração com o nome informado na pasta 'migrations' dentro de 'database'. A estrutura da tabela a ser criada deve ser colocada dentro do arquivo de migração, no método up(). 

Para aplicar as migrações, é usado o comando

    php artisan migrate


Criei um projeto Laravel para testar e segui os seguintes passos: 

Baixei php e [composer](https://getcomposer.org/download/). Em seguida, segui [este tutorial](https://supabase.com/blog/laravel-postgres).
> Para que a instalação de Laravel Breeze dê certo, foi preciso ir no arquivo `php.ini` e descomentar algumas linhas que continham extensões. As que me lembro são: curl, fileinfo, mbstring.

No arquivo .env, as configurações devem ser as seguintes:

    DB_CONNECTION=pgsql
    DB_HOST=127.0.0.1
    DB_PORT=5432
    DB_DATABASE=apidb
    DB_USERNAME=apiadmin
    DB_PASSWORD=adminadmin
    DATABASE_URL=postgres://apiadmin:adminadmin@host:5432/apidb
    
E, em seguida, apliquei o comando 'migrate' no terminal:

    php artisan migrate

<!--

O resultado obtido foi esse:

<img src = "image-5.png" class = "centralized_image">

-->

