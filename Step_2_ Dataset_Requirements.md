# Step 2: Dataset & Requirements - Supply Chain Management System

## Introduction
In this step, we will explore the structure of the **Supply Chain Management System** database. Understanding the entities and their relationships is crucial before writing any SQL code.

## Database Schema
The database consists of five main tables that represent the core components of a supply chain:
1.  **Customer:** Stores information about individuals who place orders.
2.  **Orders:** Records each transaction made by a customer.
3.  **OrderItem:** Details the specific products and quantities within each order.
4.  **Product:** Contains information about the items available for sale.
5.  **Supplier:** Lists the companies that provide the products.

## Entity-Relationship (ER) Overview
The relationships between these tables are as follows:
*   **Customer to Orders:** One customer can place many orders (1:N).
*   **Orders to OrderItem:** One order can contain multiple items (1:N).
*   **Product to OrderItem:** One product can appear in many order items (1:N).
*   **Supplier to Product:** One supplier can provide multiple products (1:N).

## Detailed Table Descriptions

### 1. Customer Table
| Column | Data Type | Description |
| :--- | :--- | :--- |
| **Id** | INT | Unique identifier for the customer (Primary Key). |
| **FirstName** | VARCHAR(40) | Customer's first name. |
| **LastName** | VARCHAR(40) | Customer's last name. |
| **City** | VARCHAR(40) | City where the customer resides. |
| **Country** | VARCHAR(40) | Country where the customer resides. |
| **Phone** | VARCHAR(20) | Contact phone number. |

### 2. Orders Table
| Column | Data Type | Description |
| :--- | :--- | :--- |
| **Id** | INT | Unique identifier for the order (Primary Key). |
| **OrderDate** | DATETIME | Date and time when the order was placed. |
| **OrderNumber** | VARCHAR(10) | Unique order number for tracking. |
| **CustomerId** | INT | Links to the Customer table (Foreign Key). |
| **TotalAmount** | DECIMAL(12,2) | Total cost of the order. |

### 3. OrderItem Table
| Column | Data Type | Description |
| :--- | :--- | :--- |
| **Id** | INT | Unique identifier for the order item (Primary Key). |
| **OrderId** | INT | Links to the Orders table (Foreign Key). |
| **ProductId** | INT | Links to the Product table (Foreign Key). |
| **UnitPrice** | DECIMAL(12,2) | Price per unit at the time of order. |
| **Quantity** | INT | Number of units ordered. |

### 4. Product Table
| Column | Data Type | Description |
| :--- | :--- | :--- |
| **Id** | INT | Unique identifier for the product (Primary Key). |
| **ProductName** | VARCHAR(50) | Name of the product. |
| **SupplierId** | INT | Links to the Supplier table (Foreign Key). |
| **UnitPrice** | DECIMAL(12,2) | Current price per unit of the product. |
| **Package** | VARCHAR(30) | Packaging details (e.g., "10 boxes"). |
| **IsDiscontinued** | BIT(1) | Status (1 = Discontinued, 0 = Active). |

### 5. Supplier Table
| Column | Data Type | Description |
| :--- | :--- | :--- |
| **Id** | INT | Unique identifier for the supplier (Primary Key). |
| **CompanyName** | VARCHAR(40) | Name of the supplier company. |
| **ContactName** | VARCHAR(50) | Name of the primary contact person. |
| **ContactTitle** | VARCHAR(40) | Title of the contact person. |
| **City** | VARCHAR(40) | City where the supplier is located. |
| **Country** | VARCHAR(40) | Country where the supplier is located. |
| **Phone** | VARCHAR(30) | Contact phone number. |
| **Fax** | VARCHAR(30) | Fax number for the supplier. |

## Business Rules & Constraints
*   **Primary Keys:** Every table must have a unique `Id` column to identify each record.
*   **Foreign Keys:** Relationships between tables must be enforced to ensure data consistency (e.g., an order cannot exist for a non-existent customer).
*   **Not Null:** Critical columns like `FirstName`, `OrderDate`, and `ProductName` must always contain data.
*   **Indexing:** Indexes should be created on frequently searched columns like `LastName` and `OrderDate` to improve query performance.

---
*Next, proceed to **Step 3: SQL Code** to begin building your database.*
