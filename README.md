# Shop Product CRUD Application (CLI)

This is a simple, command-line interface (CLI) application built in Python that demonstrates basic CRUD (Create, Read, Update, Delete) operations for managing a product inventory.

The data is stored in memory (a list of dictionaries) and is not persistent; it resets every time the application is restarted.

Features
--------

The application provides a menu-driven interface to perform the following operations:

| Operation | Menu Choice | Description |
| Create | 1. Add Product | Adds a new product with a name, price, and quantity.
| Read | 2. View All Products | Displays the entire inventory, including calculated total value for each item.
| Update | 3. Update Product | Allows modification of an existing product's name, price, or quantity using its unique short ID.
| Delete | 4. Delete Product | Removes a product from the inventory using its unique short ID.

How to Run
----------

### Prerequisites

You need to have Python 3.x installed on your system.

### Steps

1.  **Save the Code:** Save the provided code into a file named `product_manager.py`.

2.  **Run from Terminal:** Open your terminal or command prompt, navigate to the directory where you saved the file, and execute the script:

    python product_manager.py

Usage Instructions
------------------

When you run the script, a main menu will appear.

### 1. Add Product (Create)

Enter 1 and follow the prompts to input the product's name, price (e.g., 1299.99), and quantity (e.g., 5).

### 2. View All Products (Read)

Enter 2 to display a formatted table of all products, including the generated short ID (the first 4 characters of the full ID) which is necessary for Update and Delete operations.

### 3. Update Product (Update)

1.  Enter 3. The inventory will be displayed first.
2.  Input the **first 4 characters of the ID** of the product you wish to modify.
3.  You will be prompted for a new name, price, and quantity. **You can leave any of these fields blank to skip updating that specific value.** (e.g., if you only want to change the price, leave the name and quantity prompts blank).

### 4. Delete Product (Delete)

1.  Enter 4. The inventory will be displayed first.
2.  Input the **first 4 characters of the ID** of the product you wish to delete. The product will be permanently removed from the in-memory list.

### 5. Exit

Enter 5 to cleanly close the application.
