Table: Orders

| Column Name | Description | Data Type | Size | Format | Key? |
| :---- | :---- | :---- | :---- | :---- | :---- |
| order\_id | PK, unique sequential number | INT |  |  | PK |
| order\_datetime | Date and time when the orders were placed | DATE TIME |  | yyyy/mm/dd hh:mm:ss |  |
| order\_status | Current status of the order (processed, pending, incomplete) | VARCHAR | 45 |  |  |
| employee\_id | Employee who processed the order | INT |  |  | FK employees |
| customer\_id | Customer who placed the order | INT |  |  | FK customers |
| discount\_id | Discount applied to the order (if any) | INT |  |  | FK discounts |

Table: Discounts

| Column Name | Description | Data Type | Size | Format | Key? |
| :---- | :---- | :---- | :---- | :---- | :---- |
| discount\_id | PK, unique sequential number for each discount | INT |  |  | PK |
| discount\_name | Name of the discount (holiday, seasonal, student, etc) | VARCHAR | 45 |  |  |
| discount\_type | Type of discount applied (percentage, BOGO, free shipping, etc.) | VARCHAR | 45 |  |  |
| discount\_value | Value of the discount in decimal format | DECIMAL | 10, 2 |  |  |
| start\_date | Date the discount become active | DATE |  | yyyy-mm-dd |  |
| end\_date | Date the discount expires | DATE |  | yyyy-mm-dd |  |
| is\_active | Shows whether the discount is currently active (active, inactive) | ENUM |  | (‘active’, ‘inactive’) |  |

Table: Customers

| Column Name | Description | Data Type | Size | Format | Key? |
| :---- | :---- | :---- | :---- | :---- | :---- |
| customer\_id | PK, unique sequential number | INT |  |  | PK |
| first\_name | Customer’s first name | VARCHAR | 45 |  |  |
| last\_name | Customer’s last name | VARCHAR | 45 |  |  |
| email | Customer’s email address | VARCHAR | 45 | Email format (blank@blank.com) |  |
| phone | Customer’s phone number | VARCHAR | 45 | (\#\#\#-\#\#\#-\#\#\#\#) |  |
| loyalty\_join\_date | Date and time the customer joined the loyalty program | DATETIME |  | Yyyy-mm-dd hh:mm:ss |  |
| is\_loyalty\_member | Shows whether the customer is in the loyalty program | ENUM |  | (‘yes’, ‘no’) |  |

Table: Payments

| Column Name | Description | Data Type | Size | Format | Key? |
| :---- | :---- | :---- | :---- | :---- | :---- |
| payment\_id | PK, unique sequential number for each payment transaction | INT |  |  | PK |
| payment\_method | Method used to pay for order (credit/debit card, cash, paypal/apple pay) | VARCHAR | 45 |  |  |
| subtotal | Total cost of items before discounts and tax | DECIMAL | 10, 2 |  |  |
| discount\_amount | Amount deducted from payment using discounts | DECIMAL | 10,2 |  |  |
| tax\_amount | Amount of sales tax applied to the order | DECIMAL | 10,2 |  |  |
| total\_amount | Final amount charged after everything is applied | DECIMAL | 10,2 |  |  |
| tip\_amount | Tip amount added by customer (optional) | DECIMAL | 10,2 |  |  |
| orders\_id | Identifier of order associated with the payment | INT |  |  | FK, orders |

Table: Order\_Items

| Column Name | Description | Data Type | Size | Format | Key? |
| :---- | :---- | :---- | :---- | :---- | :---- |
| order\_item\_id | PK, unique identifier for each item in an order  | INT |  |  | PK |
| quantity | Number of products in this order line ?? | INT |  |  |  |
| unit\_price\_at\_sale | Price of one unit of the product at the time of sale | DECIMAL | 10, 2 |  |  |
| line\_notes | Additional notes for this order (special instructions) | VARCHAR | 45 |  |  |
| orders\_id | Identifier of which order this item belongs to | INT |  |  | FK orders |
| products\_id | Identifier of the product being ordered | INT |  |  | FK products |

Table: Products

| Column Name | Description | Data Type | Size | Format | Key? |
| :---- | :---- | :---- | :---- | :---- | :---- |
| product\_id | PK, unique sequential number  | INT |  |  | PK |
| category\_id | Identifier of the product category | INT |  |  |  |
| product\_name | Name of the product | VARCHAR | 45 |  |  |
| size\_label | Size of the product (small, medium, large) | VARCHAR | 45 |  |  |
| unit\_price | Current price per unit of the product ?? | DECIMAL | 10,2 |  |  |
| is\_active | Shows whether the product is currently available for sale | ENUM |  | (‘yes’,’no’) |  |
| product\_categories\_category\_id | Foreign key linking to product category table ?? | INT |  |  | FK |
| supplier\_id | Identifier of the supplier providing the product | INT |  |  | FK |
| suppliers\_supplier\_id | ??? | INT |  |  | FK, suppliers |

Table: Suppliers

| Column Name | Description | Data Type | Size | Format | Key? |
| :---- | :---- | :---- | :---- | :---- | :---- |
| supplier\_id | PK, unique sequential number for a supplier | INT |  |  | PK |
| supplier \_name | Name of the supplier company | VARCHAR | 45 |  |  |
| contact\_name | Name of the main contact person at the supply company | VARCHAR | 45 |  |  |
| phone | Supplier’s phone number | VARCHAR | 45 | Phone \# (\#\#\#-\#\#\#-\#\#\#\#) |  |
| email | Supplier’s email address | VARCHAR | 45 | Email (blank@blank.com) |  |

Table: Employees

| Column Name | Description | Data Type | Size | Format | Key? |
| :---- | :---- | :---- | :---- | :---- | :---- |
| employee\_id | PK, unique sequential number for each employee | INT |  |  | PK |
| first\_name | Employee’s first name | VARCHAR | 45 |  |  |
| last\_name | Employee’s last name | VARCHAR | 45 |  |  |
| email | Employee’s email address  | VARCHAR | 45 |  |  |
| role\_title | Employees job role (barista, supervisor, cashier, manager) | VARCHAR | 45 |  |  |
| hire\_date | Date the employee was hired | DATE |  | yyyy-mm-dd |  |
| hourly\_wage | Employees hourly pay rate | DECIMAL | 6,2 |  |  |

Table: Shifts

| Column Name | Description | Data Type | Size | Format | Key? |
| :---- | :---- | :---- | :---- | :---- | :---- |
| shift\_id | PK, unique sequential number for shift | INT |  |  | PK |
| shift\_start | Date and time of the start of the shift   | DATETIME |  | Yyyy-mm-dd hh:mm:ss |  |
| shift\_end | Date and time of the end of the shift  | DATETIME |  | Yyyy-mm-dd hh:mm:ss |  |
| station | Work station employee used during the shift (BAR, REG, KTC) | VARCHAR | 45 |  |  |
| employees\_id | Identifier of the employee assigned to the shift | INT |  |  | FK |

