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
Our group created a data model for the inventory management system of a Target store. For each Target store, we wanted to be able to track the current inventory in stock and the information about the product, the product description, the product type, and the location of each product within each store. In addition, our data model shows the process of each Target store restocking their inventory tracking the information on each purchase order, the order details, the shipment, the supplier of each product, and the distribution center it ships from. 

## Data Model
<img width="643" alt="Screenshot 2023-03-27 at 4 01 33 PM" src="https://user-images.githubusercontent.com/82818412/228053365-1a7b0abc-60f4-4033-8270-cee07b2c1290.png">

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
| productDesc | The product's description | VARCHAR | 45 |
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
| orderDate | The date the purchase was ordered | DATETIME | | YYYY/MM/DD |

Table: <b>Shipment</b>
| Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| shipmentID | Unique sequential number identifying each shipment | INT | | | PK |
| supplierID | Unique sequential number identifying each supplier | INT | | | FK (ref. Supplier) |
| shipmentName | The name of the shipment | VARCHAR | 45 |
| dateShipped | The date the order was shipped | DATETIME | | YYYY/MM/DD |
| expectedDelivery | The expected delivery date | DATETIME | | YYYY/MM/DD |
  
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

## Database Information
The name of the database is ns_21482_4.
