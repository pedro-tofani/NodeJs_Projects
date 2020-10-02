## Requisitos Entrega 1

##### Requisitos Gerais

1. Os `endpoints` da API devem ser criados utilizando o padrão REST;

2. O back-end deve utilizar o banco de dados `MySQL`;

3. O back-end deve ser construído seguindo o padrão arquitetural `MSC`;

4. Disponibilize um script SQL na raiz do projeto com comandos para a criação do banco de dados, das tabelas, inserção dos dados iniciais e criação do admin padrão. O script deve ser nomeado `script.sql`.

##### Página de Login

Esta tela possui o nome `Login` no protótipo.

5. Todos os elementos da tela devem respeitar os atributos descritos no protótipo;

6. A rota da tela deve ser `/login`;

7. A pessoa deve conseguir escrever seu email no input de email;

8. A pessoa deve conseguir escrever sua senha no input de senha;

9. O formulário só fica válido após um email válido e uma senha de, no mínimo, 6 números serem preenchidos. Um email válido possui a forma `<nome>@<domínio>`. Caso o formulário esteja inválido, o botão de submeter deve estar desativado. Caso contrário, deve estar ativado;

10. Após a submissão bem sucedida do formulário, o token que identifica o usuário recebido na resposta deve ser salvo no `localStorage`. Esse token deve ser utilizado para futuras requisições à API;

11. Após a submissão bem sucedida do formulário, se o usuário for do tipo `administrador`, a pessoa deve ser redirecionada para a página **Admin - Home**;

12. Após a submissão bem sucedida do formulário, se o usuário for do tipo `cliente`, a pessoa deve ser redirecionada para a página **Cliente - Produtos**;

13. Deve existir um botão para o usuário se registrar com o texto `"Ainda não tenho conta"`. Ao ser clicado, a pessoa deve ser redirecionada para a página **Registro**.

##### Página de Registro

Esta tela possui o nome `Registro` no protótipo.

14. Todos os elementos devem respeitar os atributos descritos no protótipo;

15. A rota da tela deve ser `/register`;

16. A tela deve mostrar um formulário com os seguintes campos:

    - **nome** - deve conter, no mínimo, 12 letras, sem números ou caracteres especiais;

    - **email** - deve conter um email válido. Um email válido possui o formato `<nome>@<domínio>`;

    - **senha** - composta por, no mínimo, 6 números;

    - **quero vender** - um checkbox opcional, desmarcado por padrão.

17. Caso a opção `Quero vender` esteja marcada, o usuário deve ser cadastrado com um papel de **admin**. Caso contrário, será um **client**;

18. Caso os dados inseridos no formulário sejam inválidos, o botão de submeter deve estar desativado. Caso contrário, deve estar ativado;

19. Caso a opção `Quero vender` esteja marcada, ao clicar no botão `"Cadastrar"`, a pessoa deve ser redirecionada para a página **Admin - Home**. Caso contrario, deve ser redirecionada para a página de **Cliente - Produtos**.

## Cliente

##### Menu superior

20. Todos os elementos devem respeitar os atributos descritos no protótipo para o menu superior;

21. O menu superior deve sempre ser exibido em todas as telas;

22. O título correspondente à tela em que o usuário se encontra deve ser mostrado, confome protótipos;

23. Deve haver um ícone do tipo "hambúrguer" no canto superior esquerdo do menu superior. Quando clicado, caso o menu lateral esteja oculto, deve ser mostrado. Caso contrário, o menu lateral deve ser escondido.

##### Menu lateral

24. Todos os elementos devem respeitar os atributos descritos no protótipo para o menu lateral;

25. Deve conter quatro itens: `"Produtos"`, `"Meus pedidos"`, `"Meu Perfil"` e `"Sair"`;

26. Ao clicar no item `"Produtos"`, a pessoa deve ser redirecionada para a tela **Cliente - Produtos**;

27. Ao clicar no item `"Meus pedidos"`, a pessoa deve ser redirecionada para a tela **Cliente - Meus Pedidos**;

28. Ao clicar no item `"Meu Perfil"`, a pessoa deve ser redirecionada para tela **Cliente - Meu Perfil**;

29. Ao clicar no item `"Sair"`, a pessoa deve ser redirecionada para a tela **Login** e ser deslogada.

##### Tela de perfil

Esta tela possui o nome `Cliente - Meu Pefil` no protótipo.

30. Todos os elementos devem respeitar os atributos descritos no protótipo;

31. A rota da tela deve ser `/profile`;

32. Deve ter dois campos de texto: um para o `email` e o outro para o `nome`. Apenas o `nome` pode ser alterado. Dessa forma, o campo `email` deve ser `read-only`;

33. Deve ter um botão `"Salvar"`". Caso o usuário tenha editado o nome, o botão deve ser habilitado. Caso contrário, o botão deve estar desabilitado;

34. Ao clicar no botão `"Salvar"`, uma requisição deve ser feita à API e o nome da pessoa deve ser atualizado no banco de dados;

35. Ao entrar na tela, se o usuário não estiver logado, deve ser redirecionado para a tela **Login**.

##### Tela de produtos

Esta tela possui o nome `Cliente - Produtos` no protótipo.

36. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de produtos;

37. A rota da tela deve ser `/products`;

38. Nessa tela, os produtos devem ser organizados em "cards", e deve haver um card para cada produto;

39. Os cards devem conter os seguintes dados do produto:

    - Foto;

    - Nome do produto;

    - Preço unitário;

    - Quantidade atual inserida no carrinho;

    - Botão de adicionar (`+`) e de remover (`-`) uma unidade do produto no carrinho.

40. Ao clicar no botão `+`, a quantidade do produto deve aumentar em 1;

41. Ao clicar no botão `-`, a quantidade do produto deve diminuir em 1, limitado a 0;

43. Caso a pessoa atualize o browser, o carrinho deve ser mantido;

43. O preço unitário deve seguir o padrão `R$ 00,00`;

44. Quando a quantidade mostrada no card do produto chegar a 0, o produto deve ser removido do carrinho;

45. Deve ter um botão `"Ver carrinho"`. Esse botão também deve exibir o **valor total** dos produtos no carrinho;

46. O **valor total** mostrado no botão `"Ver carrinho"` deve ser alterado dinamicamente, ou seja, ao adicionar ou remover um produto no carrinho, o valor total deve ser atualizado;

47. Ao clicar no botão `"Ver carrinho"`, a pessoa deve ser redirecionada para a página **Cliente - Checkout**.

48. Ao entrar na tela, se o usuário não estiver logado, deve ser redirecionado para a tela **Login**.

---

## Requisitos Entrega 2

##### Requisitos Gerais

49. A cobertura de testes unitários deve ser de, no mínimo, 90%;

##### Tela de Checkout

Esta tela possui o nome `Cliente - Checkout` no protótipo.

50. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela;

51. A rota da tela deve ser `/checkout`;

52. Caso a pessoa atualize o browser, o carrinho deve ser mantido;

54. Deve ter uma lista dos produtos selecionados com a seguinte estrutura: `quantidade do produto -- nome do produto -- valor total do produto`, sendo o valor total calculado por **quantidade * preço unitário**;

55. Ao lado de cada produto deve haver um botão que, quando clicado, exclui este produto do carrinho;

56. Abaixo da lista, mostre o **valor total do pedido**, no seguinte formato: `Total: R$ 0,00`. O valor total do pedido é calculado a partir da **soma de todos os valores totais dos produtos**;

57. Deve existir um formulário para a pessoa digitar o endereço de entrega dos produtos. O formulário deve conter dois campos de texto: um para a **rua** e o outro para o **número da casa**;

58. Deve ter um botão `"Finalizar Pedido"`. O botão deve estar habilitado **apenas** se o valor total do pedido for **maior que zero** e o endereço de entrega estiver preenchido;

59. Ao clicar em "`Finalizar pedido`", caso a operação dê certo, uma mensagem de sucesso deve ser exibida e a pessoa deve ser redirecionada para a página **Cliente - Produtos**. Caso contrário, deve ser exibido uma mensagem de erro;

60. Quando um pedido for finalizado, o carrinho deve ser esvaziado;

61. Ao entrar na tela, se o usuário não estiver logado, deve ser redirecionado para a tela **Login**.

##### Tela de Meus Pedidos

Esta tela possui o nome `Cliente - Meus Pedidos` no protótipo.

62. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de meus pedidos;

63. A rota da tela deve ser `/orders`;

64. Deve conter uma lista de cards, onde cada card é um pedido. Cada card deve conter as seguintes informações: `número do pedido`, `data de realização` e `valor total do pedido`. Para a data de realização do pedido, mostre apenas o dia e o mês;

65. A listagem deve mostrar os pedidos mais recentes primeiro;

66. Ao clicar no card, a pessoa deve ser redirecionada para a página **Cliente - Detalhes do Pedido**.

67. Ao entrar na tela, se o usuário não estiver logado, deve ser redirecionado para a tela **Login**.

##### Tela de detalhes de pedido

Esta tela possui o nome `Cliente - Detalhes de Pedido` no protótipo.

68. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de detalhes do pedido;

69. A rota da página deve ser `/orders/:numero-do-pedido`;

70. Mostre o `número do pedido` e a `data de realização`. Para a data de realização do pedido, mostre apenas o dia e o mês;

71. Deve ter uma lista dos produtos selecionados com a seguinte estrutura: `quantidade do produto -- nome do produto -- valor total do produto`. Sendo o valor total calculado por **quantidade * preço unitário**;

72. Abaixo da lista, mostre o `valor total do pedido`. O valor total do pedido é calculado a partir da **soma de todos os valores totais dos produtos**.

73. Ao entrar na tela, se o usuário não estiver logado, deve ser redirecionado para a tela **Login**.

## Admin

##### Menu lateral

74. Todos os elementos devem respeitar os atributos descritos no protótipo para o menu lateral;

75. Deve conter três itens: `"Pedidos"`", `"Perfil"`" e "`Sair`";

76. Ao clicar no item `"Pedidos"`, a pessoa deve ser redirecionada para a tela **Admin - Home**;

77. Ao clicar no item `"Perfil"`, a pessoa deve ser redirecionada para tela **Admin - Perfil**;

78. Ao clicar no item `"Sair"`, a pessoa deve ser redirecionada para a tela **Login** e ser deslogada.

##### Tela de perfil

Esta tela possui o nome `Admin - Perfil` no protótipo.

79. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de perfil;

80. A rota da página deve ser `/admin/profile`;

81. Mostrar o `email` e o `nome` do usuário. Não permita que o usuário edite os dados;

82. Ao entrar na tela, se o usuário não estiver logado, deve ser redirecionado para a tela **Login**.

### Tela de Pedidos

Esta tela possui o nome `Admin - Pedidos` no protótipo.

83. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de pedidos;

84. A rota da página deve ser `/admin/orders`;

85. Essa tela deve mostrar todos os pedidos feitos;

86. Os pedidos pendentes devem ter o label `Pendentes`, ao passo que os pedidos entregues devem ter o label `Entregue`;

87. Pedidos pendentes devem ser listados antes dos pedidos entregues

88. Os "cards" dos pedidos devem conter as informações:

    - Número do pedido;

    - Endereço para entrega;

    - Valor total do pedido.

89. Ao clicar em qualquer parte do card do pedido, a pessoa deve ser redirecionada para a tela `Admin - Detalhe de Pedido`.

### Tela de Detalhes de Pedido

Essa página corresponde às páginas `Admin - Detalhes de Pedido - Pendente` e `Admin - Detalhes de Pedido - Entregue` no protótipo.

90. Todos os elementos devem respeitar os atributos descritos no protótipo para a tela de detalhes do pedido;

91. A rota da página deve ser `/admin/orders/:id`;

92. No cabeçalho, mostre o `número do pedido` e o `status` atual - Pendente ou Entregue;

93. Deve ter uma listagem com os produtos do pedido, onde cada linha deve conter:

    - Quantidade;

    - Nome do produto;

    - Valor total do produto.

94. O `preço total` do produto é calculado usando **quantidade * preço unitário**;

95. Mostre também o `valor total do pedido`. O valor total do pedido é calculado a partir da **soma de todos os valores totais dos produtos**;

96. Caso o status do pedido seja **pendente**, um botão para marcar o pedido como entregue deve ser exibido. Caso contrário, não exiba o botão;

97. Ao clicar no botão `"Marcar pedido como entregue"`, o status desse pedido deve mudar para `Entregue` e o botão deve desaparecer.
