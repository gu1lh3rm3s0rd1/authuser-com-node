# Auth Users c/ Node.Js e MongoDB


Sistema básico de autenticação e gerenciamento de usuários utilizando Node.js, Express, MongoDB e Mongoose. 

Inclui funcionalidades para registro de usuários, login, autenticação baseada em token e recuperação de informações de usuários. O sistema garante o manuseio seguro de senhas com bcrypt e utiliza JWT para autenticação de usuários.

- **Registro de Usuários**: Registro de um novo usuário com nome de usuário, email e senha.
- **Login de Usuários**: Autenticação de um usuário com email e senha.
- **Autenticação baseada em Token**: Rotas seguras com tokens JWT.
- **Gerenciamento de Usuários**: Recuperação de uma lista de usuários e informações específicas de usuários.
- **Tratamento de Erros**: Mensagens de erro apropriadas para validação e erros de autenticação.

## Pré-requisitos

- Node.js
- npm (Node Package Manager)
- MongoDB

## Instalação

1. Clone o repositório:

```bash
   git clone https://github.com/seuusuario/seu-repo.git
```
2. Navegue até o diretório do projeto:

```bash
   cd seu-repo
```
3. Instale os pacotes necessários:

```bash
   npm install express bcryptjs jsonwebtoken mongoose dotenv
```
4. Crie um arquivo `.env` no diretório raiz e adicione sua URI do MongoDB e o segredo do JWT:

```env
   MONGODB_URI=sua_string_de_conexão_mongodb
   SECRET=seu_segredo_jwt
```

## Uso

Inicie o servidor:

```bash
   npm start
```

O servidor estará rodando na porta 3000. Você pode testar os endpoints usando ferramentas como Postman ou Thunder Client.

## Endpoints

### `GET /`

- **Descrição**: Endpoint básico para verificar se o servidor está em execução.
- **Resposta**: 'Hello World'

### `GET /users`

- **Descrição**: Recupera uma lista de todos os usuários.
- **Resposta**: Array JSON de usuários.

### `POST /auth/register`

- **Descrição**: Registra um novo usuário.
- **Corpo da Requisição**:
```json
  {
      "username": "seu_username",
      "email": "seu_email",
      "password": "sua_senha",
      "confirmpassword": "sua_senha"
  }
```
- **Resposta**: Objeto JSON do novo usuário registrado ou uma mensagem de erro.

### `POST /auth/login`

- **Descrição**: Realiza o login de um usuário.
- **Corpo da Requisição**:
```json
  {
      "email": "seu_email",
      "password": "sua_senha"
  }
```
- **Resposta**: Objeto JSON com uma mensagem de sucesso e o token JWT ou uma mensagem de erro.

### `GET /user/:id`

- **Descrição**: Recupera informações de um usuário específico pelo ID (rota protegida).
- **Headers**:
```json
  {
      "Authorization": "Bearer seu_jwt_token"
  }
```
- **Resposta**: Objeto JSON do usuário ou uma mensagem de erro.

## Middleware

### `checkToken`

- **Descrição**: Função middleware para validar o token JWT nos cabeçalhos da requisição.
- **Uso**: Aplicado a rotas protegidas para garantir que apenas usuários autenticados possam acessá-las.

## Tratamento de Erros

- **Registro de Usuário**: Lida com campos faltantes, senha incompatível e email duplicado.
- **Login de Usuário**: Lida com campos faltantes, usuário não encontrado e senha inválida.
- **Validação de Token**: Lida com token ausente ou inválido.

## Testes

Você pode testar os endpoints da API usando ferramentas como Postman ou Thunder Client.

1. **Registro de Usuário**: Envie uma requisição POST para `/auth/register` com os campos necessários.
2. **Login de Usuário**: Envie uma requisição POST para `/auth/login` com o email e a senha.
3. **Recuperar Usuários**: Envie uma requisição GET para `/users`.
4. **Recuperar Usuário por ID**: Envie uma requisição GET para `/user/:id` com o token JWT no cabeçalho de autorização.

## Pacotes

````bash
    npm install express bcrypt jsonwebtoken mongoose dotenv
````

- [Express](https://expressjs.com/)
- [Mongoose](https://mongoosejs.com/)
- [bcrypt.js](https://www.npmjs.com/package/bcryptjs)
- [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken)
- [dotenv](https://www.npmjs.com/package/dotenv)
