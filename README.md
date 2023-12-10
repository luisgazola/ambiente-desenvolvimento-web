# Ambiente LEMPP com WordPress

Este projeto oferece um ambiente de desenvolvimento Docker para aplicativos PHP com WordPress, utilizando a pilha LEMPP (Linux, Nginx, MySQL, PHP, e PostgreSQL).

## Estrutura de Diretórios

- **docker/**
  - **mongodb/**
    - mongodb-data
  - **mysql/**
    - mysql-data
    - **mysql-init/**
      - init.sql
  - **nginx/**
    - nginx.conf
  - **php/**
    - Dockerfile
  - **postgres/**
    - **postgres-data/**
    - **postgres-init/**
      - init.sql

- **docker-compose.yml**
- **env-example**
- **README.md**
- **src/**
  - config
  - controllers
  - models
  - public
  - routes
  - tests
  - views
  - wordpress

## Instruções de Uso

1. Clone este repositório:
   ```bash
	git clone https://github.com/seu-usuario/seu-repositorio.git
	cd seu-repositorio
	
## Serviços

- **Nginx**: Servidor web.
- **PHP**: PHP-FPM com extensões úteis.
- **MySQL**: Banco de dados MySQL.
- **PostgreSQL**: Banco de dados PostgreSQL.
- **MongoDB**: Banco de dados MongoDB.
- **phpMyAdmin**: Interface web para gerenciamento do MySQL.
- **Wordpress**: Plataforma de gerenciamento de conteúdo para websites.

## Configuração

1. Copie o arquivo `.env.example` para `.env` e configure as variáveis de ambiente.
2. Execute `docker-compose up -d` para iniciar os serviços.

## Acesso

- **Aplicação Web**: [http://localhost:8080](http://localhost:8080)
- **Wordpress**: [http://localhost:8081](http://localhost:8081)
	- **Usuário padrão**: admin
	- **Senha padrão**: password
- **phpMyAdmin**: [http://localhost:8888](http://localhost:8888)

## Diretórios Importantes

- `docker`: Configurações específicas para cada serviço.
- `src`: Código-fonte da aplicação.

Os seguintes comandos criam a estrutura de diretórios necessária para o projeto:

	```bash
	mkdir -p /docker/mongodb/mondodb-data
	mkdir -p /docker/mysql/mysql-data
	mkdir -p /docker/postgres/postgres-data
	mkdir -p /src/config
	mkdir -p /src/controllers
	mkdir -p /src/models
	mkdir -p /src/public
	mkdir -p /src/routes
	mkdir -p /src/tests
	mkdir -p /src/views
	mkdir -p /src/wordpress

## Comandos Úteis

- `docker-compose up -d`: Inicia os serviços em segundo plano.
- `docker-compose down`: Para e remove os serviços.

## Detalhes dos Serviços
- Nginx: Porta 8080
- PHP: Porta 9000
- MySQL: Porta 3306
- PostgreSQL: Porta 5432
- MongoDB: Porta 27017
- PhpMyAdmin: Porta 8888
- WordPress: Porta 8081

## Customizações
- Para customizar o Nginx, modifique o arquivo docker/nginx/nginx.conf.
- Para customizar o PHP, modifique o Dockerfile em docker/php/Dockerfile.

## Scripts de Inicialização de Banco de Dados

### MySQL

- O script `init.sql` dentro do diretório `docker/mysql/mysql-init` é executado quando o serviço MySQL é iniciado. Modifique este script conforme necessário para inicializar seu banco de dados MySQL com as configurações desejadas.

### PostgreSQL

- O script `init.sql` dentro do diretório `docker/postgres/postgres-init` é executado quando o serviço PostgreSQL é iniciado. Modifique este script conforme necessário para inicializar seu banco de dados PostgreSQL com as configurações desejadas.

## Contribuindo
- Contribuições são bem-vindas. Crie um problema para discutir grandes mudanças antes de enviar um pull request.

## Licença
- Este projeto é licenciado sob a Licença MIT.

## Observações

- Este ambiente é destinado apenas para desenvolvimento.
- Certifique-se de ajustar as configurações de segurança para implantação em produção.

