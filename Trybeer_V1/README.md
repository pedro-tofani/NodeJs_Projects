## Requirements Delivery 1

##### General requirements

1. API endpoints must be created using the REST pattern;

2. The backend must use the `MySQL` database;

3. The backend must be built following the `MSC` architectural pattern;

4. Make an SQL script available at the root of the project with commands for creating the database, tables, inserting initial data and creating the default admin. The script must be named `script.sql`.

##### Login Page

This screen is named `Login` in the prototype.

5. All screen elements must respect the attributes described in the prototype;

6. The screen route should be `/login`;

7. The person must be able to write their email in the email input;

8. The person must be able to write their password in the password input;

9. The form is only valid after a valid email address and a password of at least 6 numbers are filled in. A valid email has the form `<name>@<domain>`. If the form is invalid, the submit button must be disabled. Otherwise, it must be enabled;

10. After successful form submission, the token identifying the user received in the response must be saved in `localStorage`. This token must be used for future API requests;

11. After successful submission of the form, if the user is of type `administrator`, the person should be redirected to the page **Admin - Home**;

12. After successful submission of the form, if the user is a `client`, the person must be redirected to the **Customer - Products** page;

13. There should be a button for the user to register with the text `"I don't have an account yet"`. When clicked, the person should be redirected to the **Registration** page.

##### Registration Page

This screen has the name `Record` in the prototype.

14. All elements must respect the attributes described in the prototype;

15. The screen route should be `/register`;

16. The screen should show a form with the following fields:

    - **name** - must contain at least 12 letters, without numbers or special characters;

    - **email** - must contain a valid email address. A valid email has the form `<name>@<domain>`;

    - **password** - composed of at least 6 numbers;

    - **want to sell** - an optional checkbox, unchecked by default.

17. If the option `I want to sell` is checked, the user must be registered with a role of **admin**. Otherwise it will be a **client**;

18. If the data entered in the form is invalid, the submit button must be disabled. Otherwise, it must be enabled;

19. If the `I want to sell` option is checked, when clicking on the `"Register"` button, the person must be redirected to the **Admin - Home** page. Otherwise, it must be redirected to the **Customer - Products** page.

## Client

##### Top menu

20. All elements must respect the attributes described in the prototype for the top menu;

21. The top menu must always be displayed on all screens;

22. The title corresponding to the screen the user is on must be shown, according to prototypes;

23. There should be a "hamburger" icon in the top left corner of the top menu. When clicked, if the side menu is hidden, it should be shown. Otherwise, the side menu must be hidden.

##### Lateral menu

24. All elements must respect the attributes described in the prototype for the side menu;

25. It must contain four items: `"Products"`, `"My Orders"`, `"My Profile"` and `"Exit"`;

26. When clicking on the item `"Products"`, the person must be redirected to the **Customer - Products** screen;

27. When clicking on the item `"My Orders"`, the person must be redirected to the **Customer - My Orders** screen;

28. When clicking on the item `"My Profile"`, the person must be redirected to the **Customer - My Profile** screen;

29. When clicking on the `"Logout"` item, the person must be redirected to the **Login** screen and be logged out.

##### Profile Screen

This screen has the name `Customer - My Profile` in the prototype.

30. All elements must respect the attributes described in the prototype;

31. The screen route should be `/profile`;

32. It should have two text fields: one for `email` and one for `name`. Only the `name` can be changed. Therefore, the `email` field must be `read-only`;

33. There must be a `"Save"` button. If the user has edited the name, the button must be enabled. Otherwise, the button must be disabled;

34. When clicking the `"Save"` button, a request must be made to the API and the person's name must be updated in the database;

35. When entering the screen, if the user is not logged in, he must be redirected to the **Login** screen.

##### Products screen

This screen has the name `Customer - Products` in the prototype.

36. All elements must respect the attributes described in the prototype for the products screen;

37. The screen route should be `/products`;

38. On this screen, the products must be organized in "cards", and there must be a card for each product;

39. Cards must contain the following product data:

    - Photograph;

    - Product's name;

    - Unit price;

    - Current quantity entered in the cart;

    - Button to add (`+`) and remove (`-`) a product unit in the cart.

40. When clicking on the `+` button, the quantity of the product must increase by 1;

41. When clicking on the `-` button, the quantity of the product must decrease by 1, limited to 0;

43. If the person updates the browser, the cart must be kept;

43. The unit price must follow the standard `R$ 00.00`;

44. When the quantity shown on the product card reaches 0, the product must be removed from the cart;

45. There should be a `"View Cart"` button. This button should also display the **total amount** of the products in the cart;

46. ​​The **total amount** shown in the `"View cart"` button must be dynamically changed, that is, when adding or removing a product in the cart, the total value must be updated;

47. By clicking on the `"View Cart"` button, the person should be redirected to the **Customer - Checkout** page.

48. When entering the screen, if the user is not logged in, he must be redirected to the **Login** screen.

---

## Requirements Delivery 2

##### General requirements

49. Unit test coverage must be at least 90%;

##### Checkout Screen

This screen has the name `Customer - Checkout` in the prototype.

50. All elements must respect the attributes described in the prototype for the screen;

51. The screen route should be `/checkout`;

52. If the person updates the browser, the cart must be kept;

54. It should have a list of selected products with the following structure: `product quantity -- product name -- product total value`, with the total value calculated by **quantity * unit price**;

55. Next to each product there must be a button that, when clicked, deletes this product from the cart;

56. Below the list, show the **total amount of the order**, in the following format: `Total: R$ 0.00`. The total value of the order is calculated from the **sum of all the total values ​​of the products**;

57. There must be a form for the person to enter the delivery address of the products. The form must contain two text fields: one for the **street** and the other for the **house number**;

58. It should have a `"Checkout"` button. The button must be enabled **only** if the total value of the order is **greater than zero** and the delivery address is filled in;

59. When clicking on "`Finish order`", if the operation is successful, a success message should be displayed and the person should be redirected to the **Customer - Products** page. Otherwise, an error message should be displayed;

60. When an order is completed, the cart must be emptied;

61. When entering the screen, if the user is not logged in, he must be redirected to the **Login** screen.

##### My Orders Screen

This screen has the name `Customer - My Orders` in the prototype.

62. All elements must respect the attributes described in the prototype for the screen of my orders;

63. The screen route must be `/orders`;

64. Must contain a list of cards, where each card is an order. Each card must contain the following information: `order number`, `completion date` and `total order value`. For the order date, show only the day and month;

65. The listing must show the most recent orders first;

66. When clicking on the card, the person should be redirected to the **Customer - Order Details** page.

67. When entering the screen, if the user is not logged in, he must be redirected to the **Login** screen.

##### Order details screen

This screen has the name `Customer - Order Details` in the prototype.

68. All elements must respect the attributes described in the prototype for the order details screen;

69. The page route must be `/orders/:order-number`;

70. Show the `order number` and the `completion date`. For the order date, show only the day and month;

71. It should have a list of selected products with the following structure: `product quantity -- product name -- total product value`. The total value being calculated by **quantity * unit price**;

72. Below the list, show the `total order amount`. The total value of the order is calculated from the **sum of all the total values ​​of the products**.

73. When entering the screen, if the user is not logged in, he must be redirected to the **Login** screen.

## Admin

##### Lateral menu

74. All elements must respect the attributes described in the prototype for the side menu;

75. It must contain three items: `"Orders"`", `"Profile"`" and "`Exit`";

76. When clicking on the item `"Orders"`, the person should be redirected to the **Admin - Home** screen;

77. When clicking on the `"Profile"` item, the person must be redirected to the **Admin - Profile** screen;

78. When clicking on the `"Logout"` item, the person must be redirected to the **Login** screen and be logged out.

##### Profile Screen

This screen is named `Admin - Profile` in the prototype.

79. All elements must respect the attributes described in the prototype for the profile screen;

80. The page route must be `/admin/profile`;

81. Display the user's `email` and `name`. Do not allow the user to edit the data;

82. When entering the screen, if the user is not logged in, he must be redirected to the **Login** screen.

### Orders Screen

This screen has the name `Admin - Orders` in the prototype.

83. All elements must respect the attributes described in the prototype for the order screen;

84. The page route must be `/admin/orders`;

85. This screen should show all orders placed;

86. Pending orders must be labeled `Pending`, while delivered orders must have the label `Delivered`;

87. Pending orders must be listed before delivered orders

88. Order cards must contain the information:

    - Request number;

    - Delivery address;

    - Total value of the order.

89. When clicking on any part of the order card, the person should be redirected to the `Admin - Order Detail` screen.

### Order Details Screen

This page corresponds to the `Admin - Order Details - Pending` and `Admin - Order Details - Delivered` pages in the prototype.

90. All elements must respect the attributes described in the prototype for the order details screen;

91. The page route must be `/admin/orders/:id`;

92. In the header, show the `order number` and the current `status` - Pending or Delivered;

93. It must have a listing with the products of the order, where each line must contain:

    - The amount;

    - Product's name;

    - Total value of the product.

94. The `total price` of the product is calculated using **quantity * unit price**;

95. Also show the `total order amount`. The total value of the order is calculated from the **sum of all the total values ​​of the products**;

96. If the order status is **pending**, a button to mark the order as delivered should be displayed. Otherwise, do not display the button;

97. When you click the `"Mark order as delivered"` button, the status of that order should change to `Delivered` and the button should disappear.
