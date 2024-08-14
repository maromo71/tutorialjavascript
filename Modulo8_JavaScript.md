
# Módulo 8: Autenticação e Autorização em Aplicações Node.js

## 8.1 Introdução

**Objetivo do Módulo:**  
Neste módulo, você aprenderá a implementar autenticação e autorização em suas aplicações Node.js. Ao final deste módulo, você será capaz de criar um sistema de login seguro, proteger rotas com autenticação e gerenciar permissões de usuário usando JSON Web Tokens (JWT).

## 8.2 Contexto do Módulo

**O que é Autenticação e Autorização?**  
- **Autenticação:** O processo de verificar a identidade de um usuário. Em termos práticos, isso geralmente envolve validar um nome de usuário e senha.
- **Autorização:** O processo de verificar se um usuário autenticado tem permissão para acessar certos recursos ou realizar determinadas ações dentro de uma aplicação.

**Por que Implementar Autenticação e Autorização?**
- **Segurança:** Proteger dados e recursos sensíveis, garantindo que apenas usuários autorizados tenham acesso.
- **Controle de Acesso:** Diferenciar entre usuários com diferentes níveis de permissões, como administradores e usuários regulares.

**Aplicação Prática:**
- **Criação de Sistema de Login:** Implementar login e logout para usuários.
- **Proteção de Rotas:** Restringir o acesso a certas rotas da aplicação para usuários autenticados.
- **Uso de JWT:** Utilizar JSON Web Tokens para autenticar usuários e manter sessões seguras.

## 8.3 Conceitos Importantes

**1. JSON Web Tokens (JWT):**
- **O que é JWT?**
  JWT é um padrão aberto para autenticação entre duas partes, como um cliente e um servidor. Ele é usado para verificar a autenticidade do usuário de forma segura e eficiente.

- **Estrutura de um JWT:**
  - **Header:** Contém informações sobre o tipo de token e o algoritmo de assinatura.
  - **Payload:** Contém as informações do usuário e outros dados, como permissões.
  - **Signature:** Uma assinatura criptográfica que valida a autenticidade do token.

- **Instalação do Pacote JWT:**
  ```bash
  npm install jsonwebtoken --save
  ```

**2. Criação de um Sistema de Login:**
- **Implementando o Login:**
  - Crie uma rota para autenticar o usuário e gerar um token JWT:
    ```javascript
    const express = require('express');
    const jwt = require('jsonwebtoken');
    const bcrypt = require('bcryptjs');
    const app = express();

    const usuarios = [
        { id: 1, nome: 'admin', senha: bcrypt.hashSync('123456', 8), role: 'admin' },
        { id: 2, nome: 'user', senha: bcrypt.hashSync('123456', 8), role: 'user' }
    ];

    app.post('/login', (req, res) => {
        const { nome, senha } = req.body;
        const usuario = usuarios.find(u => u.nome === nome);

        if (!usuario) {
            return res.status(404).send('Usuário não encontrado.');
        }

        const senhaValida = bcrypt.compareSync(senha, usuario.senha);
        if (!senhaValida) {
            return res.status(401).send('Senha inválida.');
        }

        const token = jwt.sign({ id: usuario.id, role: usuario.role }, 'segredo', {
            expiresIn: 86400 // 24 horas
        });

        res.status(200).send({ auth: true, token });
    });
    ```

**3. Proteção de Rotas com Middleware:**
- **Criando Middleware para Verificar Token:**
  ```javascript
  function verificaToken(req, res, next) {
      const token = req.headers['x-access-token'];
      if (!token) {
          return res.status(403).send('Nenhum token fornecido.');
      }

      jwt.verify(token, 'segredo', (err, decoded) => {
          if (err) {
              return res.status(500).send('Falha ao autenticar token.');
          }
          req.userId = decoded.id;
          next();
      });
  }
  ```

- **Aplicando Middleware em Rotas Protegidas:**
  ```javascript
  app.get('/dashboard', verificaToken, (req, res) => {
      res.status(200).send('Bem-vindo ao Dashboard!');
  });
  ```

**4. Implementando Autorização:**
- **Restringindo Acesso por Função de Usuário:**
  ```javascript
  function verificaAdmin(req, res, next) {
      if (req.role !== 'admin') {
          return res.status(403).send('Acesso negado. Você não é um administrador.');
      }
      next();
  }

  app.get('/admin', [verificaToken, verificaAdmin], (req, res) => {
      res.status(200).send('Bem-vindo, Admin!');
  });
  ```


## 8.4 Exemplo: Sistema de Autenticação e Autorização

**Exemplo Prático: Criando um Sistema de Login com Proteção de Rotas**

Neste exemplo, você criará um sistema simples de autenticação e autorização usando JWT. Usuários poderão fazer login, acessar um dashboard protegido e administrar recursos dependendo de suas permissões.

**Passos:**

1. **Configuração Inicial:**
   - Crie um novo projeto Node.js:
     ```bash
     npm init -y
     ```
   - Instale as dependências necessárias:
     ```bash
     npm install express jsonwebtoken bcryptjs --save
     ```
   - Crie um arquivo chamado `auth.js` e adicione o seguinte código:
     ```javascript
     const express = require('express');
     const jwt = require('jsonwebtoken');
     const bcrypt = require('bcryptjs');
     const app = express();

     const usuarios = [
         { id: 1, nome: 'admin', senha: bcrypt.hashSync('123456', 8), role: 'admin' },
         { id: 2, nome: 'user', senha: bcrypt.hashSync('123456', 8), role: 'user' }
     ];

     app.use(express.json());

     function verificaToken(req, res, next) {
         const token = req.headers['x-access-token'];
         if (!token) {
             return res.status(403).send('Nenhum token fornecido.');
         }

         jwt.verify(token, 'segredo', (err, decoded) => {
             if (err) {
                 return res.status(500).send('Falha ao autenticar token.');
             }
             req.userId = decoded.id;
             req.role = decoded.role;
             next();
         });
     }

     function verificaAdmin(req, res, next) {
         if (req.role !== 'admin') {
             return res.status(403).send('Acesso negado. Você não é um administrador.');
         }
         next();
     }

     app.post('/login', (req, res) => {
         const { nome, senha } = req.body;
         const usuario = usuarios.find(u => u.nome === nome);

         if (!usuario) {
             return res.status(404).send('Usuário não encontrado.');
         }

         const senhaValida = bcrypt.compareSync(senha, usuario.senha);
         if (!senhaValida) {
             return res.status(401).send('Senha inválida.');
         }

         const token = jwt.sign({ id: usuario.id, role: usuario.role }, 'segredo', {
             expiresIn: 86400 // 24 horas
         });

         res.status(200).send({ auth: true, token });
     });

     app.get('/dashboard', verificaToken, (req, res) => {
         res.status(200).send('Bem-vindo ao Dashboard!');
     });

     app.get('/admin', [verificaToken, verificaAdmin], (req, res) => {
         res.status(200).send('Bem-vindo, Admin!');
     });

     app.listen(3000, () => {
         console.log('Servidor rodando na porta 3000');
     });
     ```

2. **Testando a Aplicação:**
   - Execute a aplicação:
     ```bash
     node auth.js
     ```
   - Use o Postman ou `curl` para testar o login e acessar as rotas protegidas:
     - **POST /login**: Faça login com um usuário e obtenha o token JWT.
     - **GET /dashboard**: Acesse o dashboard com o token JWT.
     - **GET /admin**: Acesse a rota de administrador (apenas para usuários com função `admin`).

**Explicação:**
- A aplicação implementa autenticação básica usando JWT e protege rotas com middleware.
- Diferentes permissões são gerenciadas com base na função do usuário (`role`).

## 8.5 Exercícios

**Exercício 1: Criando um Sistema de Login**
- **Objetivo:** Implementar um sistema de login básico.
- **Instruções:** Crie um sistema de login que autentique usuários e retorne um token JWT. Proteja uma rota com este token e exiba uma mensagem de boas-vindas ao usuário.

**Exercício 2: Protegendo Rotas com JWT**
- **Objetivo:** Praticar a proteção de rotas com JWT.
- **Instruções:** Crie várias rotas na sua aplicação e proteja algumas delas, permitindo o acesso apenas para usuários autenticados.

**Exercício 3: Implementando Autorização**
- **Objetivo:** Gerenciar permissões de usuário com base em funções.
- **Instruções:** Implemente uma função de verificação que permita acesso a certas rotas apenas para usuários com determinadas permissões (por exemplo, apenas administradores podem acessar a rota `/admin`).

**Exercício 4: Expiração de Token e Logout**
- **Objetivo:** Lidar com expiração de tokens JWT e implementar logout.
- **Instruções:** Configure um token JWT para expirar após um certo tempo e implemente uma rota de logout que invalide o token.

### Conclusão do Módulo 8

Neste módulo, você aprendeu a implementar autenticação e autorização em uma aplicação Node.js usando JSON Web Tokens (JWT). Você criou um sistema de login seguro, protegeu rotas da aplicação e gerenciou permissões de usuário.


