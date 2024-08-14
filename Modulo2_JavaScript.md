
# Módulo 2: Fundamentos de JavaScript

## 2.1 Introdução

**Objetivo do Módulo:**  
Neste módulo, você será introduzido aos conceitos fundamentais de JavaScript, como variáveis, tipos de dados e operadores. Estes são os blocos de construção básicos que você utilizará em qualquer programa JavaScript. Ao final deste módulo, você deverá ser capaz de declarar variáveis, utilizar diferentes tipos de dados e realizar operações básicas em JavaScript.

## 2.2 Contexto do Módulo

**Por que são importantes os Fundamentos?**  
Entender os fundamentos de JavaScript é essencial para qualquer desenvolvedor, pois essas bases são aplicadas em praticamente todos os aspectos da linguagem, desde a manipulação de dados até o controle de fluxo de programas mais complexos. Sem uma compreensão sólida desses conceitos, é difícil avançar para tópicos mais avançados.

**Aplicação Prática:**  
- **Manipulação de Dados:** Declaração de variáveis e manipulação de seus valores.
- **Lógica de Programação:** Uso de operadores para tomar decisões dentro de um programa.
- **Estruturação de Código:** Organização de dados e operações de maneira lógica e eficiente.

## 2.3 Conceitos Importantes

**1. Variáveis:**
- **O que são?**  
  Variáveis são como contêineres que armazenam dados na memória para que possam ser utilizados e manipulados ao longo do programa.
  
- **Declaração de Variáveis:**  
  JavaScript permite declarar variáveis usando as palavras-chave `var`, `let`, ou `const`.
  - **`var`:** Declara uma variável que pode ser redeclarada e cujo escopo pode ser global ou local.
  - **`let`:** Declara uma variável com escopo de bloco que não pode ser redeclarada no mesmo escopo.
  - **`const`:** Declara uma variável cujo valor não pode ser alterado após a inicialização.
  
  **Exemplos:**
  ```javascript
  var nome = "João";
  let idade = 30;
  const cidade = "São Paulo";
  ```

**2. Tipos de Dados:**
- **Tipos Primitivos:**  
  JavaScript possui vários tipos de dados primitivos que são usados para armazenar valores simples:
  - **String:** Texto entre aspas.
    ```javascript
    let texto = "Olá, Mundo!";
    ```
  - **Number:** Números, inteiros ou decimais.
    ```javascript
    let numero = 42;
    let preco = 99.99;
    ```
  - **Boolean:** Verdadeiro ou falso.
    ```javascript
    let aprovado = true;
    ```
  - **Undefined:** Variável declarada, mas não inicializada.
    ```javascript
    let indefinido;
    ```
  - **Null:** Representa ausência intencional de valor.
    ```javascript
    let vazio = null;
    ```

**3. Operadores:**
- **Operadores Aritméticos:**  
  Utilizados para realizar operações matemáticas básicas.
  ```javascript
  let soma = 10 + 5;    // 15
  let subtracao = 10 - 5; // 5
  let multiplicacao = 10 * 5; // 50
  let divisao = 10 / 5; // 2
  let resto = 10 % 3;  // 1
  ```

- **Operadores de Comparação:**  
  Usados para comparar valores e retornar um booleano (`true` ou `false`).
  ```javascript
  let igual = 10 == "10";   // true (comparação de valor)
  let estritamenteIgual = 10 === "10"; // false (comparação de valor e tipo)
  let maior = 10 > 5;  // true
  let menor = 10 < 5;  // false
  ```

- **Operadores Lógicos:**  
  Usados para combinar condições.
  ```javascript
  let e = true && false;  // false
  let ou = true || false; // true
  let nao = !true;  // false
  ```

## 2.4 Exemplo: Manipulando Variáveis e Operadores

**Exemplo Prático: Calculadora Simples**

Neste exemplo, você criará uma calculadora simples que soma, subtrai, multiplica e divide dois números.

**Passos:**
1. **Abra seu editor de código** e crie um novo arquivo chamado `calculadora.js`.
2. **Escreva o seguinte código:**
   ```javascript
   let numero1 = 10;
   let numero2 = 5;

   let soma = numero1 + numero2;
   let subtracao = numero1 - numero2;
   let multiplicacao = numero1 * numero2;
   let divisao = numero1 / numero2;

   console.log("Soma: " + soma);
   console.log("Subtração: " + subtracao);
   console.log("Multiplicação: " + multiplicacao);
   console.log("Divisão: " + divisao);
   ```
3. **Salve o arquivo**.
4. **Execute o código** no terminal usando o Node.js:
   ```bash
   node calculadora.js
   ```

**Saída Esperada:**
```
Soma: 15
Subtração: 5
Multiplicação: 50
Divisão: 2
```

**Explicação:**
- O código acima cria variáveis para armazenar os números e realiza operações matemáticas básicas com esses números. Em seguida, o resultado dessas operações é exibido no console.

## 2.5 Exercícios

**Exercício 1: Explorando Variáveis e Tipos de Dados**
- **Objetivo:** Praticar a declaração e manipulação de variáveis e diferentes tipos de dados.
- **Instruções:** Crie um novo arquivo chamado `tiposDeDados.js`. Dentro dele, declare variáveis de cada tipo de dado discutido (String, Number, Boolean, Undefined, Null) e imprima seus valores usando `console.log`.

**Exercício 2: Calculadora com Input do Usuário**
- **Objetivo:** Expandir a calculadora simples para receber input do usuário.
- **Instruções:** Use `prompt` para solicitar ao usuário dois números e uma operação (soma, subtração, multiplicação ou divisão). Realize a operação e mostre o resultado. Nota: Como `prompt` não é suportado diretamente pelo Node.js, use um pacote como `readline-sync` para capturar a entrada do usuário.

**Exercício 3: Comparação de Idades**
- **Objetivo:** Praticar operadores de comparação e lógicos.
- **Instruções:** Crie um arquivo `comparacao.js` onde você irá comparar a idade de três pessoas diferentes. Use operadores de comparação para verificar quem é o mais velho e o mais novo, e imprima os resultados.

**Exercício 4: Operadores Aritméticos Avançados**
- **Objetivo:** Explorar operações aritméticas mais avançadas.
- **Instruções:** No mesmo arquivo `calculadora.js`, adicione operações para calcular a potência de um número e o valor absoluto de uma diferença entre dois números. Use `Math.pow` e `Math.abs` para essas operações.

## Conclusão do Módulo 2

Ao completar este módulo, você terá uma compreensão sólida dos fundamentos de JavaScript, incluindo variáveis, tipos de dados e operadores. Esses conceitos são essenciais para a construção de qualquer programa em JavaScript e servirão como base para os módulos subsequentes, onde exploraremos estruturas de controle e manipulação de dados mais complexas.
