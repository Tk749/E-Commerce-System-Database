# E-Commerce Database Management System with GUI Integration

---

# Project Overview

This project is an E-Commerce System Database designed to streamline the management of online shopping platforms. Its goal is to provide a reliable, scalable, and secure infrastructure, ensuring a smooth shopping experience for users.

The database stores and manages essential data such as users, products, shopping carts, orders, payments, and invoices. To ensure data integrity and efficiency, tables are structured systematically, and strong relationships are established.

To provide enhanced functionality, the database supports:
- **Customer loyalty programs**
- **Multiple payment methods**
- **Order and invoice tracking**
- **Hierarchical address management**
- **Transaction processing with ACID compliance**
- **Concurrency control for multi-user operations**

Additionally, the system includes a **graphical user interface (GUI)** developed using **PyQt5**, allowing users to execute SQL queries, manage database views, triggers, and transactions interactively.

---

# Project detail

### **1. Data Storage Requirements**
The e-commerce system requires secure storage for essential data such as user information, addresses, products, shopping carts, orders, payments, and invoices. The main components include:

- **User Data:** User identities, email addresses, and roles (customer or admin).
- **Address Information:** User addresses are stored hierarchically with links to country, city, town, and district tables.
- **Product Data:** Includes product codes, names, prices, and categories.
- **Shopping Cart & Order Management:** Tracks user shopping carts and orders in detail.
- **Payment Information:** Stores user payments, payment type, approval codes, and error messages.
- **Invoice Management:** Maintains invoices linked to orders, storing invoice details.

### **2. E-R Diagram and Data Model**
The database model defines relationships between different tables to enhance user experience. 
- The `USER_` table contains basic user data, while `CUSTOMER` and `ADMIN` tables differentiate user roles.
- The `ADDRESS`, `ITEM`, `BASKET`, `ORDER`, and `PAYMENT` tables manage core system transactions.

### **3. Functional Dependencies**
Functional dependencies among database tables have been defined to ensure relational integrity. For example:
- `USER_.ID → NAME, EMAIL` (A user's ID determines their name and email.)
- `BASKET.ID → USERID, TOTALPRICE` (A basket's ID determines the associated user and total price.)
- `ORDER.ID → USERID, BASKETID, TOTALPRICE` (An order's ID links to a user and basket.)

### **4. Normalization Process**
To reduce redundancy and maintain data integrity, normalization techniques are applied:
- **1NF:** Ensures atomicity and unique rows.
- **2NF:** Eliminates partial dependencies, ensuring all attributes depend entirely on primary keys.
- **3NF:** Removes transitive dependencies for optimal structure.
- **BCNF:** Ensures every determinant is a super key.

### **5. Database Implementation**
To maintain data integrity, the system establishes relationships between tables:
- `CUSTOMER` and `ADMIN` tables reference the `USER_` table.
- `ADDRESS` table is linked to `USER_`, `COUNTRY`, `CITY`, `TOWN`, and `DISTRICT` tables.
- `BASKETDETAIL` table relates to `BASKET` and `ITEM` tables.
- `ORDERDETAIL` table connects to `ORDER`, `BASKETDETAIL`, and `ITEM` tables.

### **6. Keys and Relationships**
The system uses **primary keys (PK)** and **foreign keys (FK)** to enforce data integrity. Examples:
- `USER_ (PK: ID)`
- `CUSTOMER (PK: ID, FK: USER_.ID)`
- `BASKET (PK: ID, FK: USER_.ID)`
- `ORDER (PK: ID, FK: USER_.ID, FK: BASKET.ID)`
- `INVOICE (PK: ID, FK: ORDER.ID)`

### **7. Query Development and Views**
To simplify database management, various SQL queries and views have been created:
- **INNER JOIN:** Retrieves user-related shopping cart data.
- **LEFT JOIN:** Lists users with or without matching addresses.
- **RIGHT JOIN:** Retrieves order and payment details.
- **FULL OUTER JOIN:** Combines basket and order records for comprehensive reporting.
- **Views:** Predefined queries for users, addresses, orders, cart details, and payments.

### **8. Transactions and Concurrency Control**
To ensure consistency and prevent conflicts, the system applies:
- **Locking Mechanisms:** Prevents simultaneous modifications using `FOR UPDATE`.
- **Timestamp Ordering:** Ensures transactions execute in sequential order.
- **Multi-Version Concurrency Control (MVCC):** Allows data reads while updates occur.

### **9. Inheritance and Authorization**
- The `CUSTOMER` and `ADMIN` tables inherit attributes from the `USER_` table, preserving hierarchical relationships.
- **Role-Based Access Control (RBAC):**
  - `ADMIN`: Full database access.
  - `CUSTOMER`: Restricted to personal order and payment data.
  - **Constraints:** Users can only access their own records.

### **10. Graphical User Interface (GUI)**
The **SQL Runner** GUI, built using **PyQt5**, provides an interactive environment for executing and managing SQL commands. The interface consists of several key components:
- **SQL Query Execution Tab:** Users can write and execute SQL queries, with results displayed in a table format.
- **Trigger Management Tab:** Allows users to create and execute database triggers.
- **View Management Tab:** Enables the creation of SQL views for predefined queries.
- **Transaction Handling Tab:** Supports transaction execution with commit and rollback functionality.
- **User Selection:** Provides an option to switch between different database users.

The GUI enhances usability by allowing database operations to be performed without requiring direct SQL command-line interaction. It ensures a **user-friendly and efficient way** to manage database queries, transactions, and views.

[Project Report](./Report.pdf)
