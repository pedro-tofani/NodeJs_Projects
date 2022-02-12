# Welcome to the Cookmaster V2 project!
 
You already use GitHub daily to develop the exercises, right? Now, to develop the projects, you must follow the instructions below. Stay tuned every step of the way, and if you have any questions, let us know via Slack! #vqv 🚀

Here you will find details on how to structure your project's development from this repository, using a specific branch and a Pull Request to place your code.
## Project requirements

### 1 - All your endpoints must be REST standard

- Use the appropriate HTTP verbs for each operation.

- Group and standardize your URLs on each resource.

- Ensure that your endpoints always return a response, whether the operations are successful or not.

- Return correct status codes (resource created, validation error, authorization, etc).

### 2 - Create an endpoint for user registration

- The route must be (`/users`).

- In the bank, a user must have the fields Email, Password, Name and Role.

- To create a user through the API, all fields are mandatory, with the exception of Role.

- The Email field must be unique.

- Users created through this endpoint must have their Role field with the _user_ attribute, that is, they must be regular users, not admins.

- The request body must contain the following format:

  ```json
  {
    "name": "string",
    "email": "string",
    "password": "string"
  }
  ```

### 3 - Create an endpoint for user login

- The route must be (`/login`).

- The route must receive the Email and Password fields and these fields must be validated in the database.

- A `JWT` token must be generated and returned if the login is successful. The user's id, email and role must be present in your payload.

- The request body must contain the following format:

  ```json
  {
    "email": "string",
    "password": "string"
  }
  ```

### 4 - Create an endpoint for the registration of recipes

- The route must be (`/recipes`).

- The recipe can only be created if the user is logged in and the `JWT` token is validated.

- In the bank, the recipe must have the Name, Ingredients, Preparation method, Image URL and Author Id fields.

- Name, ingredients and method of preparation must be received in the body of the request, with the following format:

  ```json
  {
    "name": "string",
    "ingredients": "string",
    "preparation": "string"
  }
  ```

- The ingredients field can be an open text field.

- The Author ID field must be automatically filled in with the ID of the logged in user, which must be extracted from the JWT token.

- Image URL will be populated through another endpoint

### 5 - Create an endpoint for the recipe listing

- The route must be (`/recipes`).

- The route can be accessed by users logged in or not

### 6 - Create an endpoint to view a specific recipe

- The route must be (`/recipes/:id`).

- The route can be accessed by users logged in or not

### 7 - Create an endpoint for editing a recipe

- The route must be (`/recipes/:id`).

- The recipe can only be updated if the user is logged in and the `JWT` token is validated.

- The recipe can only be updated if it belongs to the logged in user, or if that user is an admin.

- The request body must receive the following format:

  ```json
  {
    "name": "string",
    "ingredients": "string",
    "preparation": "string"
  }
  ```

### 8 - Create an endpoint for the deletion of a recipe

- The route must be (`/recipes/:id`).

- The recipe can only be deleted if the user is logged in and the `JWT` token is validated.

- The recipe can only be deleted if it belongs to the logged-in user, or if the logged-in user is an admin.

### 9 - Create an endpoint for adding an image to a recipe

- The route must be (`/recipes/:id/image/`).

- The image must be read from the `image` field.

- The endpoint must accept requests in `multipart/form-data` format.

- The recipe can only be updated if the user is logged in and the `JWT` token is validated.

- The recipe can only be updated if it belongs to the logged in user or if the logged in user is admin.

- The image must be uploaded using `Multer`.

- The file name must be the recipe ID, without extension. Images must be available via the `/images/<recipe-id>` route in the API.

- The full URL to access the image through the API must be recorded in the database, along with the recipe data.

### 10 - admin user permissions

- By default, there must be at least one user in the database with the Role _admin_.

- This user has the power to create, delete, update or remove any recipe, regardless of who registered it.

- Create a script in the root of your project with the extension `.sql`, if you use MySQL, or `.js`, if you use mongodb. This file should initialize the database and register an admin user with the email address `root@email.com` and the password `admin`.
