<div align="center">
    <h1>Ambiente de desenvolvimento</h1>
    <p>
        Ambiente de desenvolvimento para um MVC com PHP 8, PostgreSQL e pgAdmin
    </p> 
    <br>
</div>

<hr>

## Table of Contents

- [O Projeto](#O-Projeto)
- [Estrutura](#Estrutura)
- [Containers utilizados](#Containers-utilizados)
- [Portas utilizadas](#Portas-utilizadas)
    - [Alterar porta PHP](#Alterar-porta-PHP)
    - [Alterar porta pgAdmin](#Alterar-porta-pgAdmin)
    - [Alterar porta PostgreSQL](#Alterar-porta-PostgreSQL)
- [Nomes dos containers](#Nomes-dos-containers)
    - [Alterar nome PHP](#Alterar-nome-PHP)
    - [Alterar nome pgAdmin](#Alterar-nome-pgAdmin)
    - [Alterar nome PostgreSQL](#Alterar-nome-PostgreSQL)
- [Iniciar os containers](#Iniciar-os-containers)
- [Parar os containers](#Parar-os-containers)

## O Projeto

O projeto consiste em um ambiente para desenvolvimento PHP. <br>
Ele foi feito principalmente para um projeto com arquitetura MVC <br>
Com isso você abstrai a necessidade de ter as tecnologias instaladas no seu computador.  

## Estrutura
```shell
  .
  ├── docker
  │   └── dockerfile
  ├── public
  │   └── index.php
  ├── sql
  └── .gitignore
  └── docker-compose.yml
  └── README.md
```

## Containers utilizados
O projeto utiliza os containers do PHP 8, Composer, PostgreSQL e pgAdmin.

## Portas utilizadas
> O **PHP 8** alocará a sua porta **8080** <br>
> O **pgAdmin** alocará a sua porta **2020** <br>
> O **PostgreSQL** alocará a sua porta **5432**

Caso queira altera as portas alocadas basta editar o arquivo ``docker-compose.yml``

#### Alterar porta PHP
```yaml
server:
    ports:
      - "8080:nova-porta"  
```

#### Alterar porta pgAdmin
```yaml
pgadmin-compose:
    ports:
      - "16543:nova-porta"
```

#### Alterar porta PostgreSQL
```yaml
postgres-compose:
    ports:
      - "15432:nova-porta"
```

## Nomes dos containers
> O **PHP 8** utilizará o nome **project-server** <br>
> O **pgAdmin** utilizará o nome **project-pgadmin** <br>
> O **PostgreSQL** utilizará o nome **project-postgre** <br>

Caso queira altera os nomes utilizados basta editar o arquivo ``docker-compose.yml``

#### Alterar nome PHP
```yaml
server:
  container_name: project-server  
```

#### Alterar nome pgAdmin
```yaml
pgadmin-compose:
  container_name: project-pgadmin
```

#### Alterar nome PostgreSQL
```yaml
postgres-compose:
  container_name: project-postgre
```

## Iniciar os containers

Para iniciar os container você só precisa rodar os seguintes comandos no terminal:
```sell
docker-compose build
```

```sell
docker-compose up
```

Pronto, agora você pode acessar o seu servidor php no endereço [http://localost:8080](http://localost:8080) e o pgAdmin no endereço [http://localost:2020](http://localost:2020)

## Parar os containers
Para parar os containers você precisa rodar o seguinte comando no terminal

```shell
docker stop project-postgre project-pgadmin project-server
```

>Aviso: Caso tenha alterado o nome dos containers é necessário alterar no comando acima 