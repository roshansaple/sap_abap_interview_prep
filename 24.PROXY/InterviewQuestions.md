For a **3-year experienced SAP ABAP Developer**, proxy-related interview questions are usually asked in **SAP PI/PO, SAP XI, Enterprise Services, and integration scenarios**.

## Basic Proxy Questions

### 1. What is an SAP Proxy?

**Answer:**
An SAP Proxy is an ABAP object used for communication between SAP systems and external systems through SAP PI/PO or web services. It converts XML messages into ABAP structures and vice versa.

### 2. What are the types of Proxies?

**Answer:**

* **Outbound Proxy (Client Proxy)** – SAP sends data to another system.
* **Inbound Proxy (Server Proxy)** – SAP receives data from another system.

### 3. Why do we use Proxy instead of IDoc?

**Answer:**

* Real-time communication.
* XML-based messaging.
* Better performance.
* Supports synchronous and asynchronous communication.
* No need for ALE configuration.

---

## Intermediate Questions

### 4. Explain the Proxy Architecture.

**Flow:**
SAP ABAP System → Proxy Runtime → PI/PO → Target System

For inbound:
Target System → PI/PO → Proxy Runtime → SAP System

### 5. What is the difference between Inbound and Outbound Proxy?

| Inbound Proxy              | Outbound Proxy        |
| -------------------------- | --------------------- |
| Receives data              | Sends data            |
| Implements generated class | Calls generated class |
| Server side                | Client side           |

### 6. What are Synchronous and Asynchronous Proxies?

**Synchronous**

* Request and immediate response.
* User waits for response.

**Asynchronous**

* Only sends request.
* No immediate response.
* Used for bulk processing.

### 7. How do you create a Proxy?

**Steps:**

1. Create Message Type in PI/ESR.
2. Create Service Interface.
3. Generate Proxy in SAP.
4. Use transaction **SPROXY**.
5. Activate generated objects.
6. Write ABAP code.

---

## Technical Questions

### 8. Which Transaction Code is used for Proxy Generation?

**Answer:** `SPROXY`

### 9. What objects are generated when a Proxy is created?

**Answer:**

* Proxy Class
* DDIC Structures
* Message Types
* Methods

### 10. How do you execute an Outbound Proxy?

Example:

```abap
DATA: lo_proxy TYPE REF TO zco_customer_out,
      ls_data  TYPE zcustomer_msg.

CREATE OBJECT lo_proxy.

ls_data-kunnr = '1000'.
ls_data-name  = 'ABC'.

CALL METHOD lo_proxy->execute_asynchronous
  EXPORTING
    output = ls_data.
```

### 11. How do you handle exceptions in Proxy?

```abap
TRY.
    lo_proxy->execute_asynchronous(
      EXPORTING
        output = ls_data ).

  CATCH cx_ai_system_fault INTO DATA(lx_fault).

    MESSAGE lx_fault->get_text( ) TYPE 'E'.

ENDTRY.
```

---

## Monitoring & Troubleshooting Questions

### 12. How do you monitor Proxy messages?

| T-Code      | Purpose                |
| ----------- | ---------------------- |
| SPROXY      | Proxy generation       |
| SXMB_MONI   | Message Monitoring     |
| SXI_MONITOR | XI Message Monitoring  |
| SRT_MONI    | Web Service Monitoring |
| SMQ1        | Outbound Queue         |
| SMQ2        | Inbound Queue          |
| SM58        | Failed RFC Calls       |
| SLG1        | Application Logs       |
| ST22        | Dumps                  |
| SM21        | System Logs            |

### 13. What is SXMB_MONI used for?

**Answer:**
To monitor messages exchanged between SAP and PI/PO, check payloads, errors, status, and message flow.

### 14. If Proxy messages are stuck, how will you troubleshoot?

1. Check SXMB_MONI.
2. Check SMQ1/SMQ2 queues.
3. Check SM58 RFC errors.
4. Check ST22 dumps.
5. Check SLG1 logs.
6. Verify PI/PO mapping and communication channels.

---

## Scenario-Based Questions

### 15. You are sending customer data through a proxy, but the target system is not receiving it. What will you check?

**Answer:**

* SXMB_MONI message status.
* SMQ1 outbound queue.
* RFC destination (SM59).
* PI/PO communication channel.
* Error logs in SLG1.
* Proxy runtime configuration.

### 16. Difference between IDoc, RFC, and Proxy?

| RFC               | IDoc                 | Proxy        |
| ----------------- | -------------------- | ------------ |
| Function-based    | Document-based       | XML-based    |
| Real-time         | Usually asynchronous | Real-time    |
| SAP to SAP        | SAP/Non-SAP          | SAP/Non-SAP  |
| Limited structure | Fixed structure      | Flexible XML |

### 17. Have you worked on Proxy in your project?

**Sample Answer:**

> In my project, I developed an outbound asynchronous proxy to send customer master data from SAP S/4HANA to an external CRM system through PI/PO. I generated the proxy using SPROXY, populated the generated structures, called the proxy method, handled exceptions using CX_AI_SYSTEM_FAULT, and monitored messages through SXMB_MONI and SMQ1.

---

## Frequently Asked Advanced Questions

### 18. What is CX_AI_SYSTEM_FAULT?

Standard exception class used in proxy communication to capture runtime and system errors.

### 19. What is Logical Port in Proxy?

A configuration object that defines the endpoint URL and communication settings for web service proxies.

### 20. What is the difference between Enterprise Service and Proxy?

* Enterprise Service is the service definition.
* Proxy is the ABAP implementation generated from that service definition.

---

### Interview Tip for 3 Years Experience

Expect practical questions like:

* "How did you create a proxy?"
* "How do you monitor proxy messages?"
* "What happens when a message fails?"
* "How do you debug an inbound proxy?"
* "Difference between synchronous and asynchronous proxy?"
* "Which transactions did you use in your project?"

Being able to explain **SPROXY → Coding → Exception Handling → SXMB_MONI/SRT_MONI Monitoring → Error Resolution** with a real project example is often more important than memorizing definitions.
