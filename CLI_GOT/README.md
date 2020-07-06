## O que deverá ser desenvolvido

Você vai refatorar parte de um CLI (command line interface) para que, ao invés de utilizar callbacks, utilize apenas Promises. Além disso, você vai implementar mais algumas funcionalidades, consumindo a mesma API que está sendo consumida.

## Desenvolvimento

O CLI mostra informações sobre o mundo de Game of Thrones utilizando, como fonte dessas informações, uma API pública chamada [An API of Ice And Fire](https://www.anapioficeandfire.com).

O código deste repositório possui a funcionalidade de listar as personagens, e exibir os detalhes sobre uma personagem selecionada. Além de refatorar o código já existente, você deverá adicionar a funcionalidade de buscar livros pelo nome, exibir os resultados, e mostrar os detalhes do livro selecionado.

## Requisitos do projeto

### 1 - O projeto deve ser feito, necessariamente, utilizando Promises

Não pode haver nenhum tipo de código síncrono ou que utilize callbacks.

Você pode trocar a biblioteca utilizada para fazer requisições HTTP, se preferir, mas a biblioteca atual já suporta Promises.

Você também pode utilizar async/await sempre que precisar manipular as Promises. Com isso, não existe a necessidade de consumi-las utilizando `then` e `catch`.

> **Dica**: Para entender como utilizar Promises ao invés de callbacks com o superagent, você pode consultar a [documentação oficial no npm](https://www.npmjs.com/package/superagent#node).

### 2 - Exibir, no menu inicial, o sub-menu "livros" e, dentro dele, uma opção "Pesquisar livros"

Ao selecionar essa opção, permita que o usuário insira o nome do livro que deseja pesquisar.

> **Dica**: Você pode seguir a mesma estrutura já existente para o menu de personagens, presente na pasta `lib/menus/characters`.

### 3 - Utilizando o nome inserido, realizar uma requisição para o endpoint `/books` da API, com o parâmetro `?name` contendo o nome digitado pelo usuário e apresentar os resultados para o usuário numa lista

Você pode consultar [a documentação](https://www.anapioficeandfire.com/Documentation#books) deste endpoint para verificar qual o formato em que os dados serão retornados.

A lista deve exibir apenas o nome do livro, e deve permitir que o usuário escolha um dos livros sobre o qual deseja ver os detalhes.

> **Dica**: Para realizar a busca utilizando o nome informado pelo usuário, você precisa enviar para a API o parâmetro `name` na URL, como o exemplo a seguir: `https://www.anapioficeandfire.com/api/books?name=A Game of Thrones`

### 4 - Caso nada seja digitado no momento da pesquisa, exiba todos os livros, paginados de 10 em 10

Quando o CLI solicitar o nome do livro que a pessoa deseja pesquisar, existe a possibilidade de nada ser digitado. Nesse caso, a busca deve ser feita com o parâmetro `?name` em branco (`?name=`), para que a API retorne todos os livros.

### 5 - Apresentar as opções "Próxima página" e "Página anterior" caso existam mais de 10 resultados

Ambas as opções só devem ser exibidas quando de fato forem úteis, ou seja, se o usuário já estiver na primeira página, a opção "Página anterior" não deve ser exibida e, se o usuário já estiver na última página, a opção "Próxima página" não deve ser exibida.

Para entender como a paginação funciona, leia a [documentação da API](https://www.anapioficeandfire.com/Documentation#pagination).

Você precisará ler o conteúdo do header `link`, retornado pela API quando utiliza-se paginação. O arquivo `lib/utils.js` já possui uma função (`parseLinks`) que realiza a leitura desse header e o converte de string para um objeto. O arquivo `lib/menus/characters/actions/list.js` já faz a implementação desse requisito, você pode utiliza-lo como referência.

### 6 - Quando o um livro for selecionado, exibir na tela as propriedades daquele livro

**Atenção:** As propriedades `characters` e `povCharacters` não deverão ser exibidas.

Essa exibição deve ocorrer da mesma forma que ocorre com a personagem no menu "Personagens".

Após exibir os detalhes do livro, a aplicação deve retornar para a tela de resultados de livros.

### 7 - Sempre exibir uma opção de voltar

Em todos os menus, uma opção de "voltar" deve ser exibida. Essa opção deve levar o usuário para o menu anterior e, através dela, deve ser possível chegar de volta ao menu principal.

### 8 - Caso nenhum resultado for encontrado, exibir uma mensagem e voltar ao menu de livros

A API realiza a busca por palavras exatas no valor informado no parâmetro `name`. Caso seja informado um livro que não existe, a API retornará um Array vazio.

Para esses casos, exiba na tela a mensagem `"Nenhum livro encontrado para essa pesquisa"` e, logo em seguida, retorne ao menu de livros

### 9 - Exibir opção de listar as casas do mundo de Game of Thrones

Exibir, no menu principal, um menu "casas" e, dentro dele, uma opção "Listar casas".

O comportamento deve ser idêntico ao de listar personagens, inclusive a paginação, que deve atender ao [requisito 5](#5---apresentar-as-opções-"próxima-página"-e-"página-anterior"-caso-existam-mais-de-10-resultados).

**Atenção** A propriedade `swornMembers` não deve ser exibida ao selecionar uma casa.

## Bônus

### 10 - Implemente testes unitários que cubram 90% do código

---
