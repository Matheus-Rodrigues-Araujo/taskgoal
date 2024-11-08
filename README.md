# TASKGOAL

Aplicação Fullstack para gerenciamento de tarefas com funcionalidades completas de CRUD, interface responsiva, tema personalizado e efeito Drag and Drop.

# Funcionalidades

- Criar, atualizar, remover e visualizar tarefas
- Drag and Drop
- Alternar entre tema claro e escuro

https://github.com/user-attachments/assets/37083101-a7c4-45f4-aa7d-9a3a59dd1646

## Tecnologias Utilizadas

- **Frontend:** React, Next.js, JavaScript, TypeScript, ContextAPI
- **Backend:** Nest.js, Node.js, Prisma (ORM)
- **Ferramentas:** Docker, Docker Compose
- **Banco de dados:** PostgreSQL

## Instalação

Para rodar a aplicação localmente, siga os passos abaixo:

### Pré-requisitos

- Node.js, cross-env e npm instalados
- PostgreSQL instalado

1. Clonar o repositório

```bash
$ git clone --recurse-submodules https://github.com/Matheus-Rodrigues-Araujo/taskgoal.git
```

2. Instale as dependências em ambos os diretórios client/ e server/

```bash
$ npm install
```

3. Configuração de server:

No diretório `server/`, crie um arquivo `.env.development` com o conteúdo abaixo:

```bash
NODE_ENV=development

DATABASE_URL="postgresql://postgres:password@localhost:5433/testdb?schema=public"
FRONTEND_URL="http://localhost:3000"
```

    OBS:
    - DATABASE_URL é a conexão com o banco de dados que o Prisma se conecta
    - FRONTEND_URL é a conexão com o frontend, que é permitida com CORS no backend

4. Configuração de client:

No diretório `client/`, crie um arquivo `.env.local` com o conteúdo abaixo:

```bash
NEXT_PUBLIC_API_URL="http://localhost:8000/api"
```

5. Instale o PostgreSQL: https://www.enterprisedb.com/downloads/postgres-postgresql-downloads

Execute esse comando para verificar se a instalação foi concluída com sucesso

```bash
$ psql --version
```

5. Executando `server/`:

```bash
$ npm run start:dev
```

6. Executando `client/`:

```bash
$ npm run dev
```

7. Executando o Postgres:

   Abra um terminal e execute esses comandos:

   1. Inicie conexão

   ```bash
   psql -U postgres -p 5433
   ```

   2. Crie o banco de daos

   ```bash
   CREATE DATABASE testdb;
   ```

   3. Conecte-se ao banco criado

   ```bash
   \c testdb;
   ```

   OBS: Para consultar os dados, utilize esse comando quando estiver conectado com o banco

   ```bash
       SELECT * FROM "Task";
   ```

8. Acessando a aplicação:

   - Frontend: http://localhost:3000/
   - Backend: http://localhost:8000/api/tasks

## Docker

Para facilitar o setup da aplicação, você pode usar Docker para rodar o backend, frontend e banco de dados em containers.

### Requisitos

- Docker e Docker Compose instalados
- Se já tive o Docker Desktop já vai funcionar também

1. No diretório `server/`, crie um arquivo `.env.production` com o conteúdo abaixo:

```bash
NODE_ENV=production

POSTGRES_USER=prisma
POSTGRES_PASSWORD=mystrongpassword
POSTGRES_DB=taskdb

DB_HOST=postgres
DB_PORT=5432
DB_SCHEMA=taskdb

DATABASE_URL=postgresql://${POSTGRES_USER}:${POSTGRES_PASSWORD}@${DB_HOST}:${DB_PORT}/${POSTGRES_DB}?schema=${DB_SCHEMA}

PORT=8000

FRONTEND_URL=http://localhost:3000
```

2. No diretório `client/`, crie um arquivo `.env.production` com o conteúdo abaixo:

```bash
NEXT_PUBLIC_API_URL=http://taskgoal-api:8000/api
```

3. Execute os containers:

No diretório raiz do projeto, execute:

```bash
docker-compose up --build
```

4. Acessando a aplicação via Docker:

   - Frontend: http://localhost:3000/
   - Backend: http://localhost:8000/api/tasks


## Observações

- Caso o Prisma não iniciou, execute:

```bash
docker exec -it taskgoal-api sh
npx prisma migrate dev  # ou outro comando de migração de sua preferência
```

- Caso tenha ocorrido algum problema ao se conectar a network:
    
Abra um terminal e execute esse comando:
```bash
    docker network create task-network
```

Execute esse comando para ver se a network foi criada:
```bash
    docker network ls
```