## Project requirements

### Pages

#### Visualization features

> Pages that can be accessed without login

### 1 - Create a recipe listing screen

The page must be accessible via the main route (`/`).

For each recipe, only the name of the recipe and the name of the person who registered that recipe should be shown, as well as a link to see its details.

A "New recipe" button should be displayed **only when there is a user logged in**.

### 2 - Create a screen to view a specific recipe

The canvas must be available on the `/recipes/:id` endpoint

If the ID of the person logged into the application is the same ID of the person who created the recipe, an "Edit recipe" button and another "Delete recipe" button must be displayed on the page. These buttons should take the person to the edit and delete recipe pages, respectively. If there is no person logged in, none of these buttons should be displayed.

This page should display the title, ingredients, and preparation method of the recipe.

> Tip: this is one of the cases where you can use `authMiddleware` by passing `false` to the `required` parameter, and passing the contents of `req.user` to the view, which will allow you to determine if there is a logged in user and therefore whether the buttons should be displayed.

### 3 - Create a user registration page

A user must have ID, Email, Password, First Name and Last Name fields. All fields are mandatory. The ID must be automatically generated and must not be filled in by the user at the time of registration.

Field validation must happen on the backend, and a message must be sent to the frontend through a property passed to the EJS, in the same way as with the `users/login` view.

**⚠️ Attention ⚠️**: The authentication system expects the `findUserByEmail` and `findUserById` functions to return an object with at least `email`, `password` and `id` fields. If you change the name of these fields, you will need to change the login code.

#### Administrative functions

> Pages that **not** can be accessed without login. For these pages, use `authMiddleware` without passing any parameters.

### 4 - Create a recipe registration page

The page must be accessible through the `/recipes/new` endpoint, and the form must be sent to the `POST /recipes` endpoint

The recipe must have ID, Name, Ingredients, Preparation mode and Author fields. Feel free to model the bank as you see fit. The ID must be generated automatically and must not be filled in the revenue registration form.

The ingredients field can be an open text field.

### 5 - Create a recipe editing page

The page must be accessible through the `/recipes/:id/edit` endpoint, and the form must be sent to the `POST /recipes/:id` endpoint.

When loading, the page should already contain the current information for that recipe. You can use the `value` attribute of HTML inputs to populate these fields.

Only the person who created the recipe should have permission to edit it. To verify this, you can use the `id` property located in `req.user` (which is created by `authMiddleware`) and compare it to the ID of whoever created the recipe. If the IDs are not identical, the person must be redirected to the recipe view page using the `res.redirect` method in the controller.

If the editing is successful, the person must be redirected to the page to view that recipe, with the updated data.

Field validation must be performed on the backend.

**⚠️ Attention ⚠️**: Remember that the screen is not the only way to access endpoints. A request made using Postman to the `POST /recipes/:id` endpoint **should not** change the ID of the recipe or the name of the person who registered it. For this, ensure that you are not sending these fields to the database in the update function of your revenue model.

### 6 - Create a recipe delete page

The page must be accessible through the `/recipes/:id/delete` endpoint, and can only be accessed by the person who entered the recipe.

When accessing the page, a form should be displayed, asking for the person's password to confirm the operation. This form must be sent to the `POST /recipes/:id/delete` endpoint.

The recipe should only be deleted if the password is correct. If it is incorrect, the person should be redirected to the recipe deletion page with the message "Incorrect password. Please try again".

If the recipe is successfully deleted, the person should be redirected to the recipe listing page.

### 7 - Create a recipe search page

The page must be accessible via the `/recipes/search` endpoint.

A text input must be displayed along with a "Search" button. The content of the input must be sent to the `GET /recipes/search` endpoint via the `q` parameter in the query string.

On the backend, the text input value will be accessible through the `query` property of the `req.query` object. If nothing is informed for search, the view must be rendered with only the search field. If a value is informed, a list similar to the recipe list screen should be displayed, containing the title, name of the person who registered, and a link to each recipe.

To perform the search, the recipe controller must ask the model to search for recipes **containing in its name** the value entered in the search input.

## bonus

### 8 - Create a "My Recipes" page

The link to access this page should only be visible to people logged in.

The page must be accessible through the `/me/recipes` endpoint, and it must render a list similar to the one displayed on the recipes list page, populated with the recipes registered by the logged-in user.

If a person who is not logged in accesses this page, they must be redirected to the login screen. (The `authMiddleware` middleware already implements this functionality, so don't forget to use it here.)

> Reminder: the ID of the logged in user is available in `req.user.id`.

### 9 - Create an edit user page

The link to access this page should only be visible to people logged in.

Each person should only be able to edit their own profile. For this, the backend must extract the user ID to be updated from the `req.user` property, not from the request body. This should be the ID sent to the model to perform the user update.

This page must be accessible through the `/me/edit` endpoint, and the form must be sent to the `POST /me` endpoint.

If a person not logged in tries to access the page, they must be redirected to login. (The `authMiddleware` middleware already implements this functionality, so don't forget to use it here.)

The person ID must not be editable. Neither through the screen, nor through a request made by Postman. For this, ensure that your model does not send this field to the database.

### 10 - Use EJS `includes` to render the pages navbar

Some of the HTML will be repeated on all pages, such as the navigation bar.

For such repetitive content, you can use EJS `includes`.

The [EJS documentation](https://ejs.co/#docs) (press Ctrl + F and search for "includes") talks briefly about using includes in your views.

---
