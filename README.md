-- =============================================  
-- Author : Praveen Kumar
-- Create date : 22-11-2020
-- Description : To Create Database,Table and Sample Insert Query  
-- Latest  
-- Modifier : Shanu  
-- Modify date : 22-11-2020  
-- ============================================= 
--Script to create DB,Table and sample Insert data 

USE MASTER 
GO 
-- 1) Check for the Database Exists .If the database is exist then drop and create new DB 
IF EXISTS (SELECT [name] FROM sys.databases WHERE [name] = 'ShoppingDB' ) 
DROP DATABASE ShoppingDB 
GO 
 
CREATE DATABASE ShoppingDB 
GO 
 
USE ShoppingDB 
GO 
 
-- 1) //////////// ItemDetails table 

-- Create Table ItemDetails,This table will be used to store the details like Item Information  
 
IF EXISTS ( SELECT [name] FROM sys.tables WHERE [name] = 'ItemDetails' ) 
DROP TABLE ItemDetails 
GO 
 
CREATE TABLE ItemDetails 
( 
Item_ID int identity(1,1), 
Item_Name VARCHAR(100) NOT NULL, 
Item_Price int NOT NULL, 
Image_Name VARCHAR(100) NOT NULL, 
Description VARCHAR(100) NOT NULL, 
AddedBy VARCHAR(100) NOT NULL, 
CONSTRAINT [PK_ItemDetails] PRIMARY KEY CLUSTERED  
(  
[Item_ID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]  
) ON [PRIMARY]  

-- Insert the sample records to the ItemDetails Table

Insert into ItemDetails(Item_Name,Item_Price,Image_Name,Description,AddedBy) values('Milk',50,'CD.png','Daily use','Praveen') 
Insert into ItemDetails(Item_Name,Item_Price,Image_Name,Description,AddedBy) values('Honey',1400,'honey.png','Daily use','Praveen') 
Insert into ItemDetails(Item_Name,Item_Price,Image_Name,Description,AddedBy) values('Cake',1390,'cake.png','Birthday and celebration','Praveen') 
Insert into ItemDetails(Item_Name,Item_Price,Image_Name,Description,AddedBy) values('Egg',450,'egg.png','breakfast','Praveen') 
Insert into ItemDetails(Item_Name,Item_Price,Image_Name,Description,AddedBy) values('Choclate',1250,'choclate.png','dessert','Praveen') 
 

Application Changes
------------------------------------------
1. Download zip code-> unzip it and open in VS editor.
2. Please make connection string changes in appsetting.json in MVC WEB API application

 "ConnectionStrings": {
    "ShoppingDBConnection": "Server=your server name;Database=ShoppingDB;Trusted_Connection=True;MultipleActiveResultSets=true;"
  }

3. Run it from VS or press F5.
4. Once it runs in browser change URL. Append this line  for all data in list-        /api/ItemDetailsAPI/Details

5 For specific item kindly append this line-    /api/ItemDetailsAPI/Details/Egg

  


