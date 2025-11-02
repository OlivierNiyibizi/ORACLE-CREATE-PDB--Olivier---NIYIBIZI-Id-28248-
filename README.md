**ORACLE-CREATE-PDB--Olivier---NIYIBIZI-Id-28248-**
Student Name: Olivier NIYIBIZI 
Student ID: 28248 
Course: PL/SQL and Database Administration 
Instructor: — 
Date: October 2025 
1.	Introduction 
The aim of the task was focusing on how to work with Oracle 21c Multitenant 
Architecture, particularly the creation, management, and deletion of Pluggable Databases (PDBs) within a Container Database (CDB). 
The main objectives were: 
•	To understand and apply commands such as CREATE, ALTER and DROP 
PLUGGABLE DATABASE. 
•	To create a new pluggable database for classwork. 
•	To create and delete another pluggable database for practice. 
•	To verify the operations using Oracle Enterprise Manager (OEM). 
2.	Environment Setup 
• 	Operating System: Windows 11 Pro • 	Oracle Version: Oracle Database 21c • 	Tools Used: 
o 	SQL*Plus o 	SQL Developer o 	Oracle Enterprise Manager (OEM) 
NOTE: Before starting, the Oracle listener and database services were verified to be running using: services.msc 
3.	Task 1 – Creating the First Pluggable Database 
Objective: 
Create a new PDB for classwork named pdb_NIYIBIZI28248 and assign an admin user. 
SQL Script: 
CONNECT sys/your_password AS SYSDBA; 
 
CREATE PLUGGABLE DATABASE pdb_NIYIBIZI28248 
  ADMIN USER Niyibizi _plsqlauca_28248 IDENTIFIED BY oracle123   ROLES = (DBA) 
  CREATE_FILE_DEST = 'C:\ORACLE21C\ORADATA\ORCL\PDB_Niyibizi28248'; 
 
ALTER PLUGGABLE DATABASE pdb_Niyibizi28248 OPEN READ WRITE; 
ALTER PLUGGABLE DATABASE pdb_28248 SAVE STATE; SHOW PDBS; 
Explanation: 
•	CREATE PLUGGABLE DATABASE – creates a new PDB within the container. 
•	ADMIN USER – defines the administrator for this PDB. 
•	CREATE_FILE_DEST – specifies where Oracle will store the new database files. 
•	ALTER PLUGGABLE DATABASE ... OPEN READ WRITE – opens the PDB for use. 
•	SAVE STATE – ensures it reopens automatically on database restart. 
Result: 
The PDB was created successfully and appeared under SHOW PDBS as READ WRITE. 
<img width="916" height="240" alt="image" src="https://github.com/user-attachments/assets/2d3e6749-74d9-4a15-a82a-43823e5a93ce" />
4.	Task 2 – Creating and Deleting a Second PDB 
Objective: 
Create another pluggable database named NI_to_delete_pdb_28248 and then delete it to demonstrate full database lifecycle management. 
SQL Script (Creation): 
CREATE PLUGGABLE DATABASE Ni_to_delete_pdb_28248 
  ADMIN USER Niyibizi_plsqlauca_2828248 IDENTIFIED BY . 
  ROLES = (DBA) 
  CREATE_FILE_DEST = 'C:\ORACLE21C\ORADATA\ORCL\Ni_TO_DELETE_PDB_28248'; Open and Verify: 
ALTER PLUGGABLE DATABASE NI_to_delete_pdb_28248 OPEN READ WRITE; SHOW PDBS; 
This screenshot showing ol_to_delete_pdb_28248 in READ WRITE mode. 
<img width="858" height="355" alt="image" src="https://github.com/user-attachments/assets/e9f68160-2d94-45d9-a0e5-221ce98a6ff5" />
SQL Script (Deletion): 
ALTER PLUGGABLE DATABASE NI_to_delete_pdb_28248 CLOSE IMMEDIATE; 
DROP PLUGGABLE DATABASE NI_to_delete_pdb_28248 INCLUDING DATAFILES; SHOW PDBS; 
Explanation: 
•	The PDB must be closed before deletion. 
•	INCLUDING DATAFILES ensures that all associated files are removed from disk. 
•	SHOW PDBS confirms removal from the container database. 
Output after executing DROP command showing the PDB is no longer listed 
<img width="425" height="175" alt="image" src="https://github.com/user-attachments/assets/ae768d4d-7c9f-4b13-8814-ea09d62be729" />
<img width="965" height="111" alt="image" src="https://github.com/user-attachments/assets/395ef7f3-94ad-40c1-ac9a-8db39ebfad92" />
5.	Task 3 – Managing PDBs via Oracle Enterprise Manager (OEM) 
Objective: 
Verify the existence and status of PDBs using the graphical interface of Oracle Enterprise Manager. 
Procedure: 
1.	Accessed OEM at: 
2.	https://localhost:5500/em 
3.	Logged in using the SYS user in Container Database (CDB) mode. 
4.	Navigated to: 
Container Database → Pluggable Databases 
➢ Verified: pdb_ Niyibizi28248 appears as OPEN (READ WRITE). 
o	NI_to_delete_pdb_28248 no longer exists after deletion. 
o	OEM interface showing the active PDBs list. 
     
HERE THIS IS THE IMAGE BEFORE LOGIN 
<img width="1021" height="1020" alt="image" src="https://github.com/user-attachments/assets/efa50306-a379-4621-96a4-a2d8150d6b78" />
FINALY AFTER LOGIN INTO ORACLE ENTERPRISE MANAGER DATABASE 
EXPRESS 

6.	Error Handling and Troubleshooting 
So some common errors that was faced during the extraction of our task and the methods that was used to handle them.   
Error Code 	Description 	Solution Applied 
ORA-
65005 	Invalid or missing file path in 
FILE_NAME_CONVERT 	Replaced with CREATE_FILE_DEST for simplicity. 
ORA-
65011 	PDB does not exist 	Verified creation success before attempting ALTER. 
ORA-
00933 	SQL command not properly ended 	Executed one statement at a time; avoided chaining with semicolons. 
ORA-
12541 	Listener not running 	Started Oracle Listener service via services.msc. 
ORA-
65019 	PDB already open 	Checked current PDB state with SHOW PDBS before running ALTER. 
  
7.	Understanding PDB States 
	State 	Description 	Purpose 
The PDB is recognized by Oracle 
MOUNTED 	Used during startup or maintenance. 
but not yet opened. 
READ 	The PDB is open for reading data Used for reports or seed databases (like 
ONLY 	only. 	PDB$SEED). 
	State 	Description 	Purpose 
READ 	The PDB is fully open and 	Allows all SQL operations (SELECT, 
WRITE 	editable. 	INSERT, UPDATE, DELETE). 
Example Commands: 
ALTER PLUGGABLE DATABASE pdb_ Niyibizi28248 OPEN READ WRITE; 
ALTER PLUGGABLE DATABASE pdb_ Niyibizi28248 OPEN READ ONLY; 
ALTER PLUGGABLE DATABASE pdb_ Niyibizi28248 CLOSE IMMEDIATE; 
  
8.	Role of the ALTER Command 
ALTER is used to modify the state or structure of existing database objects. 
•	In this assignment, it was used to open, close, and save the state of PDBs: 
•	ALTER PLUGGABLE DATABASE pdb_Niyibizi28248 OPEN READ WRITE; 
•	ALTER PLUGGABLE DATABASE pdb_ Niyibizi28248 SAVE STATE; 
•	ALTER PLUGGABLE DATABASE NI_to_delete_pdb_28248 CLOSE IMMEDIATE; 
•	It changes behaviour, not structure — unlike CREATE (to make new) or DROP (to remove). 
  
9.	Conclusion 
This exercise provided hands-on experience with Oracle Multitenant Architecture, demonstrating: 
•	The process of creating, opening, saving, and deleting PDBs. 
•	The use of ALTER for managing database states. 
•	Troubleshooting common Oracle errors effectively. 
•	Confirming results using Oracle Enterprise Manager (OEM). 
Through this practical, I gained confidence in using Oracle SQL commands and better understanding the relationship between the CDB (Container Database) and PDBs (Pluggable Databases). 
  so here is the source for the used data 
   References 
1.	Oracle® Database 21c: Multitenant Administrator’s Guide Oracle Corporation, 2023. 
Available at: https://docs.oracle.com/en/database/oracle/oracledatabase/21/multi/index.html 
2.	Oracle® Database SQL Language Reference 21c Oracle Corporation, 2023. 
Documentation for CREATE PLUGGABLE DATABASE, ALTER PLUGGABLE DATABASE, and DROP PLUGGABLE DATABASE commands. 
https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/index.html 
3.	Oracle Learning Library (OLL) – Tutorials on Oracle Multitenant Architecture. 
https://apexapps.oracle.com/pls/apex/f?p=44785:141:0 
4.	Oracle LiveSQL – Interactive SQL practice environment. 
https://livesql.oracle.com 
5.	Stack Overflow Community Discussions – Troubleshooting ORA-65005, ORA-65011, and ORA-12541 errors. 
https://stackoverflow.com/questions/tagged/oracle 
6.	YouTube – Oracle DBA Channel 
“Creating and Managing Pluggable Databases in Oracle 21c.” Available at: 
https://www.youtube.com/results?search_query=oracle+21c+create+pluggable+database 
7.	Oracle Enterprise Manager Express User’s Guide Oracle Documentation for managing PDBs via OEM. https://docs.oracle.com/en/database/oracle/oracle-database/21/emxug/index.html 
  
Citation Format: 
Use APA or IEEE referencing depending on your instructor’s preference. The above list follows a simple academic format suitable for GitHub or report documentation. 
 
  
Prepared by: 
Olivier (Student ID: 28248) 
Oracle Database 21c – PL/SQL Practical 
