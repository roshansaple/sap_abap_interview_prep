I'm working with the Parts Pricing Product, which handles the pricing of <Company_Name> parts.

Here’s how it works:

When new parts are added to the SAP system, the information is sent to a Java web application via PI (Process Integration). In the Java application, pricing analysts set the prices for these parts. The updated prices are sent back to the SAP system through the PI system. These prices are saved in condition tables in SAP. We have custom reports in SAP that allow users to view this price data. Price files are also created in SAP. which user sents to Dealers. Additionally, the prices are sent to other systems using ODATA services.

(SAP writes data to proxy which PI receives & sent to java application) SAP --> Proxy --> PI --> Java web application.

what is current object or project you are working? Recently I worked on Creation of ODATA service to send prices to non sap System. Also, worked on creation of price reports