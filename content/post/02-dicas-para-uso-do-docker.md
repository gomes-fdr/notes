---
title: "Dicas para uso do docker"
date: 2020-05-11
slug: "dicas-para-uso-do-docker"
tags: ["wiki", "docker"]
draft: false
---

Referencias utilizadas:
[link](https://youtu.be/aHbE3pTyG-Q)

Instalar um container - docker hub

	docker pull postgres:alpine

Listar containers instalados

	docker images -a

Remover um container

	docker rmi <nome-do-container>

Iniciar um container

	docker run --name postgres-0 -e POSTGRES_PASSWORD=1234 -d -p 5432:5432 postgres:alpine

Processo docker rodando

	docker ps

Para subir uma imagem existente

	docker start postgres-0 # <container-name>

Parar o container

	 docker stop postgres-0 # <container-name>

Para entrar no container

	docker exec -it postgres-0 bash

Para acessar o banco de dados postgre dentro do container(console postgres)

	psql -U postgres

Para fazer o dump do banco do container

	docker exec -t postgres-0 pg_dumpall -a > dump_`date +%d-%m-%Y"_"%H_%M_%S`.sql
	docker exec -t postgres-0 pg_dump -a > dump_`date +%d-%m-%Y"_"%H_%M_%S`.sql

Para restaurar o banco apartir de um dump file

	cat your_dump.sql | docker exec -i your-db-container psql -U postgres

VERIFICA SE A PORTA ESTÁ EM USO

	netstat -an | grep 5432

STOP POSTGRE SERVICE

	sudo service postgresql stop

Copiar arquivo para container:

	docker cp <arquivo> <container_id>:/

Acessar o postgres do container:

	psql -h localhost -p 5432 -U postgres

Para criar um novo banco no postgre via CL:

	createdb -U <role> <nome-banco>

## Outra maneira de fazer o backup

	docker exec -u <your_postgres_user> <postgres_container_name> pg_dump -Fc <database_name_here> > db.dump

## Cuidado!

	docker exec -u <your_postgres_user> <postgres_container_name> psql -c 'DROP DATABASE <your_db_name>'

	docker exec -i -u <your_postgres_user> <postgres_container_name> pg_restore -C -d postgres < db.dump

Exemplo:

Custom format (c)

	docker exec -u labwide postgres-0 pg_dump -Fc gestam-dados > gestam-dados.dump

SQL format(p)

	docker exec -u postgres postgres-0 pg_dump -Fp gestam-dados > gestam-dados.dump

## Backup acessando o container

**copy dump into container**

	docker cp local/path/to/db.dump CONTAINER_ID:/db.dump

**shell into container**

	docker exec -it CONTAINER_ID bash

**restore it from within**

	pg_restore -U postgres -d DB_NAME --no-owner -1 /db.dump
