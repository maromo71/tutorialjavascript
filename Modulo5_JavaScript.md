
# Módulo 5: Introdução ao Node.js

## 5.1 Introdução

**Objetivo do Módulo:**  
Neste módulo, você será introduzido ao Node.js, um ambiente de execução de JavaScript no lado do servidor. Ao final deste módulo, você será capaz de entender os conceitos básicos do Node.js, criar um servidor HTTP simples e manipular módulos para construir aplicações server-side básicas.

## 5.2 Contexto do Módulo

**O que é Node.js?**  
Node.js é um ambiente de execução que permite a utilização do JavaScript fora do navegador, especificamente no lado do servidor. Ele é construído sobre o motor V8 do Google Chrome e é amplamente utilizado para criar aplicações escaláveis e de alta performance, como servidores web, APIs RESTful e sistemas em tempo real.

**Por que Usar Node.js?**
- **Desempenho:** Node.js utiliza um modelo de I/O não-bloqueante, o que significa que operações de leitura/escrita não interrompem a execução do código. Isso resulta em uma performance eficiente para aplicações que exigem alta escalabilidade.
- **Unificação da Linguagem:** Desenvolvedores podem usar JavaScript tanto no front-end quanto no back-end, o que facilita a comunicação e o desenvolvimento dentro das equipes.
- **Ecossistema de Pacotes:** O Node.js possui um vasto ecossistema de pacotes, acessíveis através do npm (Node Package Manager), que simplifica o desenvolvimento de aplicações complexas.

**Aplicação Prática:**
- **Criação de Servidores Web:** Configuração de um servidor que responde a requisições HTTP.
- **Manipulação de Módulos:** Uso de módulos internos e externos para ampliar as funcionalidades da aplicação.
- **Desenvolvimento de APIs:** Implementação de APIs RESTful para comunicação entre sistemas.

## 5.3 Conceitos Importantes

**1. Instalando Node.js:**
- **Download e Instalação:**
  - Acesse o [site oficial do Node.js](https://nodejs.org) e baixe a versão recomendada para sua plataforma.
  - Após a instalação, verifique se o Node.js foi instalado corretamente executando os seguintes comandos no terminal:
    ```bash
    node -v
    npm -v
    ```
  - **node -v**: Mostra a versão do Node.js instalada.
  - **npm -v**: Mostra a versão do Node Package Manager instalada.

**2. Criando um Servidor HTTP Básico:**
- **Importando o Módulo HTTP:**  
  O módulo `http` é utilizado para criar servidores web simples.
  ```javascript
  const http = require('http');
  ```
- **Criando um Servidor:**
  ```javascript
  const server = http.createServer((req, res) => {
      res.statusCode = 200;
      res.setHeader('Content-Type', 'text/plain');
      res.end('Hello, World!
');
  });

  server.listen(3000, '127.0.0.1', () => {
      console.log('Servidor rodando em http://127.0.0.1:3000/');
  });
  ```

**3. Executando o Servidor:**
- **Passos para Executar:**
  - Salve o código acima em um arquivo chamado `server.js`.
  - No terminal, navegue até o diretório onde o arquivo está localizado e execute o comando:
    ```bash
    node server.js
    ```
  - No navegador, acesse `http://127.0.0.1:3000/` para ver o servidor em ação.

**4. Introdução aos Módulos no Node.js:**
- **Módulos Internos:**  
  Node.js vem com diversos módulos internos que facilitam o desenvolvimento. Alguns exemplos incluem:
  - **`fs`:** Manipulação de arquivos.
  - **`path`:** Manipulação de caminhos de arquivos e diretórios.
  - **`os`:** Informações sobre o sistema operacional.
  
- **Importando Módulos Externos:**  
  Pacotes externos podem ser instalados usando npm e importados para sua aplicação.
  ```bash
  npm install express
  ```
  ```javascript
  const express = require('express');
  ```

- **Criando Módulos Personalizados:**  
  Você pode criar seus próprios módulos exportando funções ou objetos de outros arquivos.
  ```javascript
  // arquivo calculadora.js
  function somar(a, b) {
      return a + b;
  }

  module.exports = somar;
  ```

  ```javascript
  // arquivo principal.js
  const somar = require('./calculadora');
  console.log(somar(5, 3));  // 8
  ```

## 5.4 Exemplo: Criando um Servidor com Node.js

**Exemplo Prático: Servidor HTTP que Responde Diferentes Caminhos**

Neste exemplo, vamos criar um servidor HTTP que responde com diferentes mensagens dependendo do caminho solicitado.

**Passos:**
1. **Crie um arquivo JavaScript** chamado `servidor.js`.
2. **Escreva o seguinte código:**
   ```javascript
   const http = require('http');

   const server = http.createServer((req, res) => {
       res.statusCode = 200;
       res.setHeader('Content-Type', 'text/plain');

       if (req.url === '/') {
           res.end('Bem-vindo à página inicial!
');
       } else if (req.url === '/sobre') {
           res.end('Sobre nós
');
       } else {
           res.statusCode = 404;
           res.end('Página não encontrada
');
       }
   });

   server.listen(3000, '127.0.0.1', () => {
       console.log('Servidor rodando em http://127.0.0.1:3000/');
   });
   ```

3. **Salve o arquivo**.
4. **Execute o código** no terminal usando o Node.js:
   ```bash
   node servidor.js
   ```
5. **Teste diferentes URLs** no navegador:
   - `http://127.0.0.1:3000/`
   - `http://127.0.0.1:3000/sobre`
   - `http://127.0.0.1:3000/qualquercoisa`

**Explicação:**
- O código cria um servidor que responde com diferentes mensagens dependendo do caminho solicitado (`req.url`).
- O servidor é configurado para ouvir na porta 3000, e pode ser acessado no navegador usando o endereço `http://127.0.0.1:3000/`.

## 5.5 Exercícios

**Exercício 1: Instalando e Verificando Node.js**
- **Objetivo:** Garantir que o Node.js está instalado corretamente.
- **Instruções:** Execute `node -v` e `npm -v` no terminal para verificar a instalação. Crie um arquivo `verificacao.js` e escreva um código simples que imprime "Node.js está funcionando!". Execute o arquivo usando `node verificacao.js`.

**Exercício 2: Criando um Servidor HTTP Simples**
- **Objetivo:** Praticar a criação de um servidor HTTP básico.
- **Instruções:** Crie um servidor que responda com "Olá, Mundo!" para qualquer requisição. Modifique o servidor para responder com "Olá, [seu nome]!" quando a URL for `/seunome`.

**Exercício 3: Trabalhando com Módulos Internos**
- **Objetivo:** Aprender a utilizar módulos internos do Node.js.
- **Instruções:** Crie um script que use o módulo `os` para exibir informações sobre o sistema operacional, como o nome do sistema, a versão, e a quantidade de memória disponível.

**Exercício 4: Criando e Importando Módulos Personalizados**
- **Objetivo:** Praticar a criação de módulos personalizados.
- **Instruções:** Crie um módulo chamado `calculadora` que exporte funções para somar, subtrair, multiplicar e dividir. Importe esse módulo em um arquivo separado e use as funções para realizar cálculos simples.

## Conclusão do Módulo 5

Neste módulo, você foi introduzido ao Node.js e aprendeu a criar servidores HTTP simples e a manipular módulos. Esses conceitos formam a base para o desenvolvimento de aplicações server-side mais complexas. No próximo módulo, exploraremos o uso de frameworks como o Express para simplificar o desenvolvimento de servidores e APIs.
