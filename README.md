# Projeto kube-news

### Objetivo
O projeto Kube-news é uma aplicação escrita em NodeJS e tem como objetivo ser uma aplicação de exemplo pra trabalhar com o uso de containers.

### Configuração
Pra configurar a aplicação, é preciso ter um banco de dados Postgre e pra definir o acesso ao banco, configure as variáveis de ambiente abaixo:

DB_DATABASE => Nome do banco de dados que vai ser usado.

DB_USERNAME => Usuário do banco de dados.

DB_PASSWORD => Senha do usuário do banco de dados.

DB_HOST => Endereço do banco de dados.

### Criando a rede
```
docker network create kube_news_net
```
### Criando volume para o BD
```
docker volume create kubenews_vol
```

### Criando o banco de dados Postegres
```
docker run -d -p 5432:5432 --name postgres --network kube_news_net -e POSTGRES_PASSWORD=Pg123 -e POSTGRES_USER=kubenews -e POSTGRES_DB=kubenews -v kubenews_vol:/var/lib/postgresql/data postgres:12.17
```
### Rodando a aplicação 
```
docker run -d -p 8080:8080 --name kube_news -e DB_DATABASE=kubenews -e DB_USERNAME=kubenews -e DB_PASSWORD=Pg123 -e DB_HOST=postgres --network kube_news_net jancunha/docker-kn:v1
```
