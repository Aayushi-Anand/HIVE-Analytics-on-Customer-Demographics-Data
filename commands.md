<b>Sqoop import command</b>

<p>sqoop import --connect jdbc:mysql://localhost:3306/adventureworks?useSSL=False --username root --password-file file:///home/saif/LFS/cohort_c9/envvar/sqoop.pwd --delete-target-dir --target-dir /user/saif/HFS/Input/adventureworks --query "select CustomerID,TerritoryID,AccountNumber,CustomerType,ModifiedDate,Demographics from customer_individual \
where \$CONDITIONS" --split-by CustomerID</p>


<b>Hive manage table</b>
<p>create table cust_indi(CustomerID int,TerritoryID int,AccountNumber string,CustomerType string,ModifiedDate timestamp,Demographics string) row format delimited fields terminated by ',' tblproperties("skip.header.line.count"="1") ;</p>

<b>Load data in manage table</b>
<p>load data inpath "/user/saif/HFS/Input/adventureworks/" into table cust_indi;</p>


<b>Create new table and load data from manage table to this new table</b>
<p>create table ext_cust as select customerid,territoryid,accountnumber,customertype,modifieddate,xpath(demographics,'IndividualSurvey/TotalPurchaseYTD/text()'),xpath(demographics,'IndividualSurvey/DateFirstPurchase/text()'),xpath(demographics,'IndividualSurvey/BirthDate/text()'),xpath(demographics,'IndividualSurvey/MaritalStatus/text()'),xpath(demographics,'IndividualSurvey/YearlyIncome/text()'),xpath(demographics,'IndividualSurvey/Gender/text()'),xpath(demographics,'IndividualSurvey/TotalChildren/text()'),xpath(demographics,'IndividualSurvey/NumberChildrenAtHome/text()'),xpath(demographics,'IndividualSurvey/Education/text()'),xpath(demographics,'IndividualSurvey/Occupation/text()'),xpath(demographics,'IndividualSurvey/HomeOwnerFlag/text()'),xpath(demographics,'IndividualSurvey/NumberCarsOwned/text()'),xpath(demographics,'IndividualSurvey/CommuteDistance/text()') from cust_indi;</p>


<b>Sqoop import for credit card table</b>
<p>sqoop import --connect jdbc:mysql://localhost:3306/adventureworks?useSSL=False --username root --password-file file:///home/saif/LFS/cohort_c9/envvar/sqoop.pwd --delete-target-dir --target-dir /user/saif/HFS/Input/adventureworks1 --query "select CreditCardID,CardType,CardNumber,ExpMonth,ExpYear,ModifiedDate from creditcard \
where \$CONDITIONS" -m 1</p>


<b>Create manage table for credit card</b>
create table credit_hive(CreditCardID  int,CardType string,CardNumber bigint,ExpMonth int,ExpYear int,ModifiedDate timestamp ) row format delimited fields terminated by ','  tblproperties("skip.header.line.count"="1");


<b>Load data in manage table for credit card table</b>
<p>load data inpath "/user/saif/HFS/Input/adventureworks1/" into table credit_hive;</p>


<b>Analytics Query</b>

select sum(totalpurchaseytd),education,occupation from sqlhive group by education,occupation;

select sum(numbercarsowned),territoryid,gender from sqlhive group by territoryid,gender;

select  yearlyincome, education, sum(totalpurchaseytd) num_of_occurence from sqlhive  group by yearlyincome, education;








