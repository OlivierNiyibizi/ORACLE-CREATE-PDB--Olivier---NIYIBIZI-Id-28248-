# ORACLE-CREATE-PDB--Olivier---NIYIBIZI-Id-28248-
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


