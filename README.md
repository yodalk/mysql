# mysql
Aprendendo a usar o banco de dados MYSQL

## Mini tutorial básico de MYSQL
Um mini-tutorial para aprender a usar o básico do MYSQL ou refrescar a memória.

## O que é um banco de dados MYSQL

O MySQL é um sistema de gerenciamento de banco de dados relacional (RDBMS) de código aberto amplamente utilizado para armazenar, organizar e gerenciar grandes quantidades de dados. Ele é distribuído sob a licença GPL (General Public License) e pode ser executado em vários sistemas operacionais, incluindo Windows, Linux e macOS.

O MySQL utiliza a linguagem SQL (Structured Query Language) para consultar e manipular dados em um banco de dados relacional. Ele é capaz de lidar com grandes volumes de dados e é escalável para atender às necessidades de diferentes empresas e organizações. O MySQL também oferece recursos avançados de segurança e backup, permitindo que os usuários protejam seus dados e os recuperem em caso de perda.

O MySQL é usado em muitos aplicativos da web e é especialmente popular em combinação com a linguagem de programação PHP. Ele é usado para armazenar informações em muitos tipos diferentes de aplicativos, desde pequenos sites pessoais até grandes empresas de comércio eletrônico e organizações governamentais.

## O Básico sobre a linguagem SQL

Entendendo as nomenclaturas usadas no gerenciamento do MYSQLl e na sua
documentação oficial:

-   DDL - Data Definition Linguage - Linguagem de Definição de Dados

-   DML - Data Manipulation Linguage - Linguagem de Manipulação de Dados

-   DCL - Data Control Linguage - Linguagem de Controle de Dados

-   DTL - Data Transaction Linguage - Linguagem de Transação de Dados

-   DQL - Data Query Linguage - Linguagem de Consulta de Dados


## Como criar um usuário para o banco de dados?
vamos seguir as etapas simples para criar um novo usuário para o nosso banco de dados e aderir privilégios para que o mesmo possa manipular os dados.

**Etapas:**

1\. Acessar o MYSQL pela linha de comando

2\. Acessar o Banco de Dados como administrador (root)

```
$mysql --u root --p
```

3\. Para criar um novo usuário basta digitar:
```
CREATE USER 'nomedousuario'@'localhost' IDENTIFIED BY 'senha';
```

 4\. Garanta privilégios ao usuário que foi criado:

```
GRANT ALL PRIVILEGES ON \* . \* TO 'nomedousuario'@'localhost';
```

 5\. Para ter efeito imediato:

```
 FLUSH PRIVILEGES;
```

 > Uma vez feito isso o usuário foi criado com sucesso e garantimos

> todos os privilégios ao novo usuário que criamos.
>
> Nota: garantindo privilégios dessa forma estamos habilitando todos os
> privilégios ao novo usuário que criamos, tenha isso em mente ao usar
> esse comando.


## Garantindo privilégios separadamente para o usuário do Mysql

-   CREATE - habilita o usuário a criar um banco de dados ou tabelas

-   SELECT - permite o usuário requirir os dados

-   INSERT - permite o usuário adicionar novos usuários as tabelas

-   UPDATE - permite que usuários modifiquem as entradas nas tabelas
    existentes

-   DELETE - habilita o usuário a remover entradas das tabelas

-   DROP - permite que o usuário delete entradas, banco de dados e
    tabelas


Para usar qualquer uma dessa opções, basta substituir o PERMISSION_TYPE
por qualquer um dos comandos propriamente descritos acima. Para aplicar
múltiplos privilégios, separe-os com virgula. Por exemplo, podemos
assinar CREATE e SELECT para o usuário não-root do MYSQL com esse
comando:

GRANT SELECT, CREATE ON \* . \* TO 'usuario'@'localhost';

Algumas vezes você pode querer retirar alguns privilégios de usuário e
para isso basta digitar:

REVOKE PERMISSION_TYPE ON database_name.table_name FROM
'nomedeusuario'@'localhost'

Por exemplo podemos remover todos os privilégios da seguinte forma:

REVOKE ALL PRIVILEGES ON \* . \* FROM 'nomedeusuario'@'localhost';

E finalmente podemos deletar todo banco de dados:

DROP USER 'nomedeusuario'@'localhost';

**Nota:** Lembre-se que você precisa ter privilégios de root para usar
esses comandos. Você também sempre pode usar o FLUSH PRIVILEGES para ter
efeito imediato depois que fizer suas alterações.

**Mostrando os privilégios de usuário parar um usuário do MYSQL**

SHOW GRANTS FOR 'nomedeusuario'@'localhost';
