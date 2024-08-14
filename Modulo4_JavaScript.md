
# Módulo 4: Manipulação do DOM com JavaScript

## 4.1 Introdução

**Objetivo do Módulo:**  
Neste módulo, você aprenderá a manipular o DOM (Document Object Model) com JavaScript para criar interações dinâmicas em páginas web. Ao final deste módulo, você será capaz de selecionar elementos HTML, modificar seus conteúdos e estilos, e responder a eventos do usuário.

## 4.2 Contexto do Módulo

**O que é o DOM?**  
O DOM é uma representação em árvore da estrutura de uma página web, onde cada elemento HTML é um objeto que pode ser manipulado com JavaScript. Isso permite que você altere dinamicamente o conteúdo, a estrutura e o estilo de uma página após ela ter sido carregada.

**Por que Manipular o DOM?**  
- **Interatividade:** Permite criar experiências dinâmicas para os usuários, como validação de formulários, sliders de imagens, e outros elementos interativos.
- **Atualizações Dinâmicas:** Possibilita atualizar o conteúdo da página sem recarregar, proporcionando uma experiência mais fluida.

**Aplicação Prática:**  
- **Seleção de Elementos:** Identificar e trabalhar com elementos específicos da página.
- **Modificação de Conteúdo e Estilo:** Alterar dinamicamente texto, HTML, e estilos CSS.
- **Manipulação de Eventos:** Responder a cliques, teclas pressionadas, movimentos do mouse, entre outros.

## 4.3 Conceitos Importantes

**1. Selecionando Elementos do DOM:**
- **`getElementById`:** Seleciona um elemento pelo seu ID.
  ```javascript
  let elemento = document.getElementById("meuId");
  ```
- **`getElementsByClassName`:** Seleciona todos os elementos que possuem uma classe específica.
  ```javascript
  let elementos = document.getElementsByClassName("minhaClasse");
  ```
- **`getElementsByTagName`:** Seleciona todos os elementos de um tipo específico de tag.
  ```javascript
  let paragrafos = document.getElementsByTagName("p");
  ```
- **`querySelector`:** Seleciona o primeiro elemento que corresponde a um seletor CSS.
  ```javascript
  let elemento = document.querySelector(".minhaClasse");
  ```
- **`querySelectorAll`:** Seleciona todos os elementos que correspondem a um seletor CSS.
  ```javascript
  let elementos = document.querySelectorAll("div p");
  ```

**2. Modificando Conteúdo e Estilos:**
- **`innerHTML`:** Altera o conteúdo HTML de um elemento.
  ```javascript
  let elemento = document.getElementById("meuId");
  elemento.innerHTML = "Novo conteúdo HTML";
  ```
- **`textContent`:** Altera apenas o texto dentro de um elemento, ignorando qualquer HTML.
  ```javascript
  elemento.textContent = "Novo texto";
  ```
- **Modificando Estilos:** Alterar dinamicamente o estilo de um elemento usando a propriedade `style`.
  ```javascript
  elemento.style.color = "red";
  elemento.style.fontSize = "20px";
  ```

**3. Manipulando Eventos:**
- **Eventos Comuns:**
  - **`click`:** Disparado quando o elemento é clicado.
  - **`mouseover`:** Disparado quando o mouse passa sobre o elemento.
  - **`mouseout`:** Disparado quando o mouse sai do elemento.
  - **`keyup`:** Disparado quando uma tecla é liberada.
  
- **Adicionando Event Listeners:**
  ```javascript
  let botao = document.getElementById("meuBotao");
  botao.addEventListener("click", function() {
      alert("Botão clicado!");
  });
  ```

- **Removendo Event Listeners:**
  ```javascript
  function minhaFuncao() {
      alert("Evento removido!");
  }

  botao.removeEventListener("click", minhaFuncao);
  ```

## 4.4 Exemplo: To-Do List Dinâmica

**Exemplo Prático: Criando uma Lista de Tarefas**

Neste exemplo, você criará uma simples aplicação de lista de tarefas que permite adicionar, marcar como concluída e remover tarefas.

**Passos:**
1. **Crie um arquivo HTML** chamado `todo.html` com a seguinte estrutura:
   ```html
   <!DOCTYPE html>
   <html lang="pt-BR">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>To-Do List</title>
       <style>
           .completed {
               text-decoration: line-through;
           }
       </style>
   </head>
   <body>
       <h1>Lista de Tarefas</h1>
       <input type="text" id="tarefaInput" placeholder="Nova tarefa">
       <button id="adicionarBtn">Adicionar</button>
       <ul id="listaTarefas"></ul>

       <script src="todo.js"></script>
   </body>
   </html>
   ```

2. **Crie um arquivo JavaScript** chamado `todo.js` com o seguinte código:
   ```javascript
   document.getElementById("adicionarBtn").addEventListener("click", function() {
       let tarefaInput = document.getElementById("tarefaInput");
       let tarefaTexto = tarefaInput.value;

       if (tarefaTexto === "") {
           alert("Você deve escrever uma tarefa!");
           return;
       }

       let novaTarefa = document.createElement("li");
       novaTarefa.textContent = tarefaTexto;

       novaTarefa.addEventListener("click", function() {
           novaTarefa.classList.toggle("completed");
       });

       novaTarefa.addEventListener("dblclick", function() {
           novaTarefa.remove();
       });

       document.getElementById("listaTarefas").appendChild(novaTarefa);
       tarefaInput.value = "";
   });
   ```

3. **Abra o arquivo HTML** em um navegador e experimente adicionar, marcar como concluída e remover tarefas.

**Explicação:**
- **`document.createElement`:** Cria um novo elemento HTML.
- **`classList.toggle`:** Adiciona ou remove uma classe de um elemento, dependendo de sua presença.
- **`appendChild`:** Adiciona um novo elemento como filho de um elemento existente.

## 4.5 Exercícios

**Exercício 1: Modificando Estilos com Eventos**
- **Objetivo:** Praticar a modificação de estilos em resposta a eventos.
- **Instruções:** Crie um arquivo HTML com um parágrafo. Escreva um script JavaScript que altere a cor do texto do parágrafo para vermelho quando o mouse passar sobre ele, e volte ao normal quando o mouse sair.

**Exercício 2: Contador de Cliques**
- **Objetivo:** Praticar a manipulação de eventos e atualização de conteúdo do DOM.
- **Instruções:** Crie uma página com um botão que, ao ser clicado, incrementa e exibe o número de cliques.

**Exercício 3: Filtro de Lista**
- **Objetivo:** Aplicar técnicas de manipulação do DOM para filtrar elementos.
- **Instruções:** Crie uma lista de itens em HTML e adicione um campo de texto para filtrar esses itens. Ao digitar no campo de texto, mostre apenas os itens da lista que correspondem ao texto digitado.

**Exercício 4: Adicionar e Remover Elementos Dinamicamente**
- **Objetivo:** Praticar a criação e remoção de elementos HTML dinamicamente.
- **Instruções:** Crie uma página onde o usuário pode adicionar novos itens em uma lista e remover itens existentes. Os itens devem ser adicionados e removidos usando JavaScript.

## Conclusão do Módulo 4

Neste módulo, você aprendeu a selecionar, modificar e interagir com elementos HTML usando JavaScript. Esses conceitos são essenciais para criar páginas web interativas e dinâmicas. No próximo módulo, exploraremos o uso de JavaScript no lado do servidor com Node.js.
