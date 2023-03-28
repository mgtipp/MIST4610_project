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

## Data Model
<img width="643" alt="Screenshot 2023-03-27 at 4 01 33 PM" src="https://user-images.githubusercontent.com/82818412/228053365-1a7b0abc-60f4-4033-8270-cee07b2c1290.png">

## Data Dictionary
Table: <b>Employee</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| employeeID | Unique sequential number identifying each employee | INT | | | PK |
| storeID | Unique sequential number identifying each store | INT | | | FK (ref. TargetStore) |
| empName | The employee's first and last name | Text | 45 |
| empPhone | Employee's primary phone number | Text | 45 | (999)999-9999 |
| jobTitle | Employee's primary work position | Text | 45 |

Table: <b>Inventory</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| inventoryID | Unique sequential number identifying each inventory | INT | | | PK |
| storeID | Unique sequential number identifying each store | INT | | | FK (ref. TargetStore) |
| productID | Unique sequential number identifying each product | INT | | | FK (ref. Products) |
| numInStock | Quantity of products in stock | INT |
| maxStock | Maximum quantity of products possible | INT | 

Table: <b>OrderDetails</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| orderDetailsID | Unique sequential number identifying each order detail entity | INT | | | PK |
| orderID | Unique sequential number identifying each order | INT | | | FK (ref. PurchaseOrder) |
| productID | Unique sequential number identifying each product | INT | | | FK (ref. Products) |
| orderQuantity | The number of products ordered | INT |
| priceEach | The price of each product ordered | DECIMAL(5,2) |
  
Table: <b>Products</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| productID | Unique sequential number identifying each product | INT | | | PK |
| productName | The product's name | Text | 45 |
| productDesc | The product's description | Text | 45 |
| buyPrice | The price bought at wholesale | DECIMAL(5,2) |
| MSRP | The manufacturer's suggested retail price | DECIMAL(5,2) |
  
Table: <b>ProductLocation</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| prodLocID | Unique sequential number identifying each product location | INT | | | PK |
| productID | Unique sequential number identifying each product | INT | | | FK (ref. Products) |
| typeID | Unique sequential number identifying each product type | INT | | | FK (ref. ProductType) |
| aisleName | Name of the aisle where product is located | Text | 45 |
| aisleNum | Aisle number where product is located | INT |
  
Table: <b>ProductType</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| typeID | Unique sequential number identifying each product type | INT | | | PK |
| typeName | The product type's name | Text | 45 |

Table: <b>PurchaseOrder</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| orderID | Unique sequential number identifying each order | INT | | | PK |
| storeID | Unique sequential number identifying each store | INT | | | FK (ref. TargetStore) |
| shipmentID | Unique sequential number identifying each shipment | INT | | | FK (ref. Shipment) |
| purchaserName | The first and last name of the purchaser | Text | 45 |
| purchaserContact | The purchaser's primary phone number | Text | 45 | (999)999-9999 |
| orderDate | The date the purchase was ordered | DATETIME | | YYYY/MM/DD |

Table: <b>Shipment</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| shipmentID | Unique sequential number identifying each shipment | INT | | | PK |
| supplierID | Unique sequential number identifying each supplier | INT | | | FK (ref. Supplier) |
| shipmentName | The name of the shipment | Text | 45 |
| dateShipped | The date the order was shipped | DATETIME | | YYYY/MM/DD |
| expectedDelivery | The expected delivery date | DATETIME | | YYYY/MM/DD |
  
Table: <b>Supplier</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| supplierID | Unique sequential number identifying each supplier | INT | | | PK |
| supplierName | The name of the supplier | Text | 45 |
| supplierNumber | The supplier's primary phone number | Text | 45 | (999)999-9999 |

Table: <b>TargetStore</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| storeID | Unique sequential number identifying each store | INT  | | | PK |
| storeAddress | The physical address of the store | Text | 45 |
| storePhone | Store's primary phone number | Text | 45 | (999)999-9999 |
| storeProductCap | The store's product capacity | INT |

Table: <b>Warehouse</b>
| Column Name  | Description   | Data Type     | Size          | Format | Key |
| ------------ | ------------- | ------------- | ------------- | ------ | --- |
| warehouseID | Unique sequential number identifying each warehouse | INT | | | PK |
| supplierID | Unique sequential number identifying each supplier | INT | | | FK (ref. Supplier) |
| warehouseAddress | The physical address of the warehouse | Text | 45 |
| warehousePhone | Warehouse's primary phone number | Text | 45 | (999)999-9999 |
| warehouseCap | The warehouse's product capacity | INT |

## Ten Queries

## Database Information
The name of the database is ns_21482_4.
