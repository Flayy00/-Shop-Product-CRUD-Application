# 📦 Simple Python Inventory Management System (CRUD CLI)

This is a simple, console-based **Product Inventory Management** application written in Python. It utilizes a class-based approach (`ProductManager`) and stores product data in an **in-memory list of dictionaries**.

The system provides standard **CRUD (Create, Read, Update, Delete)** operations and can generate a financial snapshot of the current inventory.

## ✨ Features

* **Create (Add Product):** Adds a new product with a unique `uuid` and timestamp.
* **Read (View All Products):** Lists all products with calculated total value per item.
* **Update (Update Product):** Modifies an existing product's name, price, or quantity using a **short ID** (first 4 characters of the UUID).
* **Delete (Delete Product):** Removes a product from the inventory using its short ID.
* **Generate Statement:** Provides a summary of the total unique products, total units, and total estimated inventory value.

## 🚀 How to Run

### Prerequisites

You need **Python 3.x** installed on your system.

### Running the Application

1.  **Save the code:** Save the provided Python code into a file named `inventory_app.py`.
2.  **Run from the terminal:** Execute the file using the Python interpreter:

    ```bash
    python inventory_app.py
    ```

## 💻 Example Interaction

The application will start by automatically adding a few default products and presenting a menu.

### Initial Output
