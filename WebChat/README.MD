## Mandatory Requirements:

### 1 - Your application must have a backend that allows several people to connect simultaneously and send messages in a chat

##### The following checks will be done:

- The application must allow several clients to connect to a chat at the same time;

- Each customer connected to the chat must receive all messages that have already been sent in the chat;

- Every message that a customer receives must contain information about who sent it, date-time of sending and the content of the message itself. The date-time of messages must be determined by the time they are saved in the database (see requirement 3).

### 2 - Your application must have a front-end where the user can interact with the chat

##### The following checks will be done:

- The front-end should display all messages already sent in the chat, keeping the most recent ones at the bottom of the screen;

- The front-end must have a text box through which the user can send messages to the chat;

- The front-end must allow the user to choose a nickname (_nickname_) for himself. For the client to be able to choose a nickname, it must have a text field and a button on the front-end. The text field will be where the customer will type the _nickname_ they want. After choosing the _nickname_, the client must click on the button for the data to be saved in `MongoDB`.

### 3 - The chat history should persist even if the chat server is closed and reopened

##### The following checks will be done:

- You must configure a MongoDB database, where each line contains a sent message;

- Your database must save the nickname of the sender, the message itself and a _timestamp_ with seconds precision of when it was saved in the database.

### 4 - Your application should send a _push notification_ to customers when a new message arrives in the chat

##### The following checks will be done:

- When a new message arrives in the chat, all customers should receive a push notification with such an alert.

### 5 - Your backend must have 100% automated testing coverage

##### The following checks will be done:

- Backend test coverage must be 100%;

- If any of your backend functions have their content erased your tests should break.
