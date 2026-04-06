# Fast-Food Order Record Management System

## 1. Project Overview

The Fast-Food Order Record Management System is a Java-based command-line application designed to support the daily operation of a fast-food business. The system manages food ordering activities, menu administration, promotional code handling, receipt generation, and order record tracking through a role-based interface for staff and administrators.

This project was developed as an academic programming exercise with the objective of applying object-oriented programming concepts, file handling, modular program structure, and user interaction design in a practical business scenario.
 
## 2. Project Goal

The primary goal of this system is to provide a structured and efficient way to:

- record and manage customer food orders;
- maintain menu items, categories, and combo sets;
- support staff in handling customer orders;
- support administrators in managing operational data and reviewing sales records; and
- persist system data using CSV-based storage files.

## 3. Scope of the System

This system focuses on the operational needs of a small fast-food ordering environment. Its scope includes:

- staff and admin account registration and login;
- customer order placement and payment processing;
- menu display, search, and category filtering;
- menu, category, and promo code management;
- order tracking and filtering;
- receipt generation and storage; and
- daily sales reporting and popularity analysis.

The project is implemented as a local CLI application and does not include:

- a database management system;
- networked or multi-branch deployment;
- online customer self-service ordering; or
- web or mobile interface support.

## 4. Target Users

The system is intended for the following user groups:

### Staff

Staff users handle customer-facing ordering operations. They can create customer orders, review existing orders, and check available promo codes.

### Admin

Admin users are responsible for business control and system maintenance. They can manage menu items, categories, promo codes, and reports.

### Customer

Customers are represented in the ordering workflow when staff place and manage orders on their behalf. Customer information and order history are stored for record purposes.

## 5. System Approach and Design

The system follows a role-based command-line workflow:

1. The program starts from `MainSystem.java`.
2. The user chooses whether to enter as staff or admin.
3. Each role accesses a dedicated menu with relevant functions.
4. Business data is stored in CSV files under the `System Data/` directory.
5. Receipts are exported as text files into `System Data/Receipts/`.

From a software design perspective, the project uses:

- object-oriented design with separate classes for users, menu items, orders, and promo codes;
- inheritance and polymorphism in menu handling;
- file-based persistence using CSV storage; and
- modular source files to separate responsibilities such as category management, file management, and colour customization.

## 6. Main Features Supported

### 6.1 General Features

- Role selection between staff and admin
- CLI colour customization
- Persistent file-based storage
- Input validation and error handling
- Automatic loading and saving of operational data

### 6.2 Staff Functions

Staff users can perform the following operations:

- register a new staff account using the staff registration code;
- log in to the system;
- view existing orders for a selected date;
- filter orders by customer name for a selected date;
- place an order for a customer;
- search available promo codes; and
- view permanent promo codes.

### 6.3 Customer Ordering Functions

Within the staff ordering workflow, the customer order module supports:

- entering customer name and phone number;
- entering delivery address;
- resuming an unpaid order if one already exists for the same customer;
- showing available menu items;
- searching menu items by ID or name;
- filtering menu items by category;
- viewing the current order cart;
- adding items into the cart;
- removing items from the cart;
- applying promo codes;
- selecting a payment method; and
- generating a receipt after successful payment.

### 6.4 Admin Functions

Admin users can perform the following operations:

- register a new admin account using the admin registration code;
- log in to the system;
- display the full menu;
- search menu items by item ID or name;
- filter menu items by category;
- manage menu items;
- manage categories;
- manage promo codes;
- filter paid orders by date;
- view the most popular items; and
- generate a daily sales report.

### 6.5 Admin Menu Management Functions

Admin menu management includes:

- adding food, drink, or combo items;
- removing menu items;
- editing existing menu items;
- setting item availability;
- managing combo exchange options; and
- saving all updates back into the corresponding CSV files.

### 6.6 Promo Code Management Functions

The system supports:

- generation of permanent promo codes;
- batch generation of one-time-use promo codes;
- viewing existing promo codes; and
- deleting promo codes.

## 7. Registration Codes

The following registration codes are required when creating privileged accounts:

- Staff Registration Code: `8888`
- Admin Registration Code: `9999`

These codes are used during sign-up to restrict account creation by role.

## 8. Project Structure

### Source Code

The main source files are stored in the `src/` folder.

Key files include:

- `MainSystem.java` - program entry point
- `MenuFactory.java` - role selection and initial navigation
- `Menu.java` - abstract base menu class
- `StaffMenu.java` - staff workflow and functions
- `AdminMenu.java` - admin workflow and functions
- `CustomerMenu.java` - customer ordering workflow
- `FileManager.java` - CSV file loading and saving
- `ColourManager.java` - CLI colour customization
- `CategoryManager.java` - category maintenance
- `Order.java` and `OrderItem.java` - order processing logic
- `Food.java`, `Drink.java`, `Combo.java`, and `MenuItem.java` - menu item models
- `PromoCode.java` - promo code generation and handling

### Data Storage

The system stores operational files in the `System Data/` folder.

Files used by the system include:

- `admins.csv` - admin usernames and passwords
- `staff.csv` - staff usernames and passwords
- `customers.csv` - customer records
- `orders.csv` - paid and unpaid order records
- `foods.csv` - food menu items
- `drinks.csv` - drink menu items
- `combos.csv` - combo menu items
- `food_categories.csv` - food categories
- `drink_categories.csv` - drink categories
- `promocodes.csv` - promo code records
- `colour_settings.csv` - saved CLI colour settings
- `Receipts/` - generated receipt text files

If any required data file is missing, the program may show an error during execution. Restarting the system may recreate required folders or files depending on the module involved.

## 9. How to Run the Program

### Requirements

- Java Development Kit (JDK) installed
- A Java-compatible IDE or terminal environment

### Compile and Run from Terminal

From the project root directory:

```powershell
javac src\*.java
java -cp src MainSystem
```

### Run from an IDE

1. Open the project in your Java IDE.
2. Ensure the working directory is the project root folder.
3. Run `MainSystem.java`.

## 10. Basic User Manual

### 10.1 Program Start

When the system starts, the main menu allows the user to:

- enter as `Staff`;
- enter as `Admin`; or
- open `CLI Colour Customization`.

### 10.2 Staff Workflow

1. Choose `Staff`.
2. Log in or sign up.
3. After login, select one of the available staff functions.
4. To place an order, enter customer information and delivery address.
5. Use the customer menu to add items, review the cart, and make payment.
6. After payment, the system prints and saves a receipt.

### 10.3 Admin Workflow

1. Choose `Admin`.
2. Log in or sign up.
3. Use the admin menu to review menu data, maintain categories and promo codes, or inspect order records.
4. Use the reporting functions to review popular items and generate daily sales summaries.

### 10.4 Payment and Receipt Workflow

During customer payment:

- the system displays the customer information and order summary;
- the user may apply a valid promo code;
- the user selects a payment method;
- the order is marked as paid; and
- a receipt file is generated in `System Data/Receipts/`.

Supported payment methods include:

- `COD`
- `QR Pay`
- `Debit Card`
- `Credit Card`
- `FPX Transfer`

## 11. Functional Summary by Role

| Role | Main Responsibilities |
|------|-----------------------|
| Staff | Manage customer orders, review orders, search promo codes |
| Admin | Manage menu, categories, promo codes, and reporting |
| Customer | Provide order details through staff-assisted workflow |

## 12. Notes and Assumptions

- The system is designed for local execution.
- Data is stored in plain CSV files for simplicity and academic demonstration.
- The application is best suited for learning purposes and small-scale record management.
- Password entry for staff and admin login uses the project’s implemented input mechanism, including GUI-assisted password input in the current version.
- Some features depend on the availability and correctness of files inside `System Data/`.

## 13. Conclusion

This project demonstrates how a fast-food ordering and record management process can be implemented using Java object-oriented programming and file handling. It provides a structured example of role-based access, order processing, menu administration, promo code management, and report generation in a command-line environment.
