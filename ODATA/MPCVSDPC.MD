what is the difference between dpc class and mpc class in odata in sap abap

In SAP ABAP OData (when you create a service using SAP Gateway), two important classes are generated:

MPC (Model Provider Class)

DPC (Data Provider Class)

Let’s understand the difference clearly and in an interview-friendly way 👇

1️⃣ MPC – Model Provider Class

Full Form: Model Provider Class
Purpose: Defines the structure of the OData service.

What it does:

Defines Entity Types

Defines Entity Sets

Defines Properties (fields)

Defines Associations

Defines Metadata (EDMX)

👉 In simple words:
MPC defines WHAT data looks like. (Structure / Blueprint)

Important Method:

DEFINE – Used to define entities and their properties.

Example:

If you create an OData service for Sales Orders:

Entity Type: SalesOrder

Properties: Vbeln, Erdat, Netwr

All this structure is defined in MPC.

2️⃣ DPC – Data Provider Class

Full Form: Data Provider Class
Purpose: Handles the actual data fetching and processing.

What it does:

Fetches data from database tables

Handles CRUD operations:

GET (Read)

POST (Create)

PUT (Update)

DELETE (Delete)

👉 In simple words:
DPC defines HOW data is fetched and manipulated. (Logic / Implementation)

Important Methods:

GET_ENTITYSET → Fetch multiple records

GET_ENTITY → Fetch single record

CREATE_ENTITY

UPDATE_ENTITY

DELETE_ENTITY

You usually redefine these methods in:

DPC_EXT (Extension class)

🔥 Simple Difference Table (Interview Ready)
MPC	DPC
Defines data model	Provides data
Structure only	Logic + database operations
Blueprint	Implementation
Uses DEFINE method	Uses GET_ENTITYSET, etc.
No database logic	Contains SELECT queries
🎯 Very Simple Way to Explain in Interview

You can say:

“MPC class defines the metadata and structure of the OData service like entity types and properties, while DPC class contains the business logic to fetch and manipulate data from backend tables.”