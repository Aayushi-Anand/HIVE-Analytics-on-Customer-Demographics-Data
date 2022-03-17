# HIVE Analytics on Customer Demographics Data
**Buisness Problem**:
A company XYZ wants to work on the database for its visiting customers and it is trying to analyse the year to date total revenue based on the database of retail sales data called adventure works. For this particular idea, company wants to use only customer, individual and credit card details.
These datasets comprise of bulk and raw data that needs to be transformed and cleaned in order to bring out the data for analytics purpose and getting the insights out of it.

**Approach**:
<p>Data is present in MySQL database.</p>
<p>Load the data from MySQL to HDFS using SQOOP.</p>
<p>Create and load data to HIVE table.</p>
<p>Read data from HIVE in Spark and perform data cleaning.</p>
<p>Load the data again to hive and perform analytics.</p>

<br>
<h4>Tool And Technologies</h4>
<ul>
 <li>MySQL</li>
 <li>Sqoop</li>
 <li>Hive</li>
 <li>Spark</li>
</li>
</ul>  

<br>
<h3>Data Source Description</h3>
<p><b>Customer</b>: This table contain all customer data related information.</p>

<img width="150" alt="Customer" src="https://user-images.githubusercontent.com/100192267/158633317-f3be96bd-e806-414e-a7e7-bef2b461ac20.png">

<p><b>Individual</b>: This table contain all Individual data information.</p>

![photo_1](https://user-images.githubusercontent.com/100331434/158746774-b96549d7-f6ba-477c-b85e-2290fa45ce79.jpeg)






<p><b>Credit Card</b>: This table contain all credit card data information.</p>
<img width="150" alt="CreditCard" src="https://user-images.githubusercontent.com/100192267/158635208-dfacf7cb-6f37-4ffc-ab86-4cb61bddc522.png">

<b>Project Architecture</b>
![Screenshot (9)](https://user-images.githubusercontent.com/100192267/158649770-9d80409e-6864-468d-bf61-dbbcd310c423.png)

