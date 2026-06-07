what is foreighn key in sap abap

In SAP ABAP, a Foreign Key is used in the Data Dictionary (DDIC) to create a relationship between two tables.

Simple Definition

A Foreign Key is a field in one table that refers to the primary key of another table.
It ensures data consistency and validation between tables.

Example (Simple)

Suppose we have two tables:

Customer Table

Customer_ID (Primary Key)

Name

City

Sales Order Table

Order_ID

Customer_ID

Amount

Here:

Customer_ID in Sales Order table is a Foreign Key

It refers to Customer_ID in Customer table

This means:

You cannot create a sales order for a customer that does not exist in the customer table.