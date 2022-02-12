## Project requirements

### 1 - Your database models must follow the following specification

#### The following points will be evaluated:

- Your project should use an `ORM` to create and update your database. Cloning the project followed by a migrate command should leave it in its expected form.

- It must contain a table called **Users**, containing the following data:

  ```json
  {
    "id": "401465483996",
    "displayName": "Brett Wiltshire",
    "email": "brett@email.com",
    "password": "123456",
    "image": "http://4.bp.blogspot.com/_YA50adQ-7vQ/S1gfR_6ufpI/AAAAAAAAAAk/1ErJGgRWZDg/S45/brett.png"
  }
  ```

- It must contain a table called **BlogPosts**, containing the following data:

  ```json
  {
    "id": "7706273476706534553",
    "published": "2011-08-01T19:58:00.000Z",
    "updated": "2011-08-01T19:58:51.947Z",
    "title": "Latest updates, August 1st",
    "content": "The whole text for the blog post goes here in this key",
    "user_id": "401465483996" // this is the id that refers to the user who is the author of the post
  }
  ```

### 2 - Your application must have the POST endpoint `/user`

#### The following points will be evaluated:

- The endpoint must be able to add a new user to its table in the database;

- The request body must have the following format:

  ```json
  {
    "displayName": "Brett Wiltshire",
    "email": "brett@email.com",
    "password": 123456,
    "image": "http://4.bp.blogspot.com/_YA50adQ-7vQ/S1gfR_6ufpI/AAAAAAAAAAk/1ErJGgRWZDg/S45/brett.png"
  }
  ```
- The `displayName` field must be a string with at least 8 characters;

- The `email` field will be considered valid if it has the format `<prefix>@<domain>` and is unique. It is mandatory.

- The password must contain 6 characters. She is mandatory.

- If there is a person with the same email in the base, the following error should be returned:

  ```json
  {
    "message": "User already exists"
  }
  ```

- Otherwise, return the same response from the `/login` endpoint, a `JWT` token:

  ```json
  {
    "token": "token-here"
  }
  ```

- The endpoint must be tested.

### 3 - Your application must have the GET `/user` endpoint

#### The following points will be evaluated:

- Must list all **Users** and return them in the following structure:

  ```json
  [
    {
      "id": "401465483996",
      "displayName": "Brett Wiltshire",
      "email": "brett@email.com",
      "image": "http://4.bp.blogspot.com/_YA50adQ-7vQ/S1gfR_6ufpI/AAAAAAAAAAk/1ErJGgRWZDg/S45/brett.png"
    }
  ]
  ```

- The request must have authentication token in the headers and, if not, return a `status 401` code.

- The endpoint must be tested.

### 4 - Your application must have the GET `/user/:id` endpoint

#### The following points will be evaluated:

- Returns user details based on the `id` of the route. The data must have the following format:

  ```json
  {
    "id": "401465483996",
    "displayName": "Brett Wiltshire",
    "email": "brett@email.com",
    "image": "http://4.bp.blogspot.com/_YA50adQ-7vQ/S1gfR_6ufpI/AAAAAAAAAAk/1ErJGgRWZDg/S45/brett.png"
  }
  ```

- The request must have authentication token in the headers and, if not, return a `status 401` code.

- The endpoint must be tested.

### 5 - Your application must have the DELETE `/user/me` endpoint

#### The following points will be evaluated:

- Using the authentication token in the headers, the corresponding user must be deleted.

- The endpoint must be tested.

### 6 - Your application must have the POST endpoint `/login`

#### The following points will be evaluated:

- The body of the request should follow the format below:

  ```json
  {
    "email": "email@mail.com",
    "password": "123456"
  }
  ```

- If any of these fields is invalid or there is no corresponding user in the database, return a status code 400 with the body `{ message: "Invalid fields" }`.

- If everything is ok with the login, the response should be a `JWT` token, in the following format:

  ```json
  {
    "token": "token-here"
  }
  ```

- The endpoint must be tested.

### 7 - Your application must have the POST endpoint `/post`

#### The following points will be evaluated:

- This endpoint must receive a _BlogPost_ in the body of the request and create it in the database. The request body must have the following structure:

  ```json
  {
    "title": "Latest updates, August 1st",
    "content": "The whole text for the blog post goes here in this key"
  }
  ```

- If the post does not contain the `title` and/or the `content` the API should return a `status 400` error.

- The request must have the authentication token in the headers and otherwise return a `status 401` code.

- The endpoint must be tested.

### 8 - Your application must have the GET `/post` endpoint

#### The following points will be evaluated:

- This endpoint should list all _BlogPosts_ and return them in the following structure:

  ```json
  [
    {
      "id": "7706273476706534553",
      "published": "2011-08-01T19:58:00.000Z",
      "updated":"2011-08-01T19:58:51.947Z",
      "title": "Latest updates, August 1st",
      "content": "The whole text for the blog post goes here in this key",
      "user": { // this user is the author of the post
        "id": "401465483996",
        "displayName": "Brett Wiltshire",
        "email": "brett@email.com",
        "image": "http://4.bp.blogspot.com/_YA50adQ-7vQ/S1gfR_6ufpI/AAAAAAAAAAk/1ErJGgRWZDg/S45/brett.png"
      }
    }
  ]
  ```

- The endpoint must be tested.

### 9 - Your application must have the PUT `/post/:id` endpoint

#### The following points will be evaluated:

- The endpoint must receive a **BlogPost** that will overwrite the original with the `id` specified in the URL. Should only be allowed to the user who created the **BlogPost**.

- The request body must have the following structure:

  ```json
  {
    "title": "Latest updates, August 1st",
    "content": "The whole text for the blog post goes here in this key"
  }
  ```

- If a person other than the one who created it makes the request, it must return a code `status 403`.

- If a request without a token is received, it must return a code of `status 401`.

- If the post does not contain the `title` and/or the `content` the API should return a `status 400` error.

- The endpoint must be tested.

### 10 - Your application must have the GET `post/:id` endpoint

#### The following points will be evaluated:

- Returns a **BlogPost** with the specified `id`. The return must have the following format:

  ```json
  {
    "id": "7706273476706534553",
    "published": "2011-08-01T19:58:00.000Z",
    "updated": "2011-08-01T19:58:51.947Z",
    "title": "Latest updates, August 1st",
    "content": "The whole text for the blog post goes here in this key",
    "user": { // this user is the author of the post
      "id": "401465483996",
      "displayName": "Brett Wiltshire",
      "email": "brett@email.com",
      "image": "http://4.bp.blogspot.com/_YA50adQ-7vQ/S1gfR_6ufpI/AAAAAAAAAAk/1ErJGgRWZDg/S45/brett.png",
    }
  }
  ```

- The endpoint must be tested.

### 11 - Your application must have the GET `post/search?q=:searchTerm` endpoint

#### The following points will be evaluated:

- Returns an array of **BlogPosts** that contain in their title, or content, the term searched in the `queryParam` of the URL. The return must have the following format:

  ```json
  [
    {
      "id": "7706273476706534553",
      "published": "2011-08-01T19:58:00.000Z",
      "updated": "2011-08-01T19:58:51.947Z",
      "title": "Latest updates, August 1st",
      "content": "The whole text for the blog post goes here in this key",
      "user": { // this user is the author of the post
        "id": "401465483996",
        "displayName": "Brett Wiltshire",
        "email": "brett@email.com",
        "image": "http://4.bp.blogspot.com/_YA50adQ-7vQ/S1gfR_6ufpI/AAAAAAAAAAk/1ErJGgRWZDg/S45/brett.png"
      }
    }
  ]
  ```

- If no **BlogPost** satisfies the search, return an empty array.

- The endpoint must be tested.

### 12 - Your application must have the DELETE `post/:id` endpoint

#### The following points will be evaluated:

- Deletes the post with the specified `id`. Should only be allowed to the user who created the **BlogPost**.

- If a person other than the one who created it makes the request, it must return a code `status 403`.

- If a request without a token is received, it must return a code of `status 401`.

- If the referred post does not exist, a code of `status 404` must be returned.

- The endpoint must be tested.

## Tips

### HTTP Status

Keep in mind that all "answers" must respect the [HTTP protocol status](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status) based on what REST preaches.

Some examples:

  - Requests that need a token but have not received it must return a code of `status 401`;

  - Requests that do not follow the format requested by the server must return a code of `status 400`;

  - An unexpected problem on the server should return a code of `status 500`;

  - An access when creating a resource, in our case user or post, should return a code of `status 201`.

### Tests

- Follow the best practices for organizing tests as you saw in the contents! Otherwise, you will get lost easily!

- Give preference to unit tests in this project.
