import uuid
from datetime import datetime

class ProductManager:
    """
    Manages a simple in-memory inventory of products using a list of dictionaries.
    Provides methods for Create, Read, Update, and Delete operations.
    """
    def __init__(self):
        # The main data structure to hold products: a list of dictionaries.
        self.products = []

    def add_product(self, name: str, price: float, quantity: int):
        """
        Creates a new product and adds it to the inventory.
        """
        if not name or price <= 0 or quantity <= 0:
            print("\nError: Invalid product details. Name must be non-empty, price and quantity must be positive.")
            return

        new_product = {
            "id": str(uuid.uuid4()),  # Generate a unique ID for the product
            "name": name,
            "price": price,
            "quantity": quantity,
            "created_at": datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        }
        self.products.append(new_product)
        print(f"\n✅ Product '{name}' added successfully with ID: {new_product['id']}")

    def view_products(self):
        """
        Reads and displays all products in the inventory.
        """
        if not self.products:
            print("\n--- Inventory is Empty ---")
            print("No products available. Please add a product first.")
            return

        print("\n--- Current Product Inventory ---")
        print("{:<4} {:<20} {:<10} {:<8} {:<15} {:<20}".format(
            "ID", "Name", "Price", "Qty", "Total Value", "Created At"
        ))
        print("-" * 80)

        # Sort products by creation time (most recent first) for better viewing
        sorted_products = sorted(self.products, key=lambda p: p['created_at'], reverse=True)

        for i, product in enumerate(sorted_products):
            short_id = product['id'][:4] # Display a short ID for readability
            total_value = product['price'] * product['quantity']
            print("{:<4} {:<20} ${:<9.2f} {:<8} ${:<14.2f} {:<20}".format(
                short_id,
                product['name'],
                product['price'],
                product['quantity'],
                total_value,
                product['created_at']
            ))
        print("-" * 80)

    def find_product_by_short_id(self, short_id: str):
        """Helper to find a product using the first 4 characters of the ID."""
        for product in self.products:
            if product['id'].startswith(short_id):
                return product
        return None

    def update_product(self, short_id: str, new_name: str, new_price: float, new_quantity: int):
        """
        Updates an existing product's details using its short ID.
        """
        product = self.find_product_by_short_id(short_id)

        if not product:
            print(f"\n❌ Error: Product with short ID '{short_id}' not found.")
            return

        # Perform validation on new values
        if new_name:
            product['name'] = new_name
        if new_price > 0:
            product['price'] = new_price
        if new_quantity > 0:
            product['quantity'] = new_quantity
        
        print(f"\n✏️ Product '{product['name']}' (ID: {short_id}) updated successfully.")

    def delete_product(self, short_id: str):
        """
        Deletes a product from the inventory using its short ID.
        """
        product_to_delete = self.find_product_by_short_id(short_id)
        
        if product_to_delete:
            self.products.remove(product_to_delete)
            print(f"\n🗑️ Product '{product_to_delete['name']}' (ID: {short_id}) deleted successfully.")
        else:
            print(f"\n❌ Error: Product with short ID '{short_id}' not found.")


def main():
    """
    Main function to run the command-line interface.
    """
    manager = ProductManager()

    # Add a few default products for easy testing
    manager.add_product("Laptop Pro X", 1299.99, 5)
    manager.add_product("Wireless Mouse", 25.50, 50)
    manager.add_product("USB-C Cable", 8.00, 100)
    
    while True:
        print("\n====================================")
        print("  Shop Product CRUD Application (CLI)")
        print("====================================")
        print("1. Add Product (Create)")
        print("2. View All Products (Read)")
        print("3. Update Product (Update)")
        print("4. Delete Product (Delete)")
        print("5. Exit")
        
        choice = input("Enter your choice (1-5): ").strip()

        try:
            if choice == '1':
                # --- Create ---
                print("\n--- Add New Product ---")
                name = input("Enter product name: ").strip()
                price = float(input("Enter price: "))
                quantity = int(input("Enter quantity: "))
                manager.add_product(name, price, quantity)
            
            elif choice == '2':
                # --- Read ---
                manager.view_products()

            elif choice == '3':
                # --- Update ---
                manager.view_products()
                if not manager.products: continue
                
                print("\n--- Update Product ---")
                short_id = input("Enter the first 4 characters of the ID to update: ").strip()
                if not short_id: continue

                # Get new data, allowing empty input to skip updates
                new_name = input(f"Enter new name (current: {manager.find_product_by_short_id(short_id)['name'] if manager.find_product_by_short_id(short_id) else 'N/A'}, leave blank to skip): ").strip()
                
                try:
                    new_price_str = input(f"Enter new price (current: ${manager.find_product_by_short_id(short_id)['price'] if manager.find_product_by_short_id(short_id) else 'N/A'}, leave blank to skip): ").strip()
                    new_price = float(new_price_str) if new_price_str else -1
                except ValueError:
                    new_price = -1 # Sentinel value to indicate no update or invalid non-numeric input

                try:
                    new_quantity_str = input(f"Enter new quantity (current: {manager.find_product_by_short_id(short_id)['quantity'] if manager.find_product_by_short_id(short_id) else 'N/A'}, leave blank to skip): ").strip()
                    new_quantity = int(new_quantity_str) if new_quantity_str else -1
                except ValueError:
                    new_quantity = -1 # Sentinel value to indicate no update or invalid non-numeric input
                
                # Update only if at least one field has valid input
                if new_name or new_price > 0 or new_quantity > 0:
                    manager.update_product(short_id, new_name, new_price, new_quantity)
                else:
                    print("\nNo valid fields provided for update. Operation cancelled.")

            elif choice == '4':
                # --- Delete ---
                manager.view_products()
                if not manager.products: continue
                
                print("\n--- Delete Product ---")
                short_id = input("Enter the first 4 characters of the ID to delete: ").strip()
                manager.delete_product(short_id)

            elif choice == '5':
                # --- Exit ---
                print("\n👋 Exiting Application. Thank you!")
                break
            
            else:
                print("\n⚠️ Invalid choice. Please enter a number between 1 and 5.")

        except ValueError:
            print("\n❌ Invalid input. Please ensure price is a number and quantity is an integer.")
        except Exception as e:
            print(f"\n🚨 An unexpected error occurred: {e}")

if __name__ == "__main__":
    main()
