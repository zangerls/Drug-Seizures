# Annual Drug Seizures

A brief analysis in SQL on drug seizures world-wide between 1970 and 2020, with a total of roughly 50.000 rows.

## The Data

The associated data for this analysis comes from [Kaggle.](https://www.kaggle.com/ramjasmaurya/drug-seizues-annually-since-1970s)

## SQL Analysis

### The Database
The DBMS used was MariaDB, locally hosted on my personal PC for the duration of the analysis.

### Snippets

Returning the first five rows of the 'seizures' table.

```sql
SELECT * 
FROM seizures
LIMIT 5;
+----------+-----------+----------+---------------+------------------+------+---------------+
| Region   | Country   | ISO_Code | Drug_Group    | Drug             | Year | KG_Equivalent |
+----------+-----------+----------+---------------+------------------+------+---------------+
| Africa   | Algeria   | DZA      | Cannabis-type | Marijuana (herb) | 1970 |           141 |
| Africa   | Algeria   | DZA      | Cannabis-type | Hashish (resin)  | 1970 |           140 |
| Americas | Argentina | ARG      | Cocaine-type  | Coca leaf        | 1970 |         13482 |
| Oceania  | Australia | AUS      | Opioids       | Heroin           | 1970 |             1 |
| Oceania  | Australia | AUS      | Opioids       | Opium            | 1970 |             9 |
+----------+-----------+----------+---------------+------------------+------+---------------+
```

Returning the sum of drugs seized (in kg) by region.

```sql
SELECT Region, FLOOR(SUM(KG_Equivalent)) AS Kilograms_Seized 
FROM seizures 
GROUP BY Region 
ORDER BY Kilograms_Seized DESC;
+----------+------------------+
| Region   | Kilograms_Seized |
+----------+------------------+
| Americas |        728008369 |
| Africa   |        527922088 |
| Asia     |        102219424 |
| Europe   |         77274364 |
| Oceania  |          1686923 |
+----------+------------------+
```

## The Dashboard

The main part of this project was the dashboard for the data.

The PowerBI file contains four individual dashboards and is fully interactive with multiple filters available to the user.

The four dashboards are the following:
* main dashboard / summary
* data by state
* data by drug group
* data by continent / year

### Preview

#### Main Dashboard
![main](https://github.com/zangerls/Drug-Seizures/blob/main/Dashboard%20Images/Main.png)

#### Main Dashboard (filtered by Cannabis and Europe)
![main-eu](https://github.com/zangerls/Drug-Seizures/blob/main/Dashboard%20Images/Main%20-%20Cannabis%20in%20Europa.png)

#### Data by state (filtered for Canada)
![canada](https://github.com/zangerls/Drug-Seizures/blob/main/Dashboard%20Images/Staaten%20-%20Canada.png)
