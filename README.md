# MIST4610-Group-Project
## Team Name:
21479 Group 3

## Team Members:
1. Isabel Villaca [@icvillaca](https://github.com/icvillaca)
2. Carson Farris [@carsonf17](https://github.com/carsonf17)
3. Phoebe Prescott [@phoebeprescott](https://github.com/phoebeprescott)
4. Alexa Persad [@aepersad](https://github.com/aepersad)

## Problem Description:
Our task was to model and build a relational database for the operations of a coffee shop. The goal of this database is to accurately represent the processes by which a coffee shop handles customer orders, manages products, tracks employees, and records payments in its daily operations. The central entity is Order, which connects to both  customers and employees involved in each transaction. Order is made up of products and order items that define its contents. Payments and discounts that determine its total cost. Employees are tied to the shifts they work, while products are organized by category and are linked to their respective suppliers. We will also perform functioning queries with this data so that they may provide us with valuable business insight about the coffee shop and its operations, such as tracking product sales performance, analyzing customer spending and loyalty, and monitoring employee wages and discount activity. 

## Data Model
Our model is based on the structure of a basic local coffee shop. This database reflects how the coffee shop operates through each relationship between our multiple entities. Each order is placed by a customer, and has an employee who processes that order. A customer can place many orders while each order is placed by one customer, and each order is handled by one employee even though an employee can process many orders. Both our customer and employees table contains basic information about their name, contact information, etc. The customer entities also include information about our loyalty program, which enables tracking of how often our customers come in and their membership status. Each order may have a discount, which could be a BOGO, price reduction, etc. The orders are linked to payments, which record the subtotal, taxes, tips, and final total charged for that order. This data tracks financial details to determine products. Since an order can contain multiple of our products, and each product can appear in many different orders, we have an order_items table as the associative entity. The product table stores the name, size, price, and availability of our products, with each product belonging to a single category and the categories containing many products. Additionally, each of our products is supplied by our main suppliers, with suppliers being able to provide multiple products. Information about our employees are found through the employees table, which includes their role and wages, and connects their shifts through the shifts table. Overall, this database is designed to track information about the basic everyday operations of a coffee shop through key entities like customers, orders, products, payments, etc.



## Data Dictionary




## Queries

