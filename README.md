# ☕ Coffee Machine Simulator (OOP Project)

An interactive console-based Coffee Machine simulator written in **Python**.
This project focuses on **Object-Oriented Programming (OOP)** principles, demonstrating clean code architecture by separating concerns into distinct classes for menu management, resource handling, and financial processing.

## 🛠️ How It Works
The program simulates the full lifecycle of a coffee machine operation:
1.  **Menu Selection:** The user chooses a drink (Latte, Espresso, or Cappuccino).
2.  **Resource Verification:** The machine checks if there are sufficient ingredients (water, milk, coffee beans).
3.  **Payment Processing:** The user is prompted to insert coins (quarters, dimes, nickels, pennies).
4.  **Transaction:** The machine calculates the total, provides change, and dispenses the coffee if the payment is successful.
5.  **Maintenance:** Administrators can generate a `report` of current resources/profits or turn the machine `off`.

## 📂 File Structure & Function Breakdown

The project is modularized into 4 files to ensure maintainability and encapsulation:

### 1. `main.py` (Controller)
The entry point of the application. It orchestrates the interaction between the different objects.
* **Functionality:** Initializes the `Menu`, `CoffeeMaker`, and `MoneyMachine` objects.
* **Flow Control:** Runs a `while` loop that handles user input, triggers resource checks, and manages the payment/dispensing sequence.

### 2. `menu.py` (Data Model)
Handles the drink definitions and menu logic.
* **`class MenuItem`**: A model representing a single drink with its name, cost, and required ingredients.
* **`class Menu`**:
    * `get_items()`: Returns a formatted string of all available drink names (e.g., "latte/espresso/cappuccino").
    * `find_drink(order_name)`: Searches the menu list by name. Returns the corresponding `MenuItem` object if found, or `None` if the item doesn't exist.

### 3. `coffee_maker.py` (Hardware Simulation)
Manages the physical resources of the machine.
* **`class CoffeeMaker`**:
    * `__init__`: Initializes the machine's tanks with starting values (300ml water, 200ml milk, 100g coffee).
    * `report()`: Prints the current status of all resources remaining in the machine.
    * `is_resource_sufficient(drink)`: Checks if the machine has enough ingredients to make the requested `drink`. Returns `True` or `False`.
    * `make_coffee(order)`: Deducts the required ingredients from the internal storage and prints a success message.

### 4. `money_machine.py` (Financial Logic)
Handles all monetary transactions, coin processing, and profit tracking.
* **`class MoneyMachine`**:
    * `report()`: Prints the current total profit earned by the machine.
    * `process_coins()`: Prompts the user to insert coins, calculates the total monetary value, and returns it.
    * `make_payment(cost)`: The core transaction method:
        1. Calls `process_coins()`.
        2. Checks if the inserted amount covers the `cost`.
        3. Calculates and prints the change (rounded to 2 decimal places).
        4. Adds the cost to the machine's `profit`.
        5. Returns `True` if the transaction succeeded, or `False` if money was refunded due to insufficient funds.

## 🚀 How to Run
Ensure you have Python 3.x installed, then run:

```bash
python main.py
