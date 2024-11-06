# TASKGOAL

Aplicação Fullstack para cadastro de tarefas

# Funcionalidades
- Criação, atualização, remoção e visualização das tarefas
- Drag and Drop

https://github.com/user-attachments/assets/37083101-a7c4-45f4-aa7d-9a3a59dd1646

## Tecnologias
- Frontend: React, Next.js, JavaScript, TypeScript
- Backend: Nest.js, Node.js, ORM (Prisma)
- Banco de dados: PostgreSQL
## Instalação

Para rodar a aplicação localmente, siga os passos abaixo:

1. Clonar o repositório

```bash
$ git clone --recurse-submodules https://github.com/Matheus-Rodrigues-Araujo/taskgoal.git
```

2. Instalar as dependências.

Nos repositórios `client/` e `server/`, abra o terminal digite:

```bash
$ npm install
```

3. Configurar a variável de ambiente:

Em `server/`, crie um arquivo `.env` e cole essas variáveis

```bash
DATABASE_URL="postgresql://postgres:password@localhost:5433/testdb?schema=public"
FRONTEND_URL="http://localhost:3000"
```
    OBS: 
    - DATABASE_URL é a conexão com o banco de dados que o Prisma se conecta
    - FRONTEND_URL é a conexão com o frontend, que é permitida com CORS no backend

4. Instale o PostgreSQL: https://www.enterprisedb.com/downloads/postgres-postgresql-downloads

Execute esse comando para verificar se a instalação foi concluída com sucesso

```bash
$ psql --version
```

5. Executando `server/`:

```bash
$ npm run start:dev
```

6. Executando `server/`:

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
    bash
    ```
        SELECT * FROM "Task";
    ```

7. Acessando a aplicação:
   
   * Link: http://localhost:3000/
