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
