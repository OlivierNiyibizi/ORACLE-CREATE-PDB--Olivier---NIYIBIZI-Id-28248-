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
