
# Módulo 1: Introdução ao JavaScript

## 1.1 Introdução

**Objetivo do Módulo:**  
Este módulo tem como objetivo introduzir o estudante ao JavaScript, uma das linguagens de programação mais importantes para o desenvolvimento web. Ao final deste módulo, o aluno deverá ser capaz de entender o que é JavaScript, como configurar seu ambiente de desenvolvimento e criar um programa simples utilizando a linguagem.

## 1.2 Contexto do Módulo

**O que é JavaScript?**  
JavaScript é uma linguagem de programação de alto nível, interpretada e baseada em eventos, que foi inicialmente desenvolvida para adicionar interatividade às páginas web. Ao longo dos anos, ela se tornou uma linguagem robusta usada tanto no front-end quanto no back-end, especialmente com o advento do Node.js.

**Onde JavaScript é Usado?**
- **Front-end:** Para manipulação do DOM, eventos, animações, e interações do usuário.
- **Back-end:** Com o Node.js, JavaScript é utilizado para construir servidores, APIs, e realizar operações de banco de dados.

**Por que Aprender JavaScript?**
- **Popularidade:** JavaScript é uma das linguagens mais populares do mundo.
- **Versatilidade:** Pode ser usada tanto para o desenvolvimento de interfaces de usuário quanto para a lógica de servidor.
- **Comunidade e Suporte:** Existe uma vasta comunidade de desenvolvedores e uma infinidade de recursos e bibliotecas.

## 1.3 Conceitos Importantes

**Conceitos Básicos:**
- **Sintaxe:** Estrutura e regras que governam a escrita de código em JavaScript.
- **Tipos de Dados:** Diferentes tipos de valores que podem ser manipulados, como números, strings, booleanos, etc.
- **Operadores:** Ferramentas para realizar operações matemáticas, lógicas e de comparação.
- **Funções:** Blocos de código reutilizáveis que podem ser chamados com diferentes entradas.
- **Variáveis:** Contêineres para armazenar dados que podem ser alterados ou reutilizados ao longo do código.

**Instalando o Node.js:**
- **Node.js** permite executar código JavaScript fora do navegador, útil para desenvolvimento back-end e execução de scripts.
- **Passos para instalação:**
  - Acesse o [site oficial do Node.js](https://nodejs.org) e baixe a versão recomendada para sua plataforma (Windows, macOS ou Linux).
  - Após a instalação, abra o terminal e verifique se o Node.js foi instalado corretamente com os comandos:
    ```bash
    node -v
    npm -v
    ```

## 1.4 Exemplo: Criando Seu Primeiro Programa em JavaScript

**Exemplo Prático: "Hello, World!"**

Vamos criar um programa simples que imprime "Hello, World!" no console.

**Passos:**
1. **Abra seu editor de código** (recomendado: Visual Studio Code).
2. **Crie um novo arquivo** chamado `hello.js`.
3. **Escreva o seguinte código:**
   ```javascript
   console.log("Hello, World!");
   ```
4. **Salve o arquivo**.
5. **Execute o código** usando o Node.js. No terminal, navegue até o diretório onde o arquivo foi salvo e execute:
   ```bash
   node hello.js
   ```
   **Saída Esperada:**  
   ```
   Hello, World!
   ```

**Explicação:**
- **`console.log`** é uma função que exibe informações no console.
- Esse é o exemplo mais simples possível de um programa em JavaScript, utilizado para verificar se o ambiente está configurado corretamente.

## 1.5 Exercícios

**Exercício 1: Instalando o Node.js**
- **Objetivo:** Instalar e verificar a instalação do Node.js no seu sistema.
- **Instruções:** Após a instalação, execute os comandos `node -v` e `npm -v` no terminal e anote as versões instaladas.

**Exercício 2: Modificando o "Hello, World!"**
- **Objetivo:** Modificar o código do "Hello, World!" para incluir seu nome na mensagem.
- **Instruções:** Altere o código no arquivo `hello.js` para que ele imprima "Hello, [Seu Nome]!" e execute novamente o código.

**Exercício 3: Explorando o `console.log`**
- **Objetivo:** Experimentar com diferentes tipos de dados no `console.log`.
- **Instruções:** No mesmo arquivo `hello.js`, adicione linhas de código para imprimir diferentes tipos de dados, como números, booleanos e arrays. Exemplo:
   ```javascript
   console.log(123);
   console.log(true);
   console.log([1, 2, 3]);
   ```
   **Saída Esperada:**  
   ```
   123
   true
   [ 1, 2, 3 ]
   ```

**Exercício 4: Instalando um Editor de Código**
- **Objetivo:** Configurar um editor de código adequado para o desenvolvimento JavaScript.
- **Instruções:** Instale o Visual Studio Code ou outro editor de sua escolha, e explore as funcionalidades básicas, como abrir e salvar arquivos, instalação de extensões para JavaScript, e execução de código no terminal integrado.

## Conclusão do Módulo 1

Ao final deste módulo, você deve estar confortável com a instalação do Node.js, a configuração de um ambiente de desenvolvimento básico e a criação de programas JavaScript simples. No próximo módulo, mergulharemos nos fundamentos de JavaScript, explorando variáveis, tipos de dados e operadores.
