
# Módulo 7: Integração com Banco de Dados usando Node.js e MongoDB

## 7.1 Introdução

**Objetivo do Módulo:**  
Neste módulo, você aprenderá a integrar um banco de dados NoSQL, como o MongoDB, em sua aplicação Node.js. Ao final deste módulo, você será capaz de conectar sua aplicação a um banco de dados MongoDB, realizar operações CRUD (Create, Read, Update, Delete), e armazenar e recuperar dados de maneira eficiente.

## 7.2 Contexto do Módulo

**O que é MongoDB?**  
MongoDB é um banco de dados NoSQL orientado a documentos que armazena dados em formato JSON-like (BSON). É altamente escalável e flexível, o que o torna ideal para aplicações que lidam com grandes volumes de dados não estruturados ou semi-estruturados.

**Por que Usar MongoDB?**
- **Flexibilidade:** MongoDB permite que você armazene dados de forma mais flexível do que bancos de dados relacionais, sem a necessidade de um esquema fixo.
- **Escalabilidade:** Projetado para escalar horizontalmente, suportando grandes volumes de dados distribuídos.
- **Facilidade de Integração:** Integrar MongoDB com Node.js é simples, graças a bibliotecas como `mongoose` que facilitam a comunicação entre a aplicação e o banco de dados.

**Aplicação Prática:**
- **Conectando ao MongoDB:** Estabelecendo uma conexão com o banco de dados MongoDB.
- **Operações CRUD:** Implementação das operações básicas para manipulação de dados no banco.
- **Modelagem de Dados:** Definição de esquemas e modelos de dados utilizando `mongoose`.

## 7.3 Conceitos Importantes

**1. Instalando e Configurando o MongoDB:**
- **Instalação Local do MongoDB:**
  - Baixe e instale o MongoDB Community Edition a partir do [site oficial](https://www.mongodb.com/try/download/community).
  - Após a instalação, inicie o servidor MongoDB:
    ```bash
    mongod
    ```
- **Usando MongoDB Atlas (opcional):**
  - Para evitar a instalação local, você pode usar o MongoDB Atlas, uma solução de MongoDB hospedada na nuvem.
  - Crie uma conta no [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) e configure um novo cluster.

**2. Instalando o Mongoose:**
- **O que é o Mongoose?**
  Mongoose é uma biblioteca de modelagem de dados para MongoDB e Node.js. Ele fornece uma solução baseada em esquemas para modelar seus dados, além de validação de dados, conversão de tipos e hooks.

- **Instalação do Mongoose:**
  ```bash
  npm install mongoose --save
  ```

**3. Conectando ao MongoDB com Mongoose:**
- **Configuração da Conexão:**
  ```javascript
  const mongoose = require('mongoose');

  mongoose.connect('mongodb://localhost:27017/meuBancoDeDados', {
      useNewUrlParser: true,
      useUnifiedTopology: true
  }).then(() => {
      console.log('Conectado ao MongoDB');
  }).catch((err) => {
      console.error('Erro ao conectar ao MongoDB', err);
  });
  ```

**4. Criando Modelos de Dados:**
- **Definindo um Esquema:**
  ```javascript
  const usuarioSchema = new mongoose.Schema({
      nome: String,
      email: String,
      idade: Number,
      dataCriacao: { type: Date, default: Date.now }
  });
  ```

- **Criando um Modelo:**
  ```javascript
  const Usuario = mongoose.model('Usuario', usuarioSchema);
  ```

**5. Operações CRUD com Mongoose:**
- **Criando um Documento:**
  ```javascript
  const novoUsuario = new Usuario({
      nome: 'João Silva',
      email: 'joao.silva@example.com',
      idade: 30
  });

  novoUsuario.save().then(() => {
      console.log('Usuário salvo com sucesso!');
  }).catch((err) => {
      console.error('Erro ao salvar usuário', err);
  });
  ```

- **Lendo Documentos:**
  ```javascript
  Usuario.find().then((usuarios) => {
      console.log('Usuários encontrados:', usuarios);
  }).catch((err) => {
      console.error('Erro ao buscar usuários', err);
  });
  ```

- **Atualizando um Documento:**
  ```javascript
  Usuario.updateOne({ _id: 'idDoUsuario' }, { idade: 31 }).then(() => {
      console.log('Usuário atualizado com sucesso!');
  }).catch((err) => {
      console.error('Erro ao atualizar usuário', err);
  });
  ```

- **Deletando um Documento:**
  ```javascript
  Usuario.deleteOne({ _id: 'idDoUsuario' }).then(() => {
      console.log('Usuário deletado com sucesso!');
  }).catch((err) => {
      console.error('Erro ao deletar usuário', err);
  });
  ```

## 7.4 Exemplo: Criando uma Aplicação de Cadastro de Usuários

**Exemplo Prático: Aplicação de CRUD para Usuários**

Neste exemplo, você criará uma aplicação simples para gerenciar um cadastro de usuários, incluindo operações de criação, leitura, atualização e deleção (CRUD).

**Passos:**

1. **Configuração Inicial:**
   - Crie um novo projeto Node.js:
     ```bash
     npm init -y
     ```
   - Instale o Express e o Mongoose:
     ```bash
     npm install express mongoose --save
     ```
   - Crie um arquivo chamado `app.js` e adicione o seguinte código:
     ```javascript
     const express = require('express');
     const mongoose = require('mongoose');
     const app = express();

     mongoose.connect('mongodb://localhost:27017/cadastroUsuarios', {
         useNewUrlParser: true,
         useUnifiedTopology: true
     }).then(() => {
         console.log('Conectado ao MongoDB');
     }).catch((err) => {
         console.error('Erro ao conectar ao MongoDB', err);
     });

     const usuarioSchema = new mongoose.Schema({
         nome: String,
         email: String,
         idade: Number,
         dataCriacao: { type: Date, default: Date.now }
     });

     const Usuario = mongoose.model('Usuario', usuarioSchema);

     app.use(express.json());

     // Rota para criar um novo usuário
     app.post('/usuarios', (req, res) => {
         const novoUsuario = new Usuario(req.body);
         novoUsuario.save().then(() => {
             res.status(201).send('Usuário criado com sucesso');
         }).catch((err) => {
             res.status(400).send('Erro ao criar usuário');
         });
     });

     // Rota para listar todos os usuários
     app.get('/usuarios', (req, res) => {
         Usuario.find().then((usuarios) => {
             res.status(200).json(usuarios);
         }).catch((err) => {
             res.status(500).send('Erro ao buscar usuários');
         });
     });

     // Rota para atualizar um usuário
     app.put('/usuarios/:id', (req, res) => {
         Usuario.updateOne({ _id: req.params.id }, req.body).then(() => {
             res.status(200).send('Usuário atualizado com sucesso');
         }).catch((err) => {
             res.status(400).send('Erro ao atualizar usuário');
         });
     });

     // Rota para deletar um usuário
     app.delete('/usuarios/:id', (req, res) => {
         Usuario.deleteOne({ _id: req.params.id }).then(() => {
             res.status(200).send('Usuário deletado com sucesso');
         }).catch((err) => {
             res.status(400).send('Erro ao deletar usuário');
         });
     });

     app.listen(3000, () => {
         console.log('Servidor rodando na porta 3000');
     });
     ```

2. **Testando a Aplicação:**
   - Execute a aplicação:
     ```bash
     node app.js
     ```
   - Use ferramentas como Postman ou `curl` para testar as operações CRUD:
     - **POST /usuarios**: Cria um novo usuário.
     - **GET /usuarios**: Lista todos os usuários.
     - **PUT /usuarios/:id**: Atualiza um usuário existente.
     - **DELETE /usuarios/:id**: Deleta um usuário.

**Explicação:**
- A aplicação Express está conectada ao MongoDB utilizando Mongoose, e implementa as operações CRUD para gerenciar um cadastro de usuários.

## 7.5 Exercícios

**Exercício 1: Configurando MongoDB e Mongoose**
- **Objetivo:** Garantir que a aplicação está conectada corretamente ao MongoDB.
- **Instruções:** Configure um novo projeto Node.js, instale Mongoose, e crie um script simples para conectar ao MongoDB e criar um documento em uma coleção.

**Exercício 2: Implementando Operações CRUD**
- **Objetivo:** Praticar as operações CRUD com Mongoose.
- **Instruções:** Crie um modelo de dados para produtos (com campos como nome, preço e estoque) e implemente as operações CRUD para gerenciar os produtos.

**Exercício 3: Validando Dados com Mongoose**
- **Objetivo:** Aprender a validar dados usando Mongoose.
- **Instruções:** Adicione validação ao modelo de dados de usuário, exigindo que o campo `email` seja único e que o campo `idade` seja um número positivo.

**Exercício 4: Criando Relacionamentos entre Documentos**
- **Objetivo:** Explorar relacionamentos entre documentos no MongoDB.
- **Instruções:** Crie dois modelos de dados relacionados (por exemplo, `Usuario` e `Post`). Implemente operações para associar posts a usuários e listar os posts de um usuário específico.

### Conclusão do Módulo 7

Neste módulo, você aprendeu a integrar um banco de dados MongoDB em sua aplicação Node.js usando Mongoose. Você configurou a conexão com o banco, criou modelos de dados, e implementou operações CRUD para gerenciar dados no MongoDB. No próximo módulo, exploraremos como implementar autenticação e autorização em sua aplicação.


