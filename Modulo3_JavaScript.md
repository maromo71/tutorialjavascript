
# Módulo 3: Funções e Escopo

## 3.1 Introdução

**Objetivo do Módulo:**  
Neste módulo, você aprenderá sobre funções em JavaScript, que são blocos de código reutilizáveis, e como o escopo das variáveis influencia a acessibilidade desses blocos de código. Ao final deste módulo, você será capaz de definir funções, invocá-las, passar parâmetros e entender como o escopo de variáveis funciona em JavaScript.

## 3.2 Contexto do Módulo

**Por que Funções e Escopo são Importantes?**  
Funções são fundamentais em qualquer linguagem de programação porque permitem a reutilização de código e a organização lógica de operações complexas. O escopo, por outro lado, define a "visibilidade" das variáveis e funções, ou seja, onde elas podem ser acessadas dentro do código.

**Aplicação Prática:**  
- **Modularização:** Quebra de código em pequenos blocos reutilizáveis.
- **Abstração:** Encapsulamento de complexidade em funções simples de usar.
- **Controle de Acesso:** Definir onde e como variáveis e funções podem ser acessadas ou modificadas.

## 3.3 Conceitos Importantes

**1. Funções:**
- **O que são?**  
  Funções são blocos de código projetados para executar uma tarefa específica. Elas podem ser definidas uma vez e reutilizadas em todo o código.
  
- **Sintaxe de Funções:**
  ```javascript
  function nomeDaFuncao(param1, param2) {
      // Código a ser executado
      return resultado;
  }
  ```
  
  **Exemplo:**
  ```javascript
  function somar(a, b) {
      return a + b;
  }

  let resultado = somar(5, 3);  // 8
  ```

- **Funções Anônimas e Arrow Functions:**
  - **Funções Anônimas:** Não possuem nome e geralmente são usadas em funções de callback.
  ```javascript
  let multiplicar = function(a, b) {
      return a * b;
  };
  ```
  - **Arrow Functions:** Uma sintaxe mais curta para escrever funções anônimas.
  ```javascript
  let dividir = (a, b) => a / b;
  ```

**2. Parâmetros e Argumentos:**
- **Parâmetros:** São os valores que você passa para uma função quando a define.
- **Argumentos:** São os valores que você fornece à função quando a chama.
  
  **Exemplo:**
  ```javascript
  function saudacao(nome) {
      return "Olá, " + nome + "!";
  }

  let mensagem = saudacao("Marcos");  // "Olá, Marcos!"
  ```

**3. Escopo de Variáveis:**
- **Escopo Global:** Variáveis declaradas fora de qualquer função são acessíveis em todo o código.
  ```javascript
  let nome = "João";  // Escopo global

  function exibirNome() {
      console.log(nome);  // Acessa a variável global
  }
  ```
- **Escopo Local:** Variáveis declaradas dentro de uma função são acessíveis apenas dentro dessa função.
  ```javascript
  function exemplo() {
      let idade = 25;  // Escopo local
      console.log(idade);
  }

  console.log(idade);  // Erro: idade não está definida
  ```

- **Hoisting:** Variáveis e funções são "elevadas" ao topo do escopo antes da execução do código.
  ```javascript
  console.log(a);  // undefined
  var a = 5;

  // Interpretação:
  var a;
  console.log(a);  // undefined
  a = 5;
  ```

## 3.4 Exemplo: Criando e Usando Funções

**Exemplo Prático: Calculadora com Funções**

Neste exemplo, vamos refatorar a calculadora do módulo anterior para usar funções para cada operação matemática.

**Passos:**
1. **Abra seu editor de código** e crie um novo arquivo chamado `calculadoraFuncao.js`.
2. **Escreva o seguinte código:**
   ```javascript
   function somar(a, b) {
       return a + b;
   }

   function subtrair(a, b) {
       return a - b;
   }

   function multiplicar(a, b) {
       return a * b;
   }

   function dividir(a, b) {
       if (b !== 0) {
           return a / b;
       } else {
           return "Erro: divisão por zero!";
       }
   }

   let num1 = 10;
   let num2 = 5;

   console.log("Soma: " + somar(num1, num2));
   console.log("Subtração: " + subtrair(num1, num2));
   console.log("Multiplicação: " + multiplicar(num1, num2));
   console.log("Divisão: " + dividir(num1, num2));
   ```
3. **Salve o arquivo**.
4. **Execute o código** no terminal usando o Node.js:
   ```bash
   node calculadoraFuncao.js
   ```

**Saída Esperada:**
```
Soma: 15
Subtração: 5
Multiplicação: 50
Divisão: 2
```

**Explicação:**
- As funções `somar`, `subtrair`, `multiplicar`, e `dividir` encapsulam a lógica de cada operação matemática. Isso torna o código mais modular e fácil de manter.

## 3.5 Exercícios

**Exercício 1: Função de Saudação Personalizada**
- **Objetivo:** Praticar a criação de funções simples com parâmetros.
- **Instruções:** Crie uma função `saudacao` que receba dois parâmetros, `nome` e `hora`, e retorne uma mensagem personalizada. Por exemplo, "Bom dia, João!" ou "Boa noite, Maria!".

**Exercício 2: Função de Verificação de Número Par**
- **Objetivo:** Usar uma função para realizar uma verificação lógica.
- **Instruções:** Crie uma função `ePar` que receba um número como parâmetro e retorne `true` se o número for par e `false` se for ímpar.

**Exercício 3: Função de Cálculo de Fatorial**
- **Objetivo:** Praticar a criação de funções recursivas.
- **Instruções:** Crie uma função `fatorial` que calcule o fatorial de um número (n!), onde n! = n * (n-1) * ... * 1. Por exemplo, `fatorial(5)` deve retornar 120.

**Exercício 4: Função de Escopo Global e Local**
- **Objetivo:** Compreender como o escopo afeta a acessibilidade das variáveis.
- **Instruções:** Crie duas variáveis com o mesmo nome, uma global e uma local dentro de uma função. Use `console.log` para imprimir o valor de cada uma e observe a diferença.

## Conclusão do Módulo 3

Ao completar este módulo, você terá uma boa compreensão de como funções são criadas e utilizadas em JavaScript, além de entender o conceito de escopo de variáveis e como ele afeta o comportamento do seu código. Esses conceitos são fundamentais para o desenvolvimento de aplicações mais complexas, onde a modularidade e o controle de variáveis são cruciais.
