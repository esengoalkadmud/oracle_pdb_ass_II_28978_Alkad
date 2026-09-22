# Oracle PDB Assignment II

**Student:** MUDAHINYUKA ESENGO Alkad  
**Student ID:** 28978  
**Course:** Database Development with PL/SQL (INSY 8311)  
**Instructor:** Eric Maniraguha  

## Overview

This assignment demonstrates practical understanding of Oracle Multitenant Architecture by creating, managing, and deleting Pluggable Databases (PDBs), creating users inside a PDB, and accessing the database management environment.

## Oracle Environment

- **Oracle Database:** 26ai Free Edition
- **Tool:** Oracle SQL Developer 26.2.0


## Task 1: Create a New Pluggable Database

Created a new PDB named **`Al_pdb_28978`** from the seed PDB, opened it in READ WRITE mode, saved its state, and created an administrative user inside it.

- **PDB Name:** `Al_pdb_28978`
- **Username inside PDB:** `Alkad_plsqlaua_28978`
- **Commands used:**

```sql
CREATE PLUGGABLE DATABASE Al_pdb_28978
ADMIN USER Alkad_plsqlaua_28978 IDENTIFIED BY alkad1312
FILE_NAME_CONVERT = ('C:\ORACLE26\ORADATA\FREE\PDBSEED\',
                     'C:\ORACLE26\ORADATA\FREE\AL_PDB_28978\');

ALTER PLUGGABLE DATABASE Al_pdb_28978 OPEN READ WRITE;
ALTER PLUGGABLE DATABASE Al_pdb_28978 SAVE STATE;
```
Evidence: see ```screenshots/pdb_creation/```

## Task 2: Create and Delete a Temporary PDB

sql

``` CREATE PLUGGABLE DATABASE Al_to_delete_pdb_28978
ADMIN USER temp_admin IDENTIFIED BY alkad1312
FILE_NAME_CONVERT = ('C:\ORACLE26\ORADATA\FREE\PDBSEED\',
                     'C:\ORACLE26\ORADATA\FREE\AL_TO_DELETE_PDB_28978\');

DROP PLUGGABLE DATABASE Al_to_delete_pdb_28978 INCLUDING DATAFILES;
```
Verified with ``` SELECT name FROM v$pdbs; before and after the drop.```

Evidence: see ```screenshots/pdb_deletion/```

## Task 3: Oracle Enterprise Manager (OEM)

**The following were captured:*

**DBA Console dashboard showing live tablespace and memory usage**
**Session confirmation: SYS connected to CDB$ROOT as SYSDBA**
**PDB status showing Al_pdb_28978 in READ WRITE**
**User verification inside the PDB**

Evidence: see ```**screenshots/oem_dashboard/**```

## Challenges Faced
**Initial TNS configuration missing** — resolved by creating a manual Basic connection in SQL Developer pointing at localhost:1521 with service names FREE (CDB root) and freepdb1.

**db_create_file_dest was NULL** — resolved by querying v$datafile to identify the correct seed PDB path (C:\ORACLE26\ORADATA\FREE\PDBSEED\) and providing an explicit FILE_NAME_CONVERT clause.

**EM Express not available in Oracle 26ai Free** — resolved by using SQL Developer's Manage Database console as the equivalent management interface.

## Integrity Statement
I, confirm that this work is entirely my own, completed individually. No commands, screenshots, or repositories were copied from classmates. All evidence presented here reflects real work performed on my own Oracle 26ai Free environment. even you can obsever throughout my screenshots

## Submission Details

Repository Link: https://github.com/esengoalkadmud/oracle_pdb_ass_II_28978_Alkad<br>
PDB Name Created: Al_pdb_28978<br>
Issues Encountered: Yes<br>

