Oracle PDB Administration Tasks
Student: ASDODJI Le Sage
Student ID: 27232
Course: PL/SQL AUCA
Date: October 2025

Task 1: Create a New Pluggable Database (PDB)
PDB Name: as_pdb_27232
Admin User: pdbadmin
Class User: asdodji_plsqlauca_27232
Password: (simple password chosen during setup)
•	SQL Commands:

CREATE PLUGGABLE DATABASE as_pdb_27232
  ADMIN USER pdbadmin IDENTIFIED BY "Welcome1!"
  ROLES = (DBA);

ALTER PLUGGABLE DATABASE as_pdb_27232 OPEN;
ALTER PLUGGABLE DATABASE as_pdb_27232 SAVE STATE;

ALTER SESSION SET CONTAINER = as_pdb_27232;
CREATE USER asdodji_plsqlauca_27232 IDENTIFIED BY "Class#123";
GRANT CREATE SESSION, CREATE TABLE, CREATE VIEW, CREATE SEQUENCE,
      CREATE PROCEDURE, CREATE TRIGGER, UNLIMITED TABLESPACE TO asdodji_plsqlauca_27232;

Screenshot Evidence:
✅ SHOW PDBS; showing AS_PDB_27232 in READ WRITE
✅ SHOW CON_NAME; inside AS_PDB_27232
✅ SELECT USER FROM DUAL; showing ASDODJI_PLSQLAUCA_27232
Task 2: Create and Delete a PDB
•	Steps:

CREATE PLUGGABLE DATABASE as_to_delete_pdb_27232
  ADMIN USER pdbadmin IDENTIFIED BY "Welcome1!";
ALTER PLUGGABLE DATABASE as_to_delete_pdb_27232 OPEN;

ALTER PLUGGABLE DATABASE as_to_delete_pdb_27232 CLOSE IMMEDIATE;
DROP PLUGGABLE DATABASE as_to_delete_pdb_27232 INCLUDING DATAFILES;

Screenshot Evidence:
✅ Before deletion (PDB listed)
✅ After deletion (PDB removed)
Task 3: Oracle Enterprise Manager (EM Express)

ALTER SESSION SET CONTAINER = CDB$ROOT;
BEGIN
  DBMS_XDB_CONFIG.SETHTTPSPORT(5500);
END;
/

Accessed via: https://localhost:5500/em
Logged in as: asdodji_plsqlauca_27232
Container: AS_PDB_27232

Screenshot Evidence:
✅ EM Express Dashboard showing username and container name.
Troubleshooting Notes
Issue	Error Message	Solution
Missing db_create_file_dest	ORA-65016 / ORA-01261	Created folder C:\oracle\oradata\XE, set parameter, and restarted DB.
PDB didn’t open automatically	N/A	Used ALTER PLUGGABLE DATABASE as_pdb_27232 SAVE STATE;
EM Express not loading	Port issue	Re-ran DBMS_XDB_CONFIG.SETHTTPSPORT(5500); and allowed port through firewall.
Screenshots Summary
1. PDB Creation (as_pdb_27232)
2. Session inside PDB
3. PDB Creation & Deletion (as_to_delete_pdb_27232)
4. OEM Dashboard (with username visible)
Submission

Repository: GitHub Public Repo
Files included:
- README.md (this document)
- Screenshots folder /screenshots/
- Optional: SQL script /scripts/pdb_tasks.sql
Link sent to instructor via email before 11:59 PM on class day.

•	✅ Status: Completed Successfully
# oracle_pdb_assignment
