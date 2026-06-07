1️⃣ What is Code Pushdown? Explain with example.
✅ Answer:

Code pushdown means moving data-intensive operations like joins, filtering, and aggregation from ABAP application server to the database layer (SAP HANA).

❌ Old Way:
SELECT * FROM vbap INTO TABLE it_vbap.

LOOP AT it_vbap INTO wa_vbap.
IF wa_vbap-netwr > 10000.
APPEND wa_vbap TO it_final.
ENDIF.
ENDLOOP.
✅ Pushdown Way:
SELECT * FROM vbap
INTO TABLE it_vbap
WHERE netwr > 10000.

🔥 2️⃣ Why are CDS Views faster?
✅ Answer:

CDS views are faster because:

They execute directly in database

Use in-memory processing

Use columnar storage

Follow code pushdown principle

🔥 3️⃣ Is CDS always faster than Open SQL?
✅ Answer:

No.
If both are simple queries returning the same data, performance difference is minimal.
CDS is more beneficial for complex joins, aggregations, and reusable data models.

🔥 4️⃣ What happens internally when CDS is activated?
✅ Answer:

When activated:

A SQL View is created in the database

Stored in HANA

Database optimizer prepares execution plan

Example:

@AbapCatalog.sqlViewName: 'ZSALES'
define view Z_CDS
as select from vbak
{
vbeln,
erdat
}

This creates a database SQL view.

🔥 5️⃣ Difference Between CDS and SE11 View?
SE11 View	CDS View
Basic SQL	Advanced SQL
No annotations	Supports annotations
No associations	Supports associations
Limited features	Works with OData & Fiori
🔥 6️⃣ What is Association in CDS?
✅ Answer:

Association defines relationship between two tables and supports lazy loading.

Example:

define view Z_CDS
as select from vbak
association [0..*] to vbap as _item
on vbak.vbeln = _item.vbeln
{
vbak.vbeln,
_item
}
🔥 7️⃣ What is difference between CDS and AMDP?
CDS:

SQL based

Declarative

Used for modeling

AMDP:

Uses SQLScript

Used for complex logic

Written in database procedure

🔥 8️⃣ What are Performance Best Practices in HANA?
✅ Answer:

Avoid SELECT *

Use proper WHERE conditions

Select only required fields

Avoid nested loops

Use CDS/AMDP for complex logic

Use indexes properly

🔥 9️⃣ How do you check performance of CDS?
✅ Answer:

SQL Trace (ST05)

Runtime Analysis (SAT)

HANA Studio PlanViz

🔥 1️⃣0️⃣ Real Scenario Question

👉 You have 1 million sales records.
You need total net value per customer.

How will you optimize?

❌ Wrong:

Fetch all data and calculate in ABAP.

✅ Correct:

Use CDS with aggregation:

define view Z_TOTAL
as select from vbap
{
kunnr,
sum(netwr) as total_value
}
group by kunnr

This performs aggregation at database level.

🎯 Most Important Interview Line

You can always say:

In HANA environment, we should move heavy processing to database layer to utilize in-memory capabilities and reduce data transfer.

This sentence sounds very professional.

Since you want to improve speaking skills also,
Next step I suggest:

I will ask you one question like an interviewer,
You answer in English,
Then I correct your answer.

Ready? 😊