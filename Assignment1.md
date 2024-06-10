
Assignment 1 
Case study: Corporate HRMS System
Define the Scope and Objectives 

Scope: 
* A corporate HRMS System where employees can log in, view account details, Change the database, Apply Leave. 

Objectives: 
* Identify potential threats. 
* Assess the impact and likelihood of threats. 
* Develop mitigation strategies. 

Entities: 
* Employee (External Entity) 
* Web Server (Process) 
* Database Server (Data Store) 
* Authorization Server (Internal Entity)




*  Click on Create A Model
    ![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/bcbc41c8-574a-4092-ae48-10565802d9bf)

* Now the resultant canvas will be:
*  Demo of Simple Web Application
  ![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/0e8c0bdd-10ae-4f14-8f9c-bac3501361c3)

* Identify and Analyse Threats: Navigate to ‘View’ then click ‘analysis view’
 ![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/f54fedbd-7d16-4939-8032-def08d582413)

The Data flow sequence will be.
Employee -> Web Application (Submit credentials) 
* Data Flow Type: HTTP 
* Description: Employee submits login credentials to the web application.

Web Application -> Authorization Server (Verify credentials) 
* Data Flow Type: HTTPS 
* Description: The web application sends the credentials to the authorization server for verification.

Authorization Server -> Web Application (Send account details) 
* Data Flow Type: HTTPS
* Description: The authorization server sends the account details back to the web application. 

Web Application -> Employee (Display account details) 
* Data Flow Type: HTTP 
* Description: The web application displays the account details to the customer. 

Employee -> Web Application (Request Applying Leave) 
* Data Flow Type: HTTPS 
* Description: The employee requests a applying leave through the web application.

Web Server -> Authorization Server (Update Leave Account) 
* Data Flow Type: HTTPS 
* Description: The web server sends the leave request to the authorization server to update the leaves. 

Web Server -> SQL Database Server (Initiate request for Update) 
* Data Flow Type: HTTPS 
* Description: The web server initiates the request with the database server 

SQL Database Server -> Web Server (Confirm Update) 
* Data Flow Type: HTTPS 
* Description: The SQL Database Server confirms the update and sends the confirmation back to the web server. 

Web Server -> Employee (Display HRMS System) 
* Data Flow Type: HTTPS 
* Description: The web server displays the leave status to the employee in HRMS System

  ![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/081f887c-e0bc-45a4-bd42-74b5788d3db8)

* Analysis View

  ![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/2e5f27f1-2031-4e9f-8262-c93d5a086113)

* We can choose a specific threat and check its properties

  ![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/eb0eaf17-0c5b-43e1-bec9-385d179ae960)

* A report is generated which lists all the threats in our model

  ![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/7c79a6c6-73a0-4ee3-97e8-7afbf5b4d2e4)

