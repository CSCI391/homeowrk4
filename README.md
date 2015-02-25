# Creating Views and Indexes

-   1. What will happen if a unique index is created on a nonunique field?

-   2. Are the following statements true or false?
    -   Both views and indexes take up space in the database and therefore
        must be factored in the planning of the database size.
    
    -   If someone updates a table on which a view has been created, the
        view must have an identical update performed on it to see the same
        data.
    
    -   If you have the disk space and you really want to get your queries
        smoking, the more indexes the better.

-   Is the following CREATE statement correct?

    create view credit_debts as
         (select all from debts
         where account_id = 4);

1.  Is the following CREATE statement correct?

    create unique view debts as
     select * from debts_tbl;

1.  Is the following CREATE statement correct?

    drop * from view debts;

1.  Is the following CREATE statement correct?

    create index id_index on bills
        (account_id);

# Controlling Transactions

1.  When nesting transactions, does issuing a ROLLBACK TRANSACTION
    command cancel the current transaction and roll back the batch of
    statements into the upper-level transaction? Why or why not?

1.  Can savepoints be used to "save off" portions of a transaction? Why or why not?

2.  Can a COMMIT command be used by itself or must it be embedded?

3.  If you issue the COMMIT command and then discover a mistake, can
    you still use the ROLLBACK command?

4.  Will using a savepoint in the middle of a transaction save all
    that happened before it automatically?

# Database Security

1.  What is wrong with the following statement?

    GRANT CONNECTION TO DAVID;

1.  True or False (and why): Dropping a user will cause all objects
    owned by that user to be dropped as well.

1.  What would happen if you created a table and granted select
    privileges on the table to public?

2.  Is the following SQL statement correct?

    create user RON
      identified by RON;

1.  Is the following SQL statement correct?

    alter RON
        identified by RON;

1.  If you own a table, who can select from that table?

# Streamlining SQL Statements for Improved Performance

1.  What does streamline an SQL statement mean?

2.  Should tables and their corresponding indexes reside on the same disk?

3.  Why is the arrangement of conditions in an SQL statement important?

4.  What happens during a full-table scan?

5.  How can you avoid a full-table scan?

6.  What are some common hindrances of general performance?

7.  Make the following SQL statement more readable.

    SELECT EMPLOYEE.LAST_NAME, EMPLOYEE.FIRST_NAME, EMPLOYEE.MIDDLE_NAME,
    EMPLOYEE.ADDRESS, EMPLOYEE.PHONE_NUMBER, PAYROLL.SALARY, PAYROLL.POSITION,
    EMPLOYEE.SSN, PAYROLL.START_DATE FROM EMPLOYEE, PAYROLL WHERE
    EMPLOYEE.SSN = PAYROLL.SSN AND EMPLOYEE.LAST_NAME LIKE 'S%' AND
    PAYROLL.SALARY > 20000;

1.  Rearrange the conditions in the following query to optimize data retrieval time.Use the following statistics (on the tables in their entirety) to determine the order of the conditions:

593 individuals have the last name SMITH.

712 individuals live in INDIANAPOLIS.

3,492 individuals are MALE.

1,233 individuals earn a salary >= 30,000.

5,009 individuals are single.

Individual<sub>id</sub> is the primary key for both tables.

    SELECT M.INDIVIDUAL_NAME, M.ADDRESS, M.CITY, M.STATE, M.ZIP_CODE,
           S.SEX, S.MARITAL_STATUS, S.SALARY
    FROM MAILING_TBL M,
         INDIVIDUAL_STAT_TBL S
    WHERE M.NAME LIKE 'SMITH%'
      AND M.CITY = 'INDIANAPOLIS'
      AND S.SEX = 'MALE'
      AND S.SALARY >= 30000
      AND S.MARITAL_STATUS = 'S'
      AND M.INDIVIDUAL_ID = S.INDIVIDUAL_ID;

# Using Views to Retrieve Useful Information from the Data Dictionary

1.  What types of information are stored in the data dictionary?

2.  How can you use performance statistics?

3.  What are some database objects?