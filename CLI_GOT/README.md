## What should be developed

You are going to refactor part of a CLI (command line interface) so that instead of using callbacks, use only Promises. In addition, you will implement some more functionality, consuming the same API that is being consumed.

## Development

The CLI displays information about the world of Game of Thrones using, as a source of this information, a public API called [An API of Ice And Fire](https://www.anapioficeandfire.com).

The code in this repository has the functionality to list characters, and display details about a selected character. In addition to refactoring the existing code, you should add functionality to search for books by name, display the results, and show the details of the selected book.

## Project requirements

### 1 - The project must be done, necessarily, using Promises

There cannot be any kind of synchronous code or code that uses callbacks.

You can change the library used to make HTTP requests if you prefer, but the current library already supports Promises.

You can also use async/await whenever you need to handle promises. With that, there is no need to consume them using `then` and `catch`.

> **Tip**: To understand how to use Promises instead of callbacks with superagent, you can refer to [official documentation on npm](https://www.npmjs.com/package/superagent#node).

### 2 - Display, in the main menu, the sub-menu "books" and, inside it, an option "Search for books"

When selecting this option, allow the user to enter the name of the book they want to search.

> **Tip**: You can follow the same structure for the characters menu, present in the `lib/menus/characters` folder.

### 3 - Using the name entered, make a request to the `/books` endpoint of the API, with the `?name` parameter containing the name entered by the user and present the results to the user in a list

You can refer to [the documentation](https://www.anapioficeandfire.com/Documentation#books) of this endpoint to check what format the data will be returned in.

The list should only display the name of the book, and should allow the user to choose one of the books they want to see details about.

> **Tip**: To perform the search using the name informed by the user, you need to send the `name` parameter in the URL to the API, as in the following example: `https://www.anapioficeandfire.com/api /books?name=A Game of Thrones`

### 4 - If nothing is typed at the time of the search, display all books, paginated 10 by 10

When the CLI asks for the name of the book that the person wants to search, there is a possibility that nothing will be typed. In this case, the search must be done with the `?name` parameter blank (`?name=`), so that the API returns all books.

### 5 - Display the options "Next page" and "Previous page" if there are more than 10 results

Both options should only be displayed when they are actually useful, that is, if the user is already on the first page, the "Previous page" option should not be displayed, and if the user is already on the last page, the "Next page" should not be displayed.

To understand how pagination works, read the [API documentation](https://www.anapioficeandfire.com/Documentation#pagination).

You will need to read the contents of the `link` header, returned by the API when using pagination. The `lib/utils.js` file already has a function (`parseLinks`) that reads this header and converts it from a string to an object. The `lib/menus/characters/actions/list.js` file already implements this requirement, you can use it as a reference.

### 6 - When a book is selected, display the properties of that book on the screen

**Warning:** The `characters` and `povCharacters` properties should not be displayed.

This display must occur in the same way as with the character in the "Characters" menu.

After displaying the book details, the application should return to the book results screen.

### 7 - Always display a back option

In all menus, a "back" option should be displayed. This option should take the user to the previous menu and, through it, it should be possible to get back to the main menu.

### 8 - If no results are found, display a message and return to the books menu

The API performs the search for exact words in the value informed in the `name` parameter. If a book is informed that does not exist, the API will return an empty Array.

For these cases, display the message `"No books found for this search"` on the screen and then return to the books menu

### 9 - Show option to list the houses of the Game of Thrones world

Display, in the main menu, a "houses" menu and, within it, an option "List houses".

The behavior must be identical to that of listing characters, including pagination, which must meet [requirement 5](#5---display-the-options-"next-page"-and-"p
