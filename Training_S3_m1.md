# inventario_tienda.py

# Diccionario para almacenar productos: clave = nombre, valor = (precio, cantidad)
inventario = {}

```python
# store_inventory.py

# Dictionary to store products: key = name, value = (price, quantity)
inventory = {}

# Function to add a product to the inventory
def add_product(name, price, quantity):
    if name in inventory:
        print("Product already exists. Use the update option to change its data.")
    else:
        inventory[name] = (price, quantity)
        print(f"Product '{name}' successfully added.")

# Function to search for a product by name
def search_product(name):
    return inventory.get(name, None)

# Function to update the price of an existing product
def update_price(name, new_price):
    if name in inventory:
        quantity = inventory[name][1]
        inventory[name] = (new_price, quantity)
        print(f"Price of product '{name}' updated to {new_price}.")
    else:
        print("Product not found.")

# Function to remove a product from the inventory
def remove_product(name):
    if name in inventory:
        del inventory[name]
        print(f"Product '{name}' removed from inventory.")
    else:
        print("Product not found.")

# Function to calculate the total value of the inventory using a lambda function
def calculate_total_value():
    total = sum(map(lambda item: item[1][0] * item[1][1], inventory.items()))
    return total
    # item[1][0] = price, item[1][1] = quantity → price * quantity for each product

# Function to validate numeric input from the user
def request_number(message):
    while True:
        entry = input(message)
        if entry.replace('.', '', 1).isdigit():
            return float(entry)
        else:
            print("Invalid input. Please enter a number.")

# Interactive menu
def menu():
    while True:
        print("\n--- INVENTORY MENU ---")
        print("1. Add product")
        print("2. Search product")
        print("3. Update product price")
        print("4. Remove product")
        print("5. Calculate total inventory value")
        print("6. Show all products")
        print("7. Exit")

        option = input("Choose an option (1-7): ")

        if option == "1":
            name = input("Product name: ")
            price = request_number("Product price: ")
            quantity = request_number("Available quantity: ")
            add_product(name, price, int(quantity))

        elif option == "2":
            name = input("Enter product name to search: ")
            result = search_product(name)
            if result:
                print(f"Product: {name}, Price: {result[0]}, Quantity: {result[1]}")
            else:
                print("Product not found.")

        elif option == "3":
            name = input("Enter product name to update: ")
            new_price = request_number("New price: ")
            update_price(name, new_price)

        elif option == "4":
            name = input("Enter product name to remove: ")
            remove_product(name)

        elif option == "5":
            total = calculate_total_value()
            print(f"Total inventory value: ${total:.2f}")

        elif option == "6":
            if inventory:
                for name, (price, quantity) in inventory.items():
                    print(f"{name} - Price: ${price}, Quantity: {quantity}")
            else:
                print("Inventory is empty.")

        elif option == "7":
            print("Exiting program.")
            break

        else:
            print("Invalid option. Please try again.")

# Run the main menu
menu()
```
