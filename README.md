# Assignment-2
//Task1
ALTER SESSION SET CONTAINER = XEPDB1;
SHOW CON_NAME;
CREATE USER ST_PLSQLAUCA IDENTIFIED BY "Auca@2020";
GRANT CONNECT, RESOURCE TO ST_PLSQLAUCA;
sqlplus ST_PLSQLAUCA/"Auca@2020"@//localhost:1521/XEPDB1
//Task2
ALTER SESSION SET CONTAINER = CDB$ROOT;
CREATE PLUGGABLE DATABASE st_to_delete_pdb
ADMIN USER admin IDENTIFIED BY admin123
FILE_NAME_CONVERT = ('C:\APP\ANNYS\PRODUCT\21C\ORADATA\XE\PDBSEED\', 'C:\APP\ANNYS\PRODUCT\21C\ORADATA\XE\st_to_delete_pdb\');
ALTER PLUGGABLE DATABASE st_to_delete_pdb OPEN;
LTER PLUGGABLE DATABASE st_to_delete_pdb SAVE STATE;
ALTER PLUGGABLE DATABASE st_to_delete_pdb CLOSE IMMEDIATE;
ALTER PLUGGABLE DATABASE st_to_delete_pdb UNPLUG INTO '/u01/app/oracle/admin/st_to_delete_pdb.xml';
DROP PLUGGABLE DATABASE st_to_delete_pdb INCLUDING DATAFILES;
SELECT NAME, OPEN_MODE FROM V$PDBS;
Exit;
//Task3
SELECT DBMS_XDB_CONFIG.GETHTTPPORT() AS HTTP_PORT,
       DBMS_XDB_CONFIG.GETHTTPSPORT() AS HTTPS_PORT
FROM dual;
BEGIN
    DBMS_XDB_CONFIG.SETHTTPPORT(8080);  -- Set HTTP port to 8080
    DBMS_XDB_CONFIG.SETHTTPSPORT(5500); -- Keep HTTPS port as 5500 (or change if needed)
END;
/
SELECT DBMS_XDB_CONFIG.GETHTTPPORT() AS HTTP_PORT,
       DBMS_XDB_CONFIG.GETHTTPSPORT() AS HTTPS_PORT
FROM dual;
SHUTDOWN IMMEDIATE;
STARTUP;
//Task4
