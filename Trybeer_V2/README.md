## Requisitos do projeto

### Testes

1. A cobertura de testes unitários do back-end deve ser de, no mínimo, 90%.

### Sequelize

2. A lógica da regra de negócio da aplicação deve estar centralizada no back-end, ou seja, na API `Node.js`. Com isso, o único lugar que deve conter a lógica será o back-end: o banco de dados e front-end **não devem** conter lógicas de regra de negócio. Ou seja, muito cuidado ao utilizar _triggers_, _procedures_, dentre outras, e muito cuidado com regras de negócio no front-end.

3. O projeto deve passar a utilizar o _ORM Sequelize_ ao invés do driver do _MySQL_.

4. Crie quantos `seeders` e quantas `migrations` quiser. Porém, lembre-se de criar todas as `migrations` necessárias para que o projeto seja gerado 100% funcional utilizando o banco de dados arquitetado por você. O arquivo `.sql`, contendo as _queries_ de criação/configuração do banco, não será mais necessário, visto que o projeto passará a utilizar `migrations` e `seeders`. Estes devem, portanto, ser removidos.

### Status do pedido

5. Todo pedido realizado deve ter um status referente ao seu progresso atual.

6. Os _status_ do pedido devem ser os seguintes:

   - `Pendente` logo quando o pedido for criado;

   - `Preparando` quando o pedido for iniciado pelo usuário admin;

   - `Entregue` quando o pedido terminar.

7. O usuário admin deve ter o controle de alterar o status do pedido. Lembre-se de seguir princípio `Open/Closed` de _SOLID_ para está implementação de forma que possam ser acrescentados novos comportamentos e `status` sem impactar os status já existentes.

8. Qualquer atualização feita no pedido pelo usuário admin deve se refletir em tempo real para o cliente.

### Funcionalidade de chat, visão de cliente

9. Essa funcionalidade só deve existir na **visão de cliente**

10. A plataforma deve ter acessível, no menu lateral, uma funcionalidade de chat denominada `Conversar com a loja`.

    - Um clique no item descrito como `Conversar com a loja` deve levar para uma página de chat.

11. Na página de chat, as mensagens devem aparecer ordenadas com as mais recentes embaixo.

    - A página deve mostrar as mensagens enviadas e recebidas, com as mensagens mais recentes mais embaixo.

    - A página deve ter um input para envio de nova mensagem ao chat.

12. O nickname de cliente deve ser o email cadastrado.

13. O histórico da conversa deve ser salvo no banco de dados `MondoDB` e aparecer quando a pessoa abre a página.

### Funcionalidade de chat, visão de admin

14. Essa funcionalidade só deve existir na **visão de admin**

15. A plataforma deve ter acessível, no menu lateral, uma funcionalidade de chats denominada `Conversas`.

    - Um clique no botão `Conversas` direciona para uma página que lista todas as conversas da loja.

    - As conversas devem aparecer numa lista. Cada conversa deve ser identificada pelo email da pessoa cliente em questão.

    - Caso não tenham conversas, deve ser exibido o texto "Nenhuma conversa por aqui".

16. Um clique num item da lista de conversas deve exibir na tela o respectivo chat.

    - Um clique em um item da lista deve exibir na tela a janela com o chat daquela conversa.

    - O _nickname_ da loja na conversa deve ser "Loja".

    - A página da conversa deve mostrar, no topo da tela, o email do usuário que a Loja está conversando.

    - A página da conversa deve ter um botão de voltar que ao ser clicado redireciona a pessoa a página de listagem de conversas novamente.

17. O histórico de cada conversa deve ser salvo no banco de dados e aparecer quando a pessoa abre a página.

18. A lista de conversas deve ser ordenada pela data da última mensagem.

    - A lista de conversas deve ser ordenada pela data da última mensagem (recebida ou enviada), as mais recentes no topo da lista.
