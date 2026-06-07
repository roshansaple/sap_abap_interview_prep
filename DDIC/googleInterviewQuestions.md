Q1. What is Data Dictionary in SAP?
Ans: We use the ABAP Dictionary to create and manage data definitions (metadata). The ABAP Dictionary allows a central description of all the data used in the 
system without redundancies. New or modified information is automatically updated for all the system components. It ensures data integrity, data consistency and 
data security.

Q2. What is a Data Class?
Ans: The Data class determines in which tablespace the table is stored when it is created in the database.

Q3. What is a Size Category?
Ans: The Size category describes the probable space requirement of the table in the database.

Q4. How Many types of size categories and data classes are there?
APPL0 - Master data (data frequently accessed but rarely updated)
APPL1 - Transaction data (data that is changed frequently)
APPL2 - Organisational data (customizing data that is entered when system is configured and then rarely changed)

Q5. What are the features or important object types in the Data Dictionary?
Ans:
Tables
Tables are defined in the ABAP Dictionary independently of the database.
Views
Views are logical views of more than one table.
Types
The structure of a type can be defined globally in ABAP programs.
Lock objects
These objects are used to synchronize access to the same data by more than one user
Domains
Different fields having the same technical type can be combined in domains.
Q6. What are the Data Elements in Data Dictionary?
Ans: We use data elements to define the type of a table field, structure component or the row type of a table type.

Q7. What are foreign keys in Data Dictionary?
Ans: We use foreign keys to define relationships between tables in the ABAP Dictionary, create value checks for input fields and link several tables in a view or 
a lock object.

Q8. What are Search helps in Data Dictionary?
Ans: Search helps are objects that you can use to assign input help (F4 Help) to screen fields. You can do this by creating a search help in the ABAP Dictionary 
and attaching it to the corresponding screen field.

There are two types of search helps:

Elementary search helps.
Collective search helps.
Q9. What is the database utility?
Ans: The database utility allows you to edit (create, delete and adjust to changes to their definition in the ABAP Dictionary) database objects derived from objects 
of the ABAP Dictionary.

Q10. What are Pooled and Cluster Tables ?
Ans: Table pools and table clusters  are special table types in the ABAP Dictionary. The data from many different tables can be stored together in a table pool 
or table cluster. Tables assigned to a table pool or table cluster are indicated as pooled tables or cluster tables.

We must use a table pool or table cluster exclusively for storing internal control information (screen sequences, program parameters, temporary data, 
continuous texts such as documentation). Data of commercial relevance is stored in transparent tables.

Q11. What are the layers of SAP System in R/3?
Ans:

The external layer.
The ABAP/4 layer.
The database layer.
Q12. What is a Data Class?
Ans: The Data class determines in which table space the table is stored when it is created in the database.

There are the following data classes:

APPL0 (master data):
Data that is seldom changed.
APPL1 (transaction data):
Data that is frequently changed.
APPL2 (organizational data):
Customizing data that is defined when the system is installed and seldom changed.
Q13. What is a Size Category?
Ans: The Size category describes the probable space requirement of the table in the database.

Q14. How many types of size categories and data classes are there?
Ans: There are five size categories (0-4) and 11 data classes only three of which are appropriate for application tables:

APPL0- Master data (data frequently accessed but rarely updated).

APPL1- Transaction data (data that is changed frequently).

APPL2- Organizational data (customizing data that is entered when system is configured and then rarely changed).

The other two types are:

USR
USR1 – Intended for customer’s own developments.
Q15. What are control tables?
Ans: The values specified for the size category and data class are mapped to database-specific values via control tables.

Q16. What is the function of the transport system and workbench organizer?
Ans: The function of the transport system and the Workbench Organizer is to control any changes made to objects of the ABAP/4 Development Workbench and to transport 
these changes between different SAP systems.

Q17. Which objects are independent transport objects?
Ans: Domains, Data elements, Tables, Technical settings for tables, Secondary indexes for transparent tables, Structures, Views,Match code objects, Match code Ids, 
Lock objects.

Q18. What is a Development class?
Ans: Related objects from the ABAP/4 repository are assigned to the same development class.  This enables you to correct and
transport related objects as a unit.

Q19. In the ABAP/4 Dictionary Tables can be defined independent of the underlying database ?
Ans: Yes.

Q20. What is a Table attribute?
Ans: The table’s attributes determine who is responsible for maintaining a table and which types of access are allowed for the table.
The most important table attributes are:

Delivery class.

Table maintenance allowed.

Activation type.



Q21. What is the max. no. Of structures that can be included in a table or structure.
Ans: Nine.

Q22. What are two methods of modifying SAP standard tables?
Ans:

Append Structures and
Customizing Includes.
Q23. How many tables can an append structure be assigned?.
Ans: One.

Q24. Can we include customizing include or an append structure with Pooled or Cluster tables?
Ans: No.

Q25. What are the two ways for restricting the value range for a domain?
Ans: By specifying fixed values.

By stipulating a value table.

Q26. Structures can contain data only during the run time of a program (T/F)
Ans: True.

Q27. What are the aggregate objects in the Dictionary?
Ans: Views

Match Code.

Lock Object.

Q28. The data of a view is not physically stored, but derived from one or more tables (t/f)
Ans: True.

Q29. What is a Match Code?
Ans: Match code is a tool to help us to search for data records in the system. Match Codes are an efficient and user-friendly search aid where key of a record
is unknown.

Q30. What are the differences between a Database index and a match code?
Ans: Match code can contain fields from several tables whereas an index can contain fields from only one table.

Match code objects can be built on transparent tables and pooled and cluster tables.

Q31. What is the function of a Domain?
Ans: A domain describes the technical settings of a table field.

A domain defines a value range, which sets the permissible data values for the fields, which refers to this domain.

A single domain can be used as basis for any number of fields that are identical in structure.

Q32. Can you delete a domain, which is being used by data elements?
Ans: No.

Q33. What are conversion routines?

Non-standard conversions from display format to sap internal format and vice-versa are implemented with so called conversion
routines.

Q34. Can you delete data element, which is being used by table fields.
Ans: No.

Q35. Can you define a field without a data element?
Ans: Yes.  If you want to specify no data element and therefore no domain for a field, you can enter data type and field length and a short text directly in the 
table maintenance.

Q36. What are null values?
Ans: If the value of a field in a table is undefined or unknown, it is called a null value.

Q37. What is the difference between a structure and a table?
Ans: Structures are constructed the almost the same way as tables, the only difference using that no database table is generated from them.

Q38. What is a view?
Ans: A view is a logical view on one or more tables.  A view on one or more tables i.e., the data from a view is not actually physically
stored instead being derived from one or more tables.

Q39. How many types of Views are there?
Ans:

Database View

Help View

Projection View

Maintenance View

Q40. What are Lock objects?
Ans: When two users simultaneously attempt to access the same data record, this is synchronized by a lock mechanism.
Read Lock (Shared Locked)
The read lock allows other  transactions read access but not write access to the locked area of the table

Write Lock (exclusive lock)
The write lock allows other  transactions neither read nor write access to the locked area of the  table.

Enhanced write lock (exclusive lock without cumulating)
Write lock also  protects from further accesses from the same transaction.

Q41. What are the Data types of the ABAP/4 layer?
Ans: C: Character.

D: Date, format YYYYMMDD.

F: Floating-point number in DOUBLE PRECISION (8 bytes).

I: Integer.

N: Numerical character string of arbitrary length.

P: Amount of counter field (packed; implementation depends on h/w platform).

S: Time Stamp YYYYMMDDHHMMSS.

V: Character string of variable length, length is given in the first two bytes.

X: Hexadecimal (binary) storage.

Q42. What is customizing include?
Ans: Customers can enhance tables and structures of the standard system without having to modify the table and structure definitions. This means that these 
enhancements cannot be lost when upgrading. If a table or structure of the standard system is enhanced with customer fields using a customizing include, these 
customer fields are automatically inserted in the new delivered table or structure definition during an upgrade.

A customizing include is a structure that satisfies a special naming convention. The name of a customizing include begins with 'CI_' and the include is in the 
customer namespace.

Q43. What is Append Structure in Dictionary?
Ans: We use append structures for enhancements that are not included in the standard. This includes special developments, country versions and adding customer 
fields to any tables or structures.

An append structure is a structure that is assigned to exactly one table or structure. There can be more than one append structure for a table or structure.

Insert new fields in TAB
Define foreign keys for fields of TAB that already exist
Attach search helps to fields of TAB that already exist

Q44. What are the steps create a Table?
Ans: Creating Tables and Table Fields

Maintain the technical settings for the table.

Maintain (if necessary) the foreign key relationships of the table to other tables.

Create (if necessary) secondary indexes for the table.

For tables with the Delivery Class G or E, you must also maintain a customer namespace (key block of the table) for the table entries.

Maintain Customer Namespace on the Delivery and Maintenance tab.

Choose an enhancement category.

Q45. What is TABLE MAINTENANCE GENERATOR in Dictionary?
Ans: Table Maintenance Generator is a tool used to customize the tables created by end users and can be changed as required, such as making an entry to that table, 
deleting an entry etc.

Transaction Codes

SE54: Generate Table Maintenance Dialog

SE55: Table view maintenance DDIC call

SE56: Table view display DDIC call

SE57: Deletion of Table Maintenance

SM30: Maintenance Table Views:

Authorization Group : If the table needs to be maintained by only particular group of people, then the Authorization group needs to be filled otherwise fill it as NC. 
To maintain the authorization group refer to SU21.

Function group is the name to which the generated maintenance modules will belong to.

Generally Function Group name can be same as table name.

Maintenance screens:  Maintenance can be done in 2 ways

Maintenance and Overview both on one screen
Maintenance on one screen and Overview on another screen.
Modifications Available in Table Maintenance

Screen Alterations

Go To Environment -> Modification ->  Maintenance Screens

Table Maintenance Events

Q46. List of Events available in Table maintenance
Ans:

01         Before saving the data in the database

02         After saving the data in the database

03         Before deleting the data displayed

04         After deleting the data displayed

05         Creating a new entry

06         After completely performing the function 'Get original'

07         Before correcting the contents of a selected field

08         After correcting the contents of a selected field

09         After getting the original of an entry

10         After creating the header entries for the change task (E071)

11         After changing a key entry for the change task (E071K)

12         After changing the key entries for the change task (E071K)

13         Exit editing (exit main function module)

14         After lock/unlock in the main function module

15         Before retrieving deleted entries

16         After retrieving deleted entries

17         Do not use. Before print: Event 26

18         After checking whether the data has changed

19         After initializing global variables, field symbols, etc.

20         after input in date sub screen (time-dep. tab. /views)

21         Fill hidden fields

22         Go to long text maintenance for other languages

23         Before calling address maintenance screen

24         After restricting an entry (time-dep. tab./views)

25         Individual authorization checks

26         Before creating a list

27         After creation or copying a GUID (not a key field)

28         After entering a date restriction for time-dep. views

AA        Instead of the standard data read routine

AB        Instead of the standard database change routine

AC        Instead of the standard 'Get original' routine

AD       Instead of the standard RO field read routine

AE        Instead of standard positioning coding

AF        Instead of reading texts in other languages

AG       Instead of 'Get original' for texts in other languages

AH        Instead of DB change for texts in other languages

ST        GUI menu main program name

AI         Internal use only

Environment ->  Modification -> Events

Q47. What are the Types in Data Dictionary?

Ans: User-defined data types can be stored for all programs in the ABAP Dictionary.  User-defined types provide the same functionality as the local types that can 
be defined in ABAP programs with TYPES

There are three different type categories:

Data elements (elementary types and reference types).
Structures (structured types):
A structure consists of components that also have a type, that is they refer to a type.
Table types:
A table type describes the structure and functional attributes of an internal table. A special case is the ranges table types.

Q48. How do you Transporting Table entries from one server to another?
Ans: Go to transaction SE10. Click on Create.

Select Workbench request. (If the table is customizing table, then select customizing request)

Provide a short description to the request.

Now double-click on the request,

Go to change mode, and enter the following details:

Now click on the key button available under the name “Function” (As shown in the screenshot above). Following screen appears. Double-click on the first empty line.

Select the third radio button “Table contents specified by current key”.

Click on Save. A warning message would appear.

SAP issues a warning message when an application table is used. Following is the SAP help that would appear when we click on the message:

Ignore the warning message and click on Save.

Now transport this request to transport the data to any other system.

Q49. What are the Packages in SAP ?

Existing development classes are simply containers for development objects with a transport layer that determines how the objects will be transported. Packages 
extend the concept of development classes with the addition of new attributes: nesting, interfaces, visibility, and use accesses.
·  Nesting allows you to embed packages in other packages.
·  Visibility is a property of package elements.

Packages use interfaces and visibility to make their services known to other packages. All the visible elements in a package can, potentially, be sued by other 
packages. In contrast, invisible elements cannot be used by other packages as well.

Q50. What is Buffering and Buffering Types?
Ans: Full buffering:
The system loads all the re
Single-record buffering:
Only the records of a table that are really accessed are loaded into the buffer.
cords of the table into the buffer when one record of the table is accessed.
Generic buffering:
When a record of the table is accessed, all the records having this record in the generic key fields (part of the table key that is left-justified, identified by 
specifying a number of key fields) are loaded into the buffer.

Q51. What is Text Table in SAP?
Ans: You create text tables when you want to store explanatory text in several languages. It is not advisable to store such texts in your primary table. You can 
make a text table that must comprise the key of the primary table (for more information, see the example below). Every text table must also have an additional 
language key field (field of data type LANG).

Q51. What is Logging?
Ans: Using the logging flag you can define whether changes to the data records of a table are logged. If you switch on the logging, each change to an existing 
data record (with UPDATE, DELETE) by the user or application program is recorded in the database in a log table (DBTABPRT).

Q52. What are Indexes in Data Dictionary?
Ans: We use indexes to speed up searching a table for data records that satisfy certain search criteria.
The primary index contains the key fields of the table and a pointer to the non-key fields of the table. The system creates the primary index automatically when 
the table is created in the database.

You can also create further indexes on a table in the ABAP Dictionary. These are called secondary indexes. This is necessary if the table is frequently accessed in 
a way that does not take advantage of the sorting of the primary index for the access.

