# MODULE-2


CREATE TABLE SALARY(
basicSalary number,
hra number,
conveyenceAllowance number,
otherAllowance number,
personalAllowance number,
monthlyTax number,
epf number,
companyPf number,
grossSalary number,
netSalary number
);
________________________________________________________________________
alter table salary add associateId number;
________________________________________________________________________
drop table salary;
________________________________________________________________________
ALTER TABLE SALARY
ADD CONSTRAINT FK_AssociateID
FOREIGN KEY (associateId) REFERENCES Associate(associateId);
________________________________________________________________________
CREATE TABLE Bank_Details(
accountNumber number,
bankName varchar2(30),
ifscCode varchar2(30)
);
________________________________________________________________________
alter table BANK_DETAILS add associateId number;
________________________________________________________________________
ALTER TABLE BANK_DETAILS
ADD CONSTRAINT AssociateID_FK
FOREIGN KEY (associateId) REFERENCES Associate(associateId);
________________________________________________________________________
ALTER TABLE TRANSACTION ADD AccountNo number;
ALTER TABLE TRANSACTION
ADD CONSTRAINT AccountNo_FK
FOREIGN KEY (accountNo) REFERENCES Account(accountNo);
_________________________________________________________________________
SELECT * FROM ACCOUNT;
SELECT * FROM ASSOCIATE;
SELECT * FROM BANK_DETAILS;
SELECT * FROM SALARY;
SELECT * FROM TRANSACTION;
_________________________________________________________________________
SELECT ACCOUNTNO,ACCOUNTBALANCE FROM ACCOUNT WHERE ACCOUNTBALANCE>2000;
SELECT ACCOUNTNO,ACCOUNTBALANCE FROM ACCOUNT WHERE ACCOUNTBALANCE BETWEEN 20000 AND 40000;
SELECT ACCOUNTNO,ACCOUNTBALANCE FROM ACCOUNT WHERE ACCOUNTTYPE = 'SAVINGS';
SELECT * FROM ACCOUNT WHERE ACCOUNTTYPE = 'CURRENT';
SELECT * FROM ACCOUNT WHERE ACCOUNTTYPE = 'SAVINGS';
UPDATE ACCOUNT SET ACCOUNTSTATUS = 'ACTIVE' WHERE ACCOUNTNO = 100005;
UPDATE ACCOUNT SET ACCOUNTSTATUS = 'ACTIVE',ATTEMPT = 0 WHERE ACCOUNTNO = 100004;
_________________________________________________________________________
SELECT ASSOCIATEID, FIRSTNAME, LASTNAME FROM ASSOCIATE WHERE YEARLYINVESTMENTUNDER80C >100000;
SELECT ASSOCIATEID, FIRSTNAME, LASTNAME, DEPARTMENT FROM ASSOCIATE WHERE DEPARTMENT  != 'IT';
SELECT ASSOCIATEID, FIRSTNAME, LASTNAME, DEPARTMENT FROM ASSOCIATE WHERE YEARLYINVESTMENTUNDER80C BETWEEN 100000 AND 200000;
_________________________________________________________________________
SELECT * FROM BANK_DETAILS WHERE BANKNAME LIKE '%S%';
_________________________________________________________________________
SELECT ASSOCIATEID, BASICSALARY, NETSALARY FROM SALARY WHERE BASICSALARY>30000;
SELECT * FROM SALARY WHERE BASICSALARY>30000;
_________________________________________________________________________
select sysdate from dual;
SELECT ADD_MONTHS(SYSDATE, 10) FROM DUAL;
SELECT MONTHS_BETWEEN(SYSDATE, '01-JAN-18') FROM DUAL;
SELECT EXTRACT(YEAR FROM SYSDATE) FROM DUAL;
SELECT EXTRACT(MONTH FROM DATE '2013-01-03') FROM DUAL;
SELECT EXTRACT(MONTH FROM SYSDATE) FROM DUAL;
SELECT TO_CHAR(SYSDATE,'DD MONTH,YEAR')FROM DUAL;
SELECT TO_CHAR(SYSDATE,'DDTH MONTH,YEAR')FROM DUAL;
SELECT TO_CHAR(17000,'$99,,999.00')FROM DUAL;
_______________________________________________________________________________
SELECT A.ASSOCIATEID, A.FIRSTNAME, A.LASTNAME, S.BASICSALARY, S.NETSALARY, B.BANKNAME 
FROM ASSOCIATE A, SALARY S, BANK_DETAILS B
WHERE A.ASSOCIATEID = S.ASSOCIATEID AND A.ASSOCIATEID = B.ASSOCIATEID;
___________________________________________________________________________________________
SELECT * FROM ASSOCIATE,SALARY, BANK_DETAILS 
WHERE ASSOCIATE.YEARLYINVESTMENTUNDER80C <100000;
