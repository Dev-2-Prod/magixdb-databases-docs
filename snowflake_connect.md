## Snowflake

Getting required credentials for connection 
following credentials are required. 

```       
  user='Username of snowflake account',
  password='password for snowflake account',
  account='account identifier ,
  warehouse='warehouse to run query on',
  database='database name',
  schema='schema name in that database'
```

1. username and password are what you get after account creation.

2. Fetching account identifier:
  it's buried underneath to copy the account identifier follow below screenshot select the account and copy identifier 
    ![image](https://github.com/user-attachments/assets/ab1049cd-bbbb-49d0-8a80-23f4ef10c0b5)

3. Warehouse
   log into the snowflake , create a sql worksheet by going on create button and run `SHOW WAREHOUSES;` this will show your warehouses choose one which is active currently and provide that value
   ![image](https://github.com/user-attachments/assets/b7670b7d-668f-45c7-8e2f-8959788093e2)
   ![image](https://github.com/user-attachments/assets/307cfdeb-320e-4d06-a9b9-314e6a7786a9)

4. database and schema name
   they are inside data tab, refer screenshot below 
 ![image](https://github.com/user-attachments/assets/ce70b63c-0f7d-417a-92b2-dcecd48f0b3e)


