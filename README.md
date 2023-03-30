# MIST4610 Group Project
## Team Name and Members
We are team 21482_4. <br>

### Team Members <br>
* [Jimmy Chancellor](https://github.com/JChancello/Groupproject1) <br>
* [Austin Crispo](https://github.com/austincrispo/MIST-4610-Project-1) <br>
* [Clayton Hoarell](https://github.com/claytonh153454/MIST4610) <br>
* [Tabea Lent](https://github.com/tabealent/mist4610_project) <br>
* [Mary Grace Tippett](https://github.com/mgtipp/MIST4610_project)

## Problem Description
Our group created a data model for the inventory management system of a Target store. For each Target store we wanted to be able to be able to track all of the different aspects that help run the operation. 
<br> <br>
We decided the first thing we needed to model for a merchandiser is products.  We thought it would be important to start with the essential business aspects of the products such as their name, their description, and the price price we paid and sold them for.  We next created a separate table for product type just storing the type of each product in order to create more organization in the store. We then decided that creating an associative entity named “ProductLocation” between the “Products” and “ProductType” tables would help take all the information pertaining to products and associate that with their proper aisle in the store.
<br> <br>
The second thing we determined was important for a merchandiser store would be keeping track of the details related to purchasing and inventory mainly to keep track of what each store has.  A store like target needs to pay close attention to these details if they would like to have a properly stocked store.  We decided first to create a table called “TargetStore” so each store would have an ID and other key details like their address, phone number and product capacity as attributes.  We created two associate entities related to Target Store.  The first associative entity we created was “Inventory”.  This table helps relate the many products that can be in many target stores, and it relays helpful addiction information like the number of the product in stock and the max stock we have for a product.  This will help a business like Target have full ability to be aware of their inventory.
<br> <br>
The next associative entity we created was “PurchaseOrder”. This table connects the “TargetStore” with a table called “Shipment”.  “Shipment” gives details about the name of the shipment, the date it was shipped , and the expected delivery.  This table thus is useful to stores to understand when things will be arriving.  The  associative entity “PurchaseOrder” contains information about who made the order and their contact information and the orderDate in order to properly keep individuals accountable for the orders they make.  The “PurchaseOrder” is then connected to the table “OrderDetails” in a one to many relationship.  In addition to having  FKs from “PurchaseOrder” it also contains details about the orderQuantity and price of each product ordered.  Order details allows the company to have record of inventory purchasing expenses.
<br> <br>
The data model also contains information about who the shipments are sent from. The data model does this by having the table “Supplier” which contains the name and number of the supplier.  This table is then a foreign key in the tables “Shipment” and Warehouse”.  “Shipment” contains information about the shipment ID, name, date shipped , and when it is expected to arrive.  “Warehouse” contains information about the address of the warehouse and its phone number and capacity.
<br> <br>
Lastly, in order to run a store like target employees are necessary. We created an employee table in order to keep track of the employees at the stores as this is essential to run a business. 

## Data Model
<img width="630" alt="Screenshot 2023-03-30 at 8 30 32 AM" src="https://user-images.githubusercontent.com/82818412/228836415-b5004413-b7e9-4e43-9171-572034d411b4.png">

### Data Model Explanation <br>
The Target inventory data model starts with an instance of the TargetStore entity, which represents a single Target store. A TargetStore instance can have many Employees, but an Employee can only work at one TargetStore. When a TargetStore gets new inventory, it comes in a shipment. A TargetStore can have many shipments, and a shipment can be delivered to many TargetStores. This creates the associative entity PurchaseOrder, which contains information about the purchaser and when the order was purchased. Further, a Supplier facilitates these Shipments, and gathers the products ordered from their Warehouses. So, a Supplier can have many Shipments, but a Shipment may only have one supplier. Similarly, a Supplier can have many Warehouses, but a Warehouse can only belong to one Supplier. <br> <br>
Since inventory is being considered here, a Products entity exists. These Products can be stored in many TargetStore instances, and a TargetStore can have many Products. This creates an associative entity called Inventory, which keeps track of how many Products are currently in stock and the maximum number of Products that can be stored in that TargetStore. Similarly, Products can belong to many PurchaseOrder instances, and a PurchaseOrder can contain many Products, creating another associative entity called OrderDetails. This entity specifies the quantity of Products ordered and how much each Product costed. Lastly, Products can belong to many ProductTypes, and a ProductType can belong to many Products, creating the ProductLocation associative entity. This details where exactly that Product is in the TargetStore using the aisle name and aisle number specifications.

## Data Dictionary
Table: <b>Employee</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| employeeID | Unique sequential number identifying each employee | INT | | | PK |
| storeID | Unique sequential number identifying each store | INT | | | FK (ref. TargetStore) |
| empName | The employee's first and last name | VARCHAR | 45 |
| empPhone | Employee's primary phone number | VARCHAR | 45 | (999)999-9999 |
| jobTitle | Employee's primary work position | VARCHAR | 45 |

Table: <b>Inventory</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| inventoryID | Unique sequential number identifying each inventory | INT | | | PK |
| storeID | Unique sequential number identifying each store | INT | | | FK (ref. TargetStore) |
| productID | Unique sequential number identifying each product | INT | | | FK (ref. Products) |
| numInStock | Quantity of products in stock | INT |
| maxStock | Maximum quantity of products possible | INT | 

Table: <b>OrderDetails</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| orderDetailsID | Unique sequential number identifying each order detail entity | INT | | | PK |
| orderID | Unique sequential number identifying each order | INT | | | FK (ref. PurchaseOrder) |
| productID | Unique sequential number identifying each product | INT | | | FK (ref. Products) |
| orderQuantity | The number of products ordered | INT |
| priceEach | The price of each product ordered | DECIMAL(5,2) |
  
Table: <b>Products</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| productID | Unique sequential number identifying each product | INT | | | PK |
| productName | The product's name | VARCHAR | 45 |
| productDesc | The product's company name | VARCHAR | 45 |
| buyPrice | The price bought at wholesale | DECIMAL(5,2) |
| MSRP | The manufacturer's suggested retail price | DECIMAL(5,2) |
  
Table: <b>ProductLocation</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| prodLocID | Unique sequential number identifying each product location | INT | | | PK |
| productID | Unique sequential number identifying each product | INT | | | FK (ref. Products) |
| typeID | Unique sequential number identifying each product type | INT | | | FK (ref. ProductType) |
| aisleName | Name of the aisle where product is located | VARCHAR | 45 |
| aisleNum | Aisle number where product is located | INT |
  
Table: <b>ProductType</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| typeID | Unique sequential number identifying each product type | INT | | | PK |
| typeName | The product type's name | VARCHAR | 45 |

Table: <b>PurchaseOrder</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| orderID | Unique sequential number identifying each order | INT | | | PK |
| storeID | Unique sequential number identifying each store | INT | | | FK (ref. TargetStore) |
| shipmentID | Unique sequential number identifying each shipment | INT | | | FK (ref. Shipment) |
| purchaserName | The first and last name of the purchaser | VARCHAR | 45 |
| purchaserContact | The purchaser's primary phone number | VARCHAR | 45 | (999)999-9999 |
| orderDate | The date the purchase was ordered | DATETIME | | YYYY-MM-DD |

Table: <b>Shipment</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| shipmentID | Unique sequential number identifying each shipment | INT | | | PK |
| supplierID | Unique sequential number identifying each supplier | INT | | | FK (ref. Supplier) |
| shipmentName | The name of the shipment | VARCHAR | 45 |
| dateShipped | The date the order was shipped | DATETIME | | YYYY-MM-DD |
| expectedDelivery | The expected delivery date | DATETIME | | YYYY-MM-DD |
  
Table: <b>Supplier</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| supplierID | Unique sequential number identifying each supplier | INT | | | PK |
| supplierName | The name of the supplier | VARCHAR | 45 |
| supplierNumber | The supplier's primary phone number | VARCHAR | 45 | (999)999-9999 |

Table: <b>TargetStore</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| storeID | Unique sequential number identifying each store | INT  | | | PK |
| storeAddress | The physical address of the store | VARCHAR | 45 |
| storePhone | Store's primary phone number | VARCHAR | 45 | (999)999-9999 |
| storeProductCap | The store's product capacity | INT |

Table: <b>Warehouse</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| warehouseID | Unique sequential number identifying each warehouse | INT | | | PK |
| supplierID | Unique sequential number identifying each supplier | INT | | | FK (ref. Supplier) |
| warehouseAddress | The physical address of the warehouse | VARCHAR | 45 |
| warehousePhone | Warehouse's primary phone number | VARCHAR | 45 | (999)999-9999 |
| warehouseCap | The warehouse's product capacity | INT |

## Ten Queries
### TP_Q1
Return the name, date shipped, and expected delivery date of all shipments and the address of the warehouse that it came from. <br>
<b>Justification:</b> It’s important for an upper level manager to be able to see the details of all current shipments, including where they came from in case of errors in delivery or shipment details. Managers should have this information so they can track deliveries and time when they will be able to restock their inventory for a given Target store. <br> <br>
<img width="557" alt="Screenshot 2023-03-30 at 4 49 00 PM" src="https://user-images.githubusercontent.com/82818412/228961036-319a1f9f-b7bb-4710-b77b-c4d29568c95e.png"> <br>
<img width="495" alt="Screenshot 2023-03-30 at 4 51 17 PM" src="https://user-images.githubusercontent.com/82818412/228961479-30999b76-b916-4ac8-b77b-22a87d36e7cb.png">

### TP_Q2
Return the overall average MSRP of all products where the product type is Electronics. <br>
<b>Justification:</b> It’s important for a manager to know this information so they can see what the customer is paying on average for an electronic product. They could possibly compare this average price to that of competitors to see if they are pricing their products competitively or not. <br> <br>
<img width="572" alt="Screenshot 2023-03-30 at 4 49 21 PM" src="https://user-images.githubusercontent.com/82818412/228961089-17c37831-c162-4027-b871-02acda0e3a26.png"> <br>
<img width="215" alt="Screenshot 2023-03-30 at 4 51 40 PM" src="https://user-images.githubusercontent.com/82818412/228961569-2487d4ca-e79e-4c66-aac8-937d18f3dc55.png">

### TP_Q3
Return the name and phone number of employees who are managers or assistant managers, and return the address of the Target store at which they work. <br>
<b>Justification:</b> It’s important for an upper level manager to know who the managers and assistant managers are for each Target location and where exactly they work so that they can be contacted easily and correctly in case of emergency instead of accidentally contacting the wrong person. <br> <br>
<img width="482" alt="Screenshot 2023-03-30 at 4 49 35 PM" src="https://user-images.githubusercontent.com/82818412/228961134-afceefea-afec-4a4d-bd7a-bf641a076521.png"> <br>
<img width="317" alt="Screenshot 2023-03-30 at 4 52 01 PM" src="https://user-images.githubusercontent.com/82818412/228961631-3c3bf06e-5eec-4c3a-aca3-dc6b86a9c63d.png">

## Database Information
The name of the database is ns_21482_4.
