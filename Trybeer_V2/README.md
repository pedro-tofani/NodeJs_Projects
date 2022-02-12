## Project requirements

### Tests

1. Backend unit test coverage must be at least 90%.

### Sequelize

2. The application's business rule logic must be centered on the back-end, that is, on the `Node.js` API. With that, the only place that should contain the logic will be the back-end: the database and front-end **should not** contain business rule logic. That is, be very careful when using _triggers_, _procedures_, among others, and be very careful with business rules on the front-end.

3. The project should start using the _ORM Sequelize_ instead of the _MySQL_ driver.

4. Create as many `seeders` and `migrations` as you want. However, remember to create all the necessary `migrations` so that the project is generated 100% functional using the database you architected. The `.sql` file, containing the database creation/configuration _queries_, will no longer be necessary, as the project will use `migrations` and `seeders`. These must therefore be removed.

### Order status

5. Every order placed must have a status regarding its current progress.

6. Order _status_ must be as follows:

   - `Pending` right when the order is created;

   - `Preparing` when the request is initiated by the admin user;

   - `Delivered` when the order is finished.

7. The admin user must have control to change the status of the order. Remember to follow the `Open/Closed` principle of _SOLID_ for this implementation so that new behaviors and `status` can be added without impacting existing statuses.

8. Any updates made to the order by the admin user must be reflected in real time to the customer.

### Chat functionality, customer view

9. This functionality should only exist in the **client view**

10. The platform must have accessible, in the side menu, a chat functionality called `Chat with the store`.

    - A click on the item described as `Chat with the store` should take you to a chat page.

11. On the chat page, messages should appear in order with the most recent at the bottom.

    - The page should show both sent and received messages, with the most recent messages at the bottom.

    - The page must have an input to send a new message to the chat.

12. The customer nickname must be the registered email.

13. The conversation history must be saved in the `MondoDB` database and appear when the person opens the page.

### Chat functionality, admin view

14. This functionality should only exist in the **admin view**

15. The platform must have accessible, in the side menu, a chat functionality called `Conversations`.

    - A click on the `Conversations` button takes you to a page that lists all the conversations in the store.

    - Conversations should appear in a list. Each conversation must be identified by the email address of the customer in question.

    - If there are no conversations, the text "No conversations here" should be displayed.

16. A click on an item in the conversation list should display the corresponding chat on the screen.

    - A click on an item in the list should display the chat window for that conversation on the screen.

    - The _nickname_ of the shop in the conversation must be "Shop".

    - The conversation page should show, at the top of the screen, the email of the user that the Store is talking to.

    - The conversation page must have a back button that, when clicked, redirects the person to the conversation listing page again.

17. The history of each conversation must be saved in the database and appear when the person opens the page.

18. The conversation list must be sorted by the date of the last message.

    - The list of conversations must be sorted by the date of the last message (received or sent), the most recent at the top of the list.
