Project explaination:

I worked on an SAP SD Pricing project where new materials created in SAP needed prices before they could be sold or invoiced.
When a new material was created, a custom ABAP report identified materials that required pricing and sent them to an external pricing system through SAP PI using proxies.
The external system calculated the prices and sent the price conditions back to SAP. If the price was effective immediately, it was updated directly into SAP condition tables. If the price was effective for a future date, it was stored in a custom staging table.
We had a scheduled background job that ran daily and moved eligible future-dated prices from the staging table to the SAP condition tables when their effective date arrived.
Once the prices were available in SAP, they were distributed to other SAP systems through qRFCs for invoicing and sales processes.
I was involved in developing custom ABAP reports, proxy interfaces, custom tables, OData services, and background jobs. I also worked on reports that allowed business users to monitor pricing data and track the status of materials sent for pricing.


If interviewer asks "What was your role?"
My role was mainly ABAP development. I developed and enhanced reports, worked on proxy interfaces, created OData services, developed custom tables and background jobs, performed testing, fixed defects, and supported production issues. I also interacted with functional consultants to understand pricing requirements and implement the required changes.


give me a flow chart of my project

Here's a simple **interview-friendly flow chart** you can explain during discussions:

```text
                +----------------------+
                | New Material Created |
                |      in SAP MM       |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Custom ABAP Report   |
                | Identify Materials   |
                | Requiring Pricing    |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | SAP Proxy Interface  |
                |  (via SAP PI/PO)     |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | External Pricing     |
                | System Calculates    |
                | Price Conditions     |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Price Response Sent  |
                | Back to SAP via PI   |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | ABAP Inbound Proxy   |
                | Receives Pricing     |
                +----------+-----------+
                           |
          +----------------+----------------+
          |                                 |
          v                                 v
 +--------------------+          +----------------------+
 | Effective Date =   |          | Future Effective     |
 | Current Date       |          | Date                 |
 +---------+----------+          +----------+-----------+
           |                                |
           v                                v
 +--------------------+          +----------------------+
 | Update SAP Pricing |          | Store in Custom      |
 | Condition Tables   |          | Staging Table        |
 | (Axxx / KONH/KONP) |          +----------+-----------+
 +---------+----------+                     |
           |                                |
           |                                v
           |                     +----------------------+
           |                     | Daily Background Job |
           |                     | Checks Effective Date|
           |                     +----------+-----------+
           |                                |
           |                                v
           |                     +----------------------+
           |                     | Move Eligible Prices |
           |                     | to SAP Condition     |
           |                     | Tables               |
           |                     +----------+-----------+
           |                                |
           +---------------+----------------+
                           |
                           v
                +----------------------+
                | Prices Available in  |
                | SAP SD Pricing       |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | qRFC Distribution    |
                | to Other SAP Systems |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Sales Orders &       |
                | Invoicing Processes  |
                +----------------------+
```

### Your Role in the Flow

You can explain:

1. Developed the **custom ABAP report** to identify materials requiring pricing.
2. Developed **outbound and inbound proxy programs** for SAP PI integration.
3. Created **custom staging tables** to store future-dated pricing records.
4. Developed the **background job program** to process future prices.
5. Created **OData services** and monitoring reports for business users.
6. Performed unit testing, defect fixing, and production support.
7. Coordinated with SD functional consultants to understand pricing requirements and implement changes.

### 30-Second Interview Explanation

> "The objective of the project was to automate material pricing. Whenever a new material was created in SAP, a custom ABAP report identified materials that required pricing and sent them to an external pricing system through SAP PI using proxies. The external system calculated the prices and sent them back to SAP. Immediate prices were updated directly into SAP condition tables, while future-dated prices were stored in a custom staging table. A daily background job moved eligible records to the condition tables when their effective date arrived. Finally, pricing data was distributed to other SAP systems through qRFCs for sales and invoicing processes. My role involved ABAP development of reports, proxy interfaces, custom tables, background jobs, OData services, testing, and production support."
