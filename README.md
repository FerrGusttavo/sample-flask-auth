
# API de Cadastro de Usuários usando Flask

Uma API simples construída em Python, e utilizando o framework Flask, Flask-Login, SQLAlchemy e Pymysql.

## Rodando localmente

Clone o projeto

```bash
  git clone https://github.com/FerrGusttavo/sample-flask-auth
```

Entre no diretório do projeto

```bash
  cd sample-flask-auth
```

Instale as dependências

```bash
  pip install -r requirements.txt
```

Instale e execute o banco de dados

```bash
  docker-compose up -d
```

### Executando migração no banco de dados

Com o banco de dados já em execução, no seu terminal, digite o seguintes comandos

```bash
  flask shell
```
```bash
  db.create_all()
```
```bash
  db.session.commit()
```
```bash
  exit()
```

### Inicie o servidor

```bash
  python app.py
```

## Documentação da API

#### Criar um usuário

```http
  POST /users
```

- Cria um novo usuário no banco de dados.

| Parâmetro (Body)   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `username`      | `string` | **Obrigatório**. Nome do usuário a ser criado.|
| `password` | `string` | **Obrigatório**. Senha do usuário a ser criado.

#### Logar com um usuário

```http
  POST /login
```

- Busca e loga com um usuário já existente no banco de dados.

| Parâmetro (Body)   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `username`      | `string` | **Obrigatório**. Nome do usuário já existente.|
| `password` | `string` | **Obrigatório**. Senha do usuário já existente.

#### Deslogar usuário

```http
  GET /logout
```

- Desloga o usuário.

#### Retornar todos os usuários


```http
  GET /users
```

- Retorna uma lista de todos os usuários criados.

#### Retornar um usuário específico 

```http
  GET /users/<id>
```

- Retorna os detalhes de um usuário específico pelo seu id.

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `id`      | `int` | **Obrigatório**. O ID do usuário a ser retornado. |

#### Retornar o perfil do usuário

```http
  GET /me
```

- Busca e retorna o dados do usuário autenticado.

#### Atualizar senha de um usuário

```http
  PUT /users/<id>
```

- Atualiza a senha do usuário autenticado.

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `id`      | `int` | **Obrigatório**. O ID do usuário a ser atualizado. |

| Parâmetro (Body)   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `password`      | `string` | **Obrigatório**. Nova senha do usuário a ser atualizado.|

#### Deletar um usuário (Somente Admin)

```http
  DELETE /users/<id>
```

- Deleta um usuário específico com base no seu id.

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `id`      | `int` | **Obrigatório**. O ID do usuário a ser deletado. |