# E-commerce System Documentation

## Introduction
This project is an object-oriented implementation of a simple e-commerce system in Java. The system is designed to manage products, customers, administrators, payments, and transactions. The following documentation provides a concise explanation of the classes and interfaces, outlining their purpose, attributes, and methods.

### 1-LoginLogout Class
The `LoginLogout` class manages user authentication and session state in the e-commerce system.

#### Purpose
* Facilitates user authentication by providing methods for login and account creation.
* Manages user sessions, keeping track of the currently logged-in customer or admin.
* Identifies user roles (customer or admin) and assigns them access levels accordingly.

### 2-PromoCode Class
The `PromoCode` class represents a promotional code in the e-commerce system.

#### Fields
* `code`: A string representing the promotional code.
* `Discount`: An integer representing the discount percentage.

### 3-Reviews Class
The `Reviews` class represents customer reviews for a product in the e-commerce system.

#### Fields
* `reviewerName`: A string representing the name of the reviewer.
* `review`: A string representing the review text.
* `rating`: A double representing the rating given by the reviewer(between 0 and 5 stars).
  
### 4-Product Abstract Class
The abstract `Product` class represents items available for sale in the e-commerce system. It serves as a base class for specific product types such as Electronics, Car, Clothes, Food, and Game.

#### Fields
* `idProduct`: Unique identifier for each product.
* `idSeller`: Identifier of the seller offering the product.
* `name`: Name of the product.
* `brand`: Brand of the product.
* `price`: Price of the product.
* `quantity`: Available quantity of the product.
* `listPromoCodes`: List of promotional codes applicable to the product.
* `listReviews`: List of customer reviews for the product.

#### Methods
* `displayReviews()`: Displays reviews for the product.
* `displayPromoCodes()`: Displays promotional codes for the product.
* `Rating()`: Calculates and returns the average rating based on customer reviews.
* `AddReview(nameReviewer)`: Allows customers to add reviews for the product.

#### 4-a-Electronics Class
The `Electronics` class extends the `Product` class, representing electronic items in the e-commerce system.

#### 4-b-Car Class
The `Car` class extends the `Product` class, representing cars available for sale in the e-commerce system.

##### Additional Fields
* `mileage`: Represents the mileage of the car.

#### 4-c-Clothes Class
The `Clothes` class extends the `Product` class, representing clothing items in the e-commerce system.

##### Additional Fields
* `size`: Represents the size of the clothing item.
* `type`: Represents the type or category of the clothing item.

#### 4-d-Food Class
The `Food` class extends the `Product` class, representing food items available for sale in the e-commerce system.

##### Additional Fields
* Inherits fields from the `Product` class.
* `expDate`: Represents the expiration date of the food item.

#### 4-e-Game Class
The `Game` class extends the `Product` class, representing video games in the e-commerce system.

#### 4-f-Sport Class
The `Sport` class extends the `Product` class, representing sports-related products in the e-commerce system.

### 5-Inventory Class
This class is used to manage the inventory of products in the e-commerce system. Products can be added, removed, updated, and displayed using the provided methods.

#### Fields
* `listProducts`: ArrayList to store `Product` objects.

#### Methods
* `addProduct(int idSeller)`: Adds a new product to the inventory based on user input.
* `deleteProduct(int idSeller, int idProduct)`: Removes a product from the inventory.
* `deleteProduct(int idProduct)`: Overloaded method for administrators to remove any product.
* `getProduct(int idProduct)`: Retrieves a product based on its ID.
* `updateProduct(int idSeller, int idProduct)`: Updates details of a product in the inventory.
* `displayAll()`: Displays information about all products in the inventory.
* `displayFilter()`: Displays filtered products based on user criteria.
* `check(Product product, int value)`: Helper method to check the type of a product.

### 6-Order Class
This class is used to create order objects with relevant information. Each order is assigned a unique ID and includes details about the purchased product.

#### Fields
* `numberOrders`: Static variable to track the total number of orders.
* `idOrder`: Unique identifier for each order.
* `idCustomer`: Identifier for the customer placing the order.
* `idProduct`: Identifier for the product being purchased.
* `quantity`: Quantity of the product in the order.
* `priceUnit`: Unit price of the product.
* `date`: Date when the order was created.

### 7-Transaction Class
The `Transactions` class manages a list of customer orders in the e-commerce system.

#### Fields
* `listOrders`: ArrayList to store `Order` objects.

#### Methods
* `addOrder(Order order)`: Adds a new order to the list.
* `removeOrder(int idOrder)`: Removes an order from the list based on its ID.
* `displayOrders()`: Displays information about all orders in the list.

### 8-Payment Interface
The `Payment` interface serves as a blueprint for different payment methods in the system.

### 8-a-Paypal Class
Implements the `Payment` interface for Paypal transactions as one of the payment methods.

### 8-b-Cash Class
Implements the `Payment` interface for cash transactions as one of the payment methods.

### 8-c-CreditCard Class
Implements the `Payment` interface for credit card transactions as one of the payment methods.

### 9-Customer Class
The `Customer` class represents a customer in the e-commerce system. Each customer has a unique identifier, a username, a password, and associated lists for offers, shopping cart items, order history, and payment methods. Customers can perform various actions like putting items for sale, updating offers, removing offers, managing the shopping cart, finalizing purchases, leaving reviews, etc.

Note that when the purchase is finalized, the total price is automatically subtracted from the buyer's account and added to the seller's account (Cash or Credit Card or Paypal). The quantity of

 the bought product is subtracted from the inventory, and an order is automatically created and stored in the transaction class.

### 10-Admin Class
The `Admin` class represents an administrator in the e-commerce system. Administrators have a unique identifier, a username, and a password. Admins have the authority to perform administrative actions such as removing customers and products from the system. They also have access to all account and product and order info.

### 11-Menu Class
The `Menu` class represents the user interface for interacting with the e-commerce system. It provides a menu-driven interface for customers and admins to perform various actions within the system.

#### Methods
* `EcommerceApplication(Ecommerce ecommerce)`: Initiates the main menu loop for the e-commerce application.
* `TestFillInventory(Ecommerce ecommerce)`: Populates the inventory with initial products and creates a test customer account.
* `createPromoCodes(int discount1, int discount2)`: Helper method to create a list of promo codes with specified discounts.

### 12-E-commerce Class
The `Ecommerce` class represents the core of an e-commerce system, managing customers, admins, inventory, transactions, and user authentication.

#### Fields
* `listCustomers`: ArrayList to store `Customer` objects.
* `listAdmins`: ArrayList to store `Admin` objects.
* `inventory`: `Inventory` object to manage and store products.
* `transaction`: `Transactions` object to handle customer orders.
* `loginLogout`: `LoginLogout` object for user authentication.
* `menu`: An object of `Menu` class represents the user interface.

#### Methods
* `addCustomer()`: Allows the addition of a new customer to the system, including username, password, and multiple payment methods (cash, credit card, Paypal).
* `addAdmin()`: Adds a new admin to the system with a given username and password.
* `removeCustomer(int idCustomer)`: Removes a customer from the system based on their ID.
* `findCustomer(int idCustomer)`: Finds and returns a customer based on their ID.
* `findCustomer(String username, String password)`: Finds and returns a customer based on their username and password.
* `findAdmin(String username, String password)`: Finds and returns an admin based on their username and password.
* `displayCustomers()`: Displays information about all customers in the system.
* `displayAdmins()`: Displays information about all admins in the system.

## Bonus Features
1. User Reviews and Ratings
2. Discounts and Promotions








