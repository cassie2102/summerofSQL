

/*
Requirements
Input the data (help)
Split the Transaction Code to extract the letters at the start of the transaction code. These identify the bank who processes the transaction (help)
Rename the new field with the Bank code 'Bank'. 
Rename the values in the Online or In-person field, Online of the 1 values and In-Person for the 2 values. 
Change the date to be the day of the week (help)

Different levels of detail are required in the outputs. You will need to sum up the values of the transactions in three ways (help):
1. Total Values of Transactions by each bank
2. Total Values by Bank, Day of the Week and Type of Transaction (Online or In-Person)
3. Total Values by Bank and Customer Code
Output each data file (help)
*/
SELECT 
    split_part(transaction_code, '-', 1)  AS BANK ,
    CASE
        WHEN ONLINE_OR_IN_PERSON = 1 THEN 'Online'
        ELSE 'In-Person'
        END
        AS "TYPE",
    dayname(date_from_parts(split_part(left(transaction_date,10), '/', 3),
        split_part(left(transaction_date,10), '/', 2),
        split_part(left(transaction_date,10), '/', 1)))
        AS "DAY_OF_WEEK",
    VALUE,
    CUSTOMER_CODE
FROM PD2023_WK01;

SELECT
split_part(transaction_code, '-', 1)  AS BANK ,
SUM(VALUE) AS TOTAL_VALUE
FROM PD2023_WK01
GROUP BY SPLIT_PART(TRANSACTION_CODE,'-',1);

SELECT 
    split_part(transaction_code, '-', 1)  AS BANK ,
    CASE
        WHEN ONLINE_OR_IN_PERSON = 1 THEN 'Online'
        ELSE 'In-Person'
        END
        AS "TYPE",
    dayname(date_from_parts(split_part(left(transaction_date,10), '/', 3),
        split_part(left(transaction_date,10), '/', 2),
        split_part(left(transaction_date,10), '/', 1)))
        AS "DAY_OF_WEEK",
sum(value) as total_value from pd2023_wk01
group by split_part(transaction_code, '-', 1),
DAY_OF_WEEK,
VALUE,
TYPE;

SELECT 
    split_part(transaction_code, '-', 1)  AS BANK ,
    customer_code,
   sum(value) as total_value from pd2023_wk01
   group by split_part(transaction_code, '-', 1),
   customer_code;
   
   


