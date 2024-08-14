
# Módulo 6: Aplicação Web Completa com Node.js e Express

## 6.1 Introdução

**Objetivo do Módulo:**  
Neste módulo, você aprenderá a criar uma aplicação web completa usando Node.js e o framework Express. Ao final deste módulo, você será capaz de configurar um servidor Express, servir páginas HTML, e desenvolver rotas dinâmicas para uma aplicação web.

## 6.2 Contexto do Módulo

**O que é o Express?**  
Express é um framework minimalista e flexível para Node.js que fornece um conjunto robusto de recursos para desenvolver aplicações web e APIs. Ele simplifica a criação de servidores HTTP, o gerenciamento de rotas, o middleware, e a manipulação de requisições e respostas.

**Por que Usar o Express?**
- **Simplicidade:** Express abstrai muitas das complexidades de configurar servidores HTTP em Node.js, tornando o desenvolvimento mais rápido e fácil.
- **Flexibilidade:** Permite adicionar funcionalidades conforme necessário, sem impor uma estrutura rígida.
- **Ecosistema:** Compatível com um vasto número de pacotes e middleware que estendem suas capacidades, como `body-parser`, `cors`, e `mongoose`.

**Aplicação Prática:**
- **Configuração do Servidor Express:** Criação de um servidor web utilizando o Express.
- **Servir Páginas Estáticas e Dinâmicas:** Configuração para servir arquivos HTML, CSS, e JS, além de rotas dinâmicas.
- **Criação de Rotas:** Definição de rotas para manipular diferentes requisições HTTP.

## 6.3 Conceitos Importantes

**1. Instalando e Configurando o Express:**
- **Instalação do Express:**
  - Inicie um novo projeto Node.js (caso ainda não tenha feito):
    ```bash
    npm init -y
    ```
  - Instale o Express:
    ```bash
    npm install express --save
    ```
  
- **Configurando um Servidor Básico com Express:**
  ```javascript
  const express = require('express');
  const app = express();

  app.get('/', (req, res) => {
      res.send('Bem-vindo ao Express!');
  });

  app.listen(3000, () => {
      console.log('Servidor rodando na porta 3000');
  });
  ```

**2. Servindo Páginas Estáticas:**
- **Servir Arquivos HTML:**
  - Crie uma pasta chamada `public` e adicione um arquivo HTML chamado `index.html`.
  - Configure o Express para servir arquivos estáticos:
    ```javascript
    app.use(express.static('public'));
    ```
  
  - O arquivo `index.html` será servido automaticamente quando o usuário acessar a raiz (`/`) do servidor.

**3. Criando Rotas Dinâmicas:**
- **Rotas Simples:**
  ```javascript
  app.get('/sobre', (req, res) => {
      res.send('Página Sobre Nós');
  });

  app.get('/contato', (req, res) => {
      res.send('Página de Contato');
  });
  ```
  
- **Rotas com Parâmetros:**
  ```javascript
  app.get('/usuario/:nome', (req, res) => {
      res.send(`Olá, ${req.params.nome}!`);
  });
  ```

**4. Usando Middleware:**
- **O que é Middleware?**
  Middleware é uma função que tem acesso ao objeto de requisição (`req`), ao objeto de resposta (`res`), e à próxima função middleware na aplicação. Pode ser usado para manipular requisições antes que elas alcancem as rotas finais.

- **Exemplo de Middleware:**
  ```javascript
  app.use((req, res, next) => {
      console.log(`Método: ${req.method} | URL: ${req.url}`);
      next();
  });
  ```

## 6.4 Exemplo: Criando uma Aplicação Web de Blog

**Exemplo Prático: Desenvolvendo uma Aplicação de Blog**

Neste exemplo, vamos criar uma aplicação web simples de blog que permite listar posts e visualizar posts individuais.

**Passos:**

1. **Configuração Inicial:**
   - Crie um novo projeto Node.js:
     ```bash
     npm init -y
     ```
   - Instale o Express:
     ```bash
     npm install express --save
     ```
   - Crie um arquivo chamado `app.js` e adicione o seguinte código:
     ```javascript
     const express = require('express');
     const app = express();

     app.set('view engine', 'ejs');

     app.get('/', (req, res) => {
         const posts = [
             { title: 'Post 1', content: 'Conteúdo do Post 1' },
             { title: 'Post 2', content: 'Conteúdo do Post 2' }
         ];
         res.render('index', { posts });
     });

     app.get('/post/:id', (req, res) => {
         const post = { title: `Post ${req.params.id}`, content: `Conteúdo do Post ${req.params.id}` };
         res.render('post', { post });
     });

     app.listen(3000, () => {
         console.log('Servidor rodando na porta 3000');
     });
     ```

2. **Criação das Views:**
   - Crie uma pasta chamada `views` e adicione os seguintes arquivos:
     - **`index.ejs`:**
       ```html
       <!DOCTYPE html>
       <html lang="pt-BR">
       <head>
           <meta charset="UTF-8">
           <meta name="viewport" content="width=device-width, initial-scale=1.0">
           <title>Blog</title>
       </head>
       <body>
           <h1>Posts</h1>
           <ul>
               <% posts.forEach(post => { %>
                   <li><a href="/post/<%= post.title.split(' ')[1] %>"><%= post.title %></a></li>
               <% }); %>
           </ul>
       </body>
       </html>
       ```
     - **`post.ejs`:**
       ```html
       <!DOCTYPE html>
       <html lang="pt-BR">
       <head>
           <meta charset="UTF-8">
           <meta name="viewport" content="width=device-width, initial-scale=1.0">
           <title><%= post.title %></title>
       </head>
       <body>
           <h1><%= post.title %></h1>
           <p><%= post.content %></p>
           <a href="/">Voltar</a>
       </body>
       </html>
       ```

3. **Execução da Aplicação:**
   - No terminal, execute a aplicação:
     ```bash
     node app.js
     ```
   - Acesse `http://localhost:3000` no navegador para ver a lista de posts.

**Explicação:**
- Utilizamos `EJS` como motor de templates para renderizar HTML dinâmico no lado do servidor.
- A aplicação possui rotas para a página principal e para visualizar posts individuais.

## 6.5 Exercícios

**Exercício 1: Criando um Projeto Express**
- **Objetivo:** Configurar um projeto Express básico.
- **Instruções:** Inicie um novo projeto Node.js, instale o Express e crie um servidor que responda com "Olá, Express!" na rota raiz (`/`).

**Exercício 2: Servindo Páginas Estáticas**
- **Objetivo:** Praticar o uso do Express para servir arquivos estáticos.
- **Instruções:** Configure o Express para servir arquivos HTML e CSS de uma pasta chamada `public`. Crie uma página `index.html` e acesse-a no navegador.

**Exercício 3: Desenvolvendo Rotas Dinâmicas**
- **Objetivo:** Praticar a criação de rotas dinâmicas.
- **Instruções:** Crie uma rota que receba um parâmetro de URL (como `/produto/:id`) e exiba uma mensagem personalizada para diferentes IDs de produto.

**Exercício 4: Usando Middleware**
- **Objetivo:** Aprender a usar middleware em uma aplicação Express.
- **Instruções:** Adicione middleware que registre no console o método HTTP e a URL de cada requisição feita ao servidor.

## Conclusão do Módulo 6

Neste módulo, você aprendeu a criar uma aplicação web completa utilizando Node.js e Express. Você configurou um servidor Express, serviu páginas estáticas e dinâmicas, e desenvolveu rotas para manipular diferentes requisições. No próximo módulo, exploraremos como integrar um banco de dados à sua aplicação web para armazenar e recuperar dados.
