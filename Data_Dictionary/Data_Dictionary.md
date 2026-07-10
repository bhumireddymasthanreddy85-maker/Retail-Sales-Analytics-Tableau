# Data Dictionary

## Project
Retail Sales Analytics Dashboard

## Dataset
Northwind OData Dataset

---

# Customers Table

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| CustomerID | Text | Unique identifier for each customer. Primary Key. |
| CompanyName | Text | Name of the customer company. |
| ContactName | Text | Primary contact person of the customer. |
| ContactTitle | Text | Job title of the contact person. |
| Address | Text | Customer address. |
| City | Text | City where the customer is located. |
| Region | Text | State or region of the customer. |
| PostalCode | Text | Postal or ZIP code. |
| Country | Text | Customer country. |
| Phone | Text | Customer phone number. |
| Fax | Text | Customer fax number. |

---

### Primary Key
- CustomerID

### Business Purpose
Stores customer information used for analyzing customer sales, regional sales performance, and customer purchasing behavior.

---

# Orders Table

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| OrderID | Integer | Unique order identifier. Primary Key. |
| CustomerID | Text | Customer who placed the order. Foreign Key. |
| EmployeeID | Integer | Employee responsible for the order. |
| OrderDate | Date | Date when the order was placed. |
| RequiredDate | Date | Required delivery date. |
| ShippedDate | Date | Actual shipment date. |
| ShipVia | Integer | Shipping company identifier. |
| Freight | Decimal | Shipping charges. |
| ShipName | Text | Shipping recipient name. |
| ShipCity | Text | Destination city. |
| ShipCountry | Text | Destination country. |

---

### Primary Key
- OrderID

### Foreign Key
- CustomerID → Customers.CustomerID

### Business Purpose
Stores every customer order and forms the basis for sales analysis.\

---

# Order Details Table

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| OrderID | Integer | Unique order identifier. Foreign Key. |
| ProductID | Integer | Product identifier. Foreign Key. |
| UnitPrice | Decimal | Selling price of the product at the time of the order. |
| Quantity | Integer | Number of units ordered. |
| Discount | Decimal | Discount applied to the product (0–1). |

---

### Primary Key
- Composite Key (OrderID + ProductID)

### Foreign Keys
- OrderID → Orders.OrderID
- ProductID → Products.ProductID

### Business Purpose
Stores the individual products included in each customer order. This table is the core fact table used to calculate revenue, sales trends, product performance, and customer purchasing behavior.

### Business Metrics Derived
- Total Sales = UnitPrice × Quantity × (1 - Discount)
- Total Quantity Sold
- Average Order Value
- Product Revenue
- Discount Analysis

---

# Products Table

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| ProductID | Integer | Unique identifier for each product. Primary Key. |
| ProductName | Text | Name of the product. |
| SupplierID | Integer | Supplier who provides the product. Foreign Key. |
| CategoryID | Integer | Product category. Foreign Key. |
| QuantityPerUnit | Text | Package quantity information. |
| UnitPrice | Decimal | Current selling price of the product. |
| UnitsInStock | Integer | Number of units currently available in inventory. |
| UnitsOnOrder | Integer | Number of units currently on order from suppliers. |
| ReorderLevel | Integer | Stock level at which new inventory should be ordered. |
| Discontinued | Boolean | Indicates whether the product is discontinued. |

---

### Primary Key
- ProductID

### Foreign Keys
- SupplierID → Suppliers.SupplierID
- CategoryID → Categories.CategoryID

### Business Purpose

Stores detailed information about every product sold by the company. This table is used to analyze product performance, inventory levels, pricing, and category-wise sales.

---

# Categories Table

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| CategoryID | Integer | Unique identifier for each product category. Primary Key. |
| CategoryName | Text | Name of the product category. |
| Description | Text | Description of the category. |

---

### Primary Key
- CategoryID

### Business Purpose

Stores product category information used to analyze category-wise sales, product performance, and profitability.

---

# Suppliers Table

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| SupplierID | Integer | Unique identifier for each supplier. Primary Key. |
| CompanyName | Text | Supplier company name. |
| ContactName | Text | Supplier contact person. |
| City | Text | Supplier city. |
| Country | Text | Supplier country. |
| Phone | Text | Supplier phone number. |

---

### Primary Key
- SupplierID

### Business Purpose

Stores supplier information for analyzing supplier contributions and product sourcing.

---

# Employees Table

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| EmployeeID | Integer | Unique employee identifier. Primary Key. |
| FirstName | Text | Employee first name. |
| LastName | Text | Employee last name. |
| Title | Text | Employee job title. |
| City | Text | Employee city. |
| Country | Text | Employee country. |
| HireDate | Date | Employee hiring date. |

---

### Primary Key
- EmployeeID

### Business Purpose

Stores employee information used to evaluate sales performance and order management by employees.

---

# Shippers Table

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| ShipperID | Integer | Unique shipper identifier. Primary Key. |
| CompanyName | Text | Shipping company name. |
| Phone | Text | Contact phone number. |

---

### Primary Key
- ShipperID

### Business Purpose

Stores shipping company information used to analyze shipping methods and logistics performance.