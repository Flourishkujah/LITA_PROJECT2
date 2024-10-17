# LITA_PROJECT2

# Project 2: Customer Segmentation for a Subscription Service 
---

## **Summary**:
This project focuses on analyzing customer data for a subscription service to uncover segments and trends. The aim is to gain insights into customer behavior, monitor subscription types, and identify patterns in cancellations and renewals. The final output will be a Power BI dashboard showcasing the analysis.



## 1. **Excel**:  

![image](https://github.com/user-attachments/assets/6829f2cc-87d4-4a66-bd2e-1c603deb8109)

   - Use pivot tables to analyze customer data and identify subscription trends.
   
     ![image](https://github.com/user-attachments/assets/1dce94d9-a1d3-4e65-b10d-ca642e2cdeef)

   - Calculate the average subscription duration and determine the most popular subscription types.
  
  ![image](https://github.com/user-attachments/assets/30a9fbaf-e744-49c3-877b-9b80fb9572de)
  
  ![image](https://github.com/user-attachments/assets/1dce94d9-a1d3-4e65-b10d-ca642e2cdeef)

   - Generate any other insightful reports.
   - 
![image](https://github.com/user-attachments/assets/1a5d8fd3-619c-4db3-b72c-81709f81fb32)



## 2. **SQL**:  
   
   ### Write queries to gather insights on:
   
   - Total number of customers per region.
     ```
     SELECT region, COUNT(customerid) AS Totalnumberofcustomers
     FROM LITACapstoneDatasetCusCSV
     GROUP By region;
      ```

![image](https://github.com/user-attachments/assets/f3d80b15-0ab8-4055-82d1-6ff3d9cfc5b0)

   - The most popular subscription type by customer count.

```
SELECT TOP 1 SubscriptionType, COUNT(customerid) AS Numberofcustomers
FROM LITACapstoneDatasetCusCSV
GROUP By SubscriptionType
ORDER BY NumberOfCustomers DESC;
```

![image](https://github.com/user-attachments/assets/1fcaeb56-ab45-4c72-be70-013d898d9359)

   - Customers who canceled their subscription within 6 months.

```
SELECT CustomerID,DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) AS DurationInMonths
FROM LITACapstoneDatasetCusCSV
WHERE Canceled = 1 
AND DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) <= 6;
```

![image](https://github.com/user-attachments/assets/3b25f933-a3b3-4b63-80c8-389dab082360)

   - Average subscription duration for all customers.

```
SELECT AVG(Subcription_Duration_months) AS AverageSubscriptionDuration
FROM LITACapstoneDatasetCusCSV;
```

![image](https://github.com/user-attachments/assets/4d981c86-4ae9-460f-bc65-61c86591d5b4)

   - Customers with subscriptions longer than 12 months.

```
SELECT CustomerID,Subcription_Duration_months AS DurationInMonths
FROM LITACapstoneDatasetCusCSV
WHERE Canceled = 1 
AND Subcription_Duration_months >12;
```

![image](https://github.com/user-attachments/assets/a0540719-e6b6-4c33-85dd-e8b00af2a4c6)

   - Total revenue by subscription type.
```
SELECT Subscriptiontype, SUM(revenue) As TotalRevenue
FROM LITACapstoneDatasetCusCSV
GROUP By Subscriptiontype;
```

![image](https://github.com/user-attachments/assets/2dbbac4e-158e-4526-a43e-c568da135e76)


   - Top 3 regions with the highest cancellations.
```
 SELECT TOP 3  Region,COUNT(CustomerID) AS NumberOfCancellations
FROM LITACapstoneDatasetCusCSV
WHERE Canceled = 'TRUE'
GROUP BY Region
ORDER BY NumberOfCancellations DESC;
```

![image](https://github.com/user-attachments/assets/788c7f81-df95-4ff1-866f-9ff177d16ae2)

   - Total number of active vs. canceled subscriptions.

```
SELECT  CASE 
        WHEN Canceled = 1 THEN 'True'
        WHEN Canceled = 0 THEN 'False'
    END AS Canceled,COUNT(CustomerID) AS TotalSubscriptions
FROM LITACapstoneDatasetCusCSV
GROUP BY Canceled;
```
![image](https://github.com/user-attachments/assets/8a3dc1c6-bc35-492b-9a5f-4cb7e1dc97ec)


## 3. **Power BI**:  
   - Develop a Power BI dashboard that visualizes key segments, cancellations, and subscription trends. Add slicers for interactive exploration.

   ![image](https://github.com/user-attachments/assets/08797a2a-9980-48af-a935-3c3950780481)
