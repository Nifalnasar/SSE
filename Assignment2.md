
DVTA Setup - DVTA - Part 1 - Setup (parsiya.net)
Use CFF Framework to analyse custom DVTA.exe created above.

To Start with the DVTA, first we need to setup SQL Server 2008

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/3ff90eca-b53b-4216-9afd-3101d044a756)

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/70ece77c-2fdd-4ddf-a81d-affb1b43db3d)

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/4e12d5fa-602a-4976-93c4-7fbb176499ee)

We have to setup support files

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/9f37a643-167d-44f2-a3cd-dd40b9abf2b5)

To Add Database Engine 

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/65733fef-e197-4ef7-aa59-bdbb34e5fa97)

Now we have to configure server 

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/dc82cbaa-14df-43fe-b58c-a9ffff4bd9e7)

Add a password as a configuration of Server 

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/dc3ee7ad-fe3b-4734-ad7a-0ae61ababa31)

Password Should be – P@ssw0rd
•	We need to add users SQL Server Administrator

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/3b5e7d06-91c8-42a2-a3fa-7db47b00fb9b)

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/09df4f28-244c-4b40-9e27-738df94786bf)

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/1f6b2b46-234e-464d-b9a5-8666dd05d01d)

* We need to start SQL Server 2008

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/18a764fa-7382-4d3d-a35f-af0570afad0a)

Create New Database

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/4b562eea-116c-411f-b71a-1306b8036753)

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/7154d435-5f41-4556-a5e0-ef71bde7f470)

*	Restart SQL Server 

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/69280707-a7d2-42e5-a8e8-26f59bfe62fd)

*	Start a Filezila Server in your computer 
*	Going to Admin Panel 

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/d36a60b9-7697-413c-ba18-be8a9164b1a6)

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/2ab27979-cce8-47ef-aeeb-8c633e6cc230)

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/263c954f-c150-432f-89d3-5de7eeb9122a)

1)	Identify the Application architecture, languages and frameworks used?
*	Upon opening the dvta.exe in CFF-explorer, we can identify the following information
*	Architecture – 32 bit & 2 tier [Since it communicates with the database.]
*	Languages used - .NET Assembly
*	Frameworks - .NET framework

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/f1b8073c-40ec-4d1d-9b32-987efd68e6f9)

2. Decompile and try to retrieve the source code of the application? Also, check if any hardcoded sensitive information is found? 
*	By decompiling the application using DNSpy or MS Visual studio tools, we can see the source code of the application.

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/5e2244d5-96f9-48f9-a014-06881ea1ea81)

3) Sniff the traffic between client and server. Identify which protocol is being used for communication?
*	With Wireshark we can sniff the client and server 
*	Next inspect the contents of the packets to determine whether the app is using TCP/UDP protocol for communication.
*	In the packet inspection window, we can see that the protocol used by the  dvta is TCP protocol.

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/4c248f57-3e1e-4bcf-82f4-e725e7108f83)

4) Identify if unencrypted communication is happening between client and server?
*	In this case we can use either ECHIMIRAGE / wireshark. We have used Echomirage here. 
*	From the output we can see that when we login to DVTA , the data is sent as plaintext format to the database. 

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/b255d773-a460-4247-9a3d-d5a2fc766a05)

5) Capture and analyse the communication using proxy tools (eg: Burpsuite, Echo mirage). 
*	From the below screenshot, we can understand that using wireshark we’re able to capture & analyse the requests that are being sent to the database and to the server

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/901f11c1-05d7-44fd-a3aa-46b89a7375e2)

6) Analyse the application workflow and observe which all files/folders are being used by the application using Process Monitor
*	With the help of a tool called Process-Monitor can see that there are several files & folders being retrieved when running the DVTA.exe.

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/33db3bdc-48d4-4502-9208-07d43a2937bc)

7) Exploit DLL Hijacking vulnerability (You can use a simple legitimate “Hello World” printing dll.
*	In order to hijack a DLL, we need to find which DLL’s that are being loaded when DVTA.exe runs is not found.
*	For this we need to open Procmon & set the following 3 filters .

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/7aaeacb5-0810-42f9-806c-81ae99a27fe1)

*	We will Start Process Monitor Filter 

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/3b0067ff-b807-43c2-9b46-028e74fd3ad6)

*	When click DVTA.exe automatically Hello world pop up will appear with opening of DVTA Login Page 

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/82cd7d5c-3a26-4ad3-b47a-b0ab67d091af)

*	As we can see now when the DVTA.exe runs, it loads our calc.dll along with the application. Thus we have hijacked the DLL. 

8) Check for sensitive information in the configuration files of the thick client application? 
*	In the folder of DVTA, we have few files . One of the files is App.config. It contains the following sensitive information.
*	We have to open Visual Studio and analyse DVTA.exe.config.

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/db2d0298-44be-44e0-8f4d-2195f3cdfa12)

9) Identify sensitive information found in memory?

*	From the source code which we got from DNSpy, we got to know that it stores the username & password in HKCU/dvta registry file.
*	We can visit the registry to find the sensitive information which is stored in the memory.
*	We have to open registry editor to analyse dvta username and password.  

![image](https://github.com/KVNuhman/Secure-Systems-Engineering/assets/46161259/b8239194-d5ab-4ce7-9689-71fa1257fe10)

