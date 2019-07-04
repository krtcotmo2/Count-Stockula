# [Count-Stockula](https://count-stockula.herokuapp.com/)
![alt text](https://img.shields.io/badge/uses-Node-brightgreen.svg) ![alt text](https://img.shields.io/badge/uses-Mongoose-brightgreen.svg) ![alt text](https://img.shields.io/badge/uses-Express-brightgreen.svg) ![alt text](https://img.shields.io/badge/uses-Axios-brightgreen.svg) ![alt text](https://img.shields.io/badge/uses-Nodemailer-brightgreen.svg) ![alt text](https://img.shields.io/badge/uses-Twilio-brightgreen.svg) ![alt text](https://img.shields.io/badge/uses-bcrypt-brightgreen.svg) ![alt text](https://img.shields.io/badge/uses-Json_Web_Token-brightgreen.svg) 

![alt text](https://img.shields.io/badge/uses-React-blue.svg)  ![alt text](https://img.shields.io/badge/uses-Materialize-blue.svg) ![alt text](https://img.shields.io/badge/uses-pdfMake-blue.svg) ![alt text](https://img.shields.io/badge/uses-ReactBarcodeReader-blue.svg) 

### Problem

Small business experience difficulties keeping up with inventory levels. The POS systems can keep track of what is sold but puts the onus of inventory level on the manger. This can be a manual process.

### How we built it (this was a team effort)
The database used in this project is MongoDB. Before you can run a downloaded copy you will need to create the collections using the seedDB.js file in the scripts folder at the root level.
```
cd scripts 
node seedDB.js
```

While having a hand held scanner is a definite advantage (we used a Motorola DS6878 ), the application can be run without the scanner. Instead of scanning upc’s the user will need to click on the text in the red fields and then enter in the upc numbers manually. The events for scanning an item are handled through the ReactBarCodeReader package.

Materialize components and css help shape the look and feel while React is used for the frontend scaffolding and interactivity. The application is intended to be run off a desktop while scanning but the responsive design will resize and reformat for a mobile device. The mobile device view was intended for the inventory manager to use at any location to view inventory levels for multiple stores. 

Other packages were used for secondary functions within the application. PDFMake is used for creating the receipts from the actual sales process and could easily also generate reports for sales data across stores. Nodemailer sends a copy of the receipt to a specified address. Twillio allows the system to text the manager when inventory levels are low.

### Solution
Count Stockula links the scanning of objects into an inventory system that will inform and keep the owners connected to inventory, even across multiple stores. Users login the system using an encrypted username and password. Each time scanned into the application it will reduce the inventory from the specific store. The user can manually enter in a upc, use a quick click dashboard to add common items or items that traditionally have upc code, such as produce. The user closes out the order by entering in as email address and a pdf receipt is generated and mailed out. 

### Inventory Levels

Each item in the store has a “critical threshold” level that determines when an item needs to be restocked. Count Stockula will send a text message out to the inventory manager whenever an item’s current inventory level reaches this critical threshold. The system will also send out a text message when the inventory level of any item reaches 0.

In addition to text messages, the inventory manager can open up a list that shows all inventory levels for items across single or multiple stores. The manager can look at items that are out of stock, at or below critical level or all products in the system. This list is available outside through the web interface and report inventory levels in real time.

### Restocking Inventory
The user can scan in a upc number. If the item is not in the store’s inventory, the user is prevented from adding stock until it is added. Users can also add inventory to non scannable items by manually entering in a upc number. The user is shown the item description and can then enter in a number by which to increase inventory.

### Adding Inventory

The user can scan in a upc number. If the item exists in the store’s inventory, the user is prevented from duplicating the upc. Users can also add inventory to non scannable items by manually entering in a upc number. The upc is prepopulated and the user can add in the item description.
