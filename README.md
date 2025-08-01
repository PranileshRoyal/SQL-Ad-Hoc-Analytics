# SQL-Ad-Hoc-Analytics

## Project Overview
The [**Codebasics Data Analytics Bootcamp**](https://codebasics.io/bootcamps/data-analytics-bootcamp-with-practical-job-assistance) exhibits a fictional company called **AtliQ Technologies**. In the [**Codebasics Resume Project Challenge #4**](https://codebasics.io/challenge/codebasics-resume-project-challenge), AtliQ’s upper management team has posted ten ad-hoc business questions that need to be addressed. The objective of this project is to leverage **SQL in MySQL** to answer these questions.




## AtliQ Technologies Business Model

<details>
  <summary><b>Overview</b></summary>

AtliQ manufactures computer hardware **products** (e.g., mouse, keyboard, printer, monitor) and then sells them to various **customers** which are stores such as Amazon and Best Buy. Hence, AtliQ's customers are in the form of <ins>store businesses</ins> (e.g., Amazon, Best Buy) and should not be confused with customers in the form of people (i.e., the people purchasing products from Amazon or Best Buy).

<br>
</details>

<details>
  <summary><b>Customers</b></summary>

AtliQ's customers are categorized into two different **platforms**:
1. Brick & Motar
   * stores that have physical location(s)
2. E-Commerce
   * stores which only sell products online
<br>

AtliQ's customers are categorized into three different **channels**:
1. Retailer
   * Stores not owned by AtliQ (e.g. Amazon, Best Buy)
3. Direct
   * Stores owned by AtliQ. These are AltiQ Exclusive and AtliQ E-Store.
5. Distributor
   * Some markets have laws/regulations which only allow AtliQ to sell products to a distributor type customer within that market. AtliQ sells products to the distributor; the distributor then sells the products to various stores within that market.

<br>
</details>

<details>
  <summary><b>Profit and Loss (P&L) Statement</b></summary>

This simplified P&L statement should give a better understanding of AtliQ's business model. In this example, the P&L values are derived from one sale transaction of one product being sold to one customer.
| P&L Line Item | Description | P&L Value Formula | P&L Value Calculation | Final P&L Value |
| :- | :- | :- | :- | -: |
| Gross Price |  The base price of a product | not applicable | `not applicable` | `$50.00` |
| Pre-Invoice Deduction | For every fiscal year, the sales team determines a<br>pre-invoice deduction percentage for each<br><ins>specific customer</ins>. The pre-invoice deduction<br>percentage is based on AtliQ's relationship and<br>experience with the customer. The pre-invoice<br>deduction is applied to the gross price of the<br>product before it is billed to the customer. In this<br>example, the customer receives a pre-invoice<br>deduction of 10% of gross price. | (Gross Price $) *<br> (Pre&nbsp;Invoice&nbsp;Deduction&nbsp;%) | `$50.00` *<br>`0.10` | `$5.00` |
| Net Invoice Sales | The amount of money that is billed to the<br>customer to obtain the product, after<br>pre-invoice deductions are subtracted<br>from gross price. | (Gross Price $) -<br>(Pre&nbsp;Invoice Deduction $) | `$50.00` -<br>`$5.00` | `$45.00` |
| Post-Invoice Deudctions | For&nbsp;each&nbsp;calendar&nbsp;month,&nbsp;the&nbsp;sales&nbsp;team<br>determines&nbsp;a&nbsp;post-invoice&nbsp;deduction&nbsp;percentage<br>based&nbsp;on&nbsp;a&nbsp;<ins>specific&nbsp;customer&nbsp;and&nbsp;product</ins>.&nbsp;For<br>example,&nbsp;if&nbsp;AtliQ&nbsp;sells&nbsp;a&nbsp;product&nbsp;to&nbsp;a&nbsp;customer<br>and&nbsp;that&nbsp;customer&nbsp;agrees&nbsp;to&nbsp;display&nbsp;the&nbsp;product&nbsp;at<br>a&nbsp;prime&nbsp;location&nbsp;within&nbsp;the&nbsp;store&nbsp;during&nbsp;a<br>specific&nbsp;calendar&nbsp;month,&nbsp;AtliQ&nbsp;may&nbsp;pay&nbsp;that<br>customer&nbsp;a&nbsp;post-invoice&nbsp;deduction.&nbsp;AtliQ&nbsp;pays&nbsp;a<br>post-invoice&nbsp;deduction&nbsp;amount&nbsp;as&nbsp;a&nbsp;rebate&nbsp;to&nbsp;the<br>customer&nbsp;after&nbsp;net&nbsp;invoice&nbsp;sales.&nbsp;In&nbsp;this&nbsp;example,<br>the&nbsp;customer&nbsp;receives&nbsp;a&nbsp;post-invoice&nbsp;deduction&nbsp;of<br>20%&nbsp;of&nbsp;net&nbsp;invoice&nbsp;sales. | (Net Invoice Sales $) *<br>(Post-Invoice Deduction %) | `$45.00` *<br>`0.20` | `$9.00` |
| Net Sales | Revenue | (Net Invoice Sales $) -<br>(Post-Invoice Deudctions $) | `$45.00` -<br>`$9.00` | `$36.00` |
| Cost of Goods Sold (COGS) | Expenses AtliQ incurs such as manufacturing<br>products, shipping products, and storing products<br>in warehouses. | (Manufacturing Cost $) +<br>(Freight Cost $) +<br>(Other COGS $) | `$9.00` +<br>`$4.00` +<br>`$3.00` | `$16.00` |
| Gross Margin | AtliQ's Profit after deducing COGS from Net Sales. | (Net Sales $) -<br>(COGS $) | `$36.00` -<br>`$16.00` | `$20.00` |
| Operational Expenses | Expenses AtliQ incurs from activities such as<br>advertising and promotions of products<br>performed by the marketing team. | (Ads & Promotions $) +<br>(Other&nbsp;Operational&nbsp;Expense&nbsp;$) | `$10.00` +<br>`$5.00` | `$15.00` |
| Net Profit | AtliQ's Profit after deducting operational expenses<br>from gross margin. | (Gross Margin $) -<br>(Operational Expenses $) | `$20.00` -<br>`$15.00` | `$5.00` |

<br>
</details>


<details>
  <summary><b>AtliQ Fiscal Dates</b></summary>

AtliQ's fiscal year begins in September and ends in August the following year. The example below shows AtliQ's fiscal dates for fiscal year 2021 compared to calendar dates.
| 	Calendar Month and Year	 | 	AtliQ Fiscal Year	 | 	AtliQ Fiscal Month Number | 	AtliQ Fiscal Quarter	 |
| 	-:	 | 	-:	 | 	-:	 | 	-:	 |
| 	September 2020	 | 	2021	 | 	1	 | 	Q1	 |
| 	October 2020	 | 	2021	 | 	2	 | 	Q1	 |
| 	November 2020	 | 	2021	 | 	3	 | 	Q1	 |
| 	December 2020	 | 	2021	 | 	4	 | 	Q2	 |
| 	January 2021	 | 	2021	 | 	5	 | 	Q2	 |
| 	February 2021	 | 	2021	 | 	6	 | 	Q2	 |
| 	March 2021	 | 	2021	 | 	7	 | 	Q3	 |
| 	April 2021	 | 	2021	 | 	8	 | 	Q3	 |
| 	May 2021	 | 	2021	 | 	9	 | 	Q3	 |
| 	June 2021	 | 	2021	 | 	10	 | 	Q4	 |
| 	July 2021	 | 	2021	 | 	11	 | 	Q4	 |
| 	August 2021	 | 	2021	 | 	12	 | 	Q4	 |

<br>
</details>









## Data Sources

<details>
  <summary><b>Dimension Tables</b></summary>

### Dimension Tables
The following **dimension tables** are in MySQL schema `gdb0041`. Sample records from the dimension tables are provided below.

**dim_customer**
| customer_code | customer         | platform     | channel   | market       | sub_zone | region |
|-------------:|:---------------|:--------------|:------------|:------------|:---------|:-------|
| 90004067     | Amazon          | E-Commerce  | Retailer | Japan      | ROA     | APAC   |
| 90004068     | Amazon          | E-Commerce  | Retailer | Japan      | ROA     | APAC   |
| 90007197     | Amazon          | E-Commerce  | Retailer | South Korea | ROA     | APAC   |
| 90022081     | Amazon          | E-Commerce  | Retailer | USA        | NA      | NA     |
| 90022082     | Amazon          | E-Commerce  | Retailer | USA        | NA      | NA     |
| 90023023     | Amazon          | E-Commerce  | Retailer | Canada     | NA      | NA     |
| 90023030     | Amazon          | E-Commerce  | Retailer | Canada     | NA      | NA     |
| 70004070     | Atliq e Store   | E-Commerce  | Direct   | Japan      | ROA     | APAC   |
| 70007199     | Atliq e Store   | E-Commerce  | Direct   | South Korea | ROA     | APAC   |
| 70022085     | Atliq e Store   | E-Commerce  | Direct   | USA        | NA      | NA     |
| 70023032     | Atliq e Store   | E-Commerce  | Direct   | Canada     | NA      | NA     |
| 70004069     | Atliq Exclusive | Brick & Mortar | Direct | Japan      | ROA     | APAC   |
| 70007198     | Atliq Exclusive | Brick & Mortar | Direct | South Korea | ROA     | APAC   |
| 70022084     | Atliq Exclusive | Brick & Mortar | Direct | USA        | NA      | NA     |
| 70023031     | Atliq Exclusive | Brick & Mortar | Direct | Canada     | NA      | NA     |
| 90022078     | Costco          | Brick & Mortar | Retailer | USA      | NA      | NA     |
| 90023027     | Costco          | Brick & Mortar | Retailer | Canada   | NA      | NA     |
| 90022080     | Staples         | Brick & Mortar | Retailer | USA      | NA      | NA     |
| 90023029     | Staples         | Brick & Mortar | Retailer | Canada   | NA      | NA     |
| 80001019	   | Neptune	       | Brick & Mortar | Distributor	| China |	ROA |	APAC |
| 80006154	   | Synthetic	     | Brick & Mortar	| Distributor	| Philiphines |	ROA |	APAC |
 
Notes:
* `customer_code` is a primary key field. 


**dim_product**
| 	product_code	 | 	division	 | 	segment	 | 	category	 | 	product	 | 	variant	 |
| 	-:	 | 	:-	 | 	:-	 | 	:-	 | 	:-	 | 	:-	 |
| A7119160102    | N & S    | Networking | Wi fi extender         | AQ Wi Power Dx1  | Plus        |
| A7119160103    | N & S    | Networking | Wi fi extender         | AQ Wi Power Dx1  | Premium     |
| A7118160101    | N & S    | Networking | Wi fi extender         | AQ Wi Power Dx1  | Standard    |
| A6419160302    | N & S    | Storage    | External Solid State Drives | AQ Clx1      | Plus        |
| A6419160303    | N & S    | Storage    | External Solid State Drives | AQ Clx1      | Premium     |
| A6419160301    | N & S    | Storage    | External Solid State Drives | AQ Clx1      | Standard    |
| A3119150303    | P & A    | Accessories| Keyboard               | AQ Gamers        | Plus 1      |
| A3120150304    | P & A    | Accessories| Keyboard               | AQ Gamers        | Plus 2      |
| A3120150305    | P & A    | Accessories| Keyboard               | AQ Gamers        | Premium 1   |
| A3120150306    | P & A    | Accessories| Keyboard               | AQ Gamers        | Premium 2   |
| A3119150301    | P & A    | Accessories| Keyboard               | AQ Gamers        | Standard 1  |
| A3119150302    | P & A    | Accessories| Keyboard               | AQ Gamers        | Standard 2  |
| A0721150402    | P & A    | Peripherals| Graphic Card           | AQ GT 21         | Plus 1      |
| A0721150403    | P & A    | Peripherals| Graphic Card           | AQ GT 21         | Plus 2      |
| A0721150404    | P & A    | Peripherals| Graphic Card           | AQ GT 21         | Premium     |
| A0721150401    | P & A    | Peripherals| Graphic Card           | AQ GT 21         | Standard    |
| A4118110105    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Plus Blue   |
| A4118110104    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Plus Grey   |
| A4118110106    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Plus Red    |
| A4118110107    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Premium Black|
| A4118110102    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Standard Blue|
| A4118110101    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Standard Grey|
| A4118110103    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Standard Red|



Notes:
* `product_code` is a primary key field.
</details>



<details>
  <summary><b>Fact Tables</b></summary>

### Fact Tables
The following **fact tables** are in MySQL schema `gdb0041`. Sample records from the fact tables are provided below.


**fact_sales_monthly**
| date       | product_code | customer_code | sold_quantity | fiscal_year |
|------------|--------------|---------------|---------------|-------------|
| 2019-09-01 | A0118150101  | 70002017      | 137           | 2020        |
| 2019-09-01 | A0118150101  | 70002018      | 47            | 2020        |
| 2019-09-01 | A0118150102  | 70002017      | 122           | 2020        |
| 2019-09-01 | A0118150102  | 70002018      | 24            | 2020        |
| 2019-10-01 | A0118150101  | 70002017      | 40            | 2020        |
| 2019-10-01 | A0118150101  | 70002018      | 32            | 2020        |
| 2019-10-01 | A0118150102  | 70002017      | 189           | 2020        |
| 2019-10-01 | A0118150102  | 70002018      | 139           | 2020        |
| 2020-09-01 | A0118150101  | 70002017      | 248           | 2021        |
| 2020-09-01 | A0118150101  | 70002018      | 240           | 2021        |
| 2020-09-01 | A0118150102  | 70002017      | 42            | 2021        |
| 2020-09-01 | A0118150102  | 70002018      | 91            | 2021        |
| 2020-10-01 | A0118150101  | 70002017      | 297           | 2021        |
| 2020-10-01 | A0118150101  | 70002018      | 119           | 2021        |
| 2020-10-01 | A0118150102  | 70002017      | 275           | 2021        |
| 2020-10-01 | A0118150102  | 70002018      | 284           | 2021        |

Notes:
* This table contains data on the sold quantity of products for specific customers, on a monthly level
* The columns `date`, `product_code`, and `customer_code` make up a **composite primary key**
* Sales data is available for fiscal years 2020 and 2021



**fact_gross_price**
| product_code | fiscal_year | gross_price |
|--------------|-------------|-------------|
| A0118150101  | 2020        | 16.2323     |
| A0118150101  | 2021        | 19.0573     |
| A0118150102  | 2020        | 19.8577     |
| A0118150102  | 2021        | 21.4565     |
| A0118150103  | 2020        | 22.1317     |
| A0118150103  | 2021        | 21.7795     |

Notes:
* Gross price is the base price of a product
* This table contains data on the gross price of each specific product on a fiscal year level
* The columns `product_code` and `fiscal_year` make up a **composite primary key**
* Gross price data is available for fiscal years 2020 and 2021


**fact_manufacturing_cost**
| product_code | cost_year | manufacturing_cost |
|--------------|-----------|--------------------|
| A0118150101  | 2020      | 5.0207             |
| A0118150101  | 2021      | 5.5172             |
| A0118150102  | 2020      | 5.7180             |
| A0118150102  | 2021      | 6.2835             |
| A0118150103  | 2020      | 6.3264             |
| A0118150103  | 2021      | 6.5900             |

Notes:
* Manufacturing cost is one component of COGS
* This table contains data on the manufacturing cost ($) for one unit quantity of each specific product on a fiscal year level
* The columns `product_code` and `cost_year` make up a **composite primary key**
* Manufacturing cost ($) data is available for fiscal years 2020 and 2021




**fact_pre_invoice_deductions**
| 	customer_code	 | 	fiscal_year	 | 	pre_invoice_discount_pct	 |
| 	-:	 | 	-:	 | 	-:	 |
| 70002017      | 2020        | 0.0735                   |
| 70002017      | 2021        | 0.0703                   |
| 70002018      | 2020        | 0.2255                   |
| 70002018      | 2021        | 0.2061                   |
| 70003181      | 2020        | 0.0531                   |
| 70003181      | 2021        | 0.0974                   |

Notes:
* This table contains data on pre-invoice deductions (as a percentage of gross sales) for each specific customer, on a fiscal year level
* The columns `customer_code`, and `fiscal_year` make up a **composite primary key**
* Pre-invoice deductions data is available for fiscal years 2020 and 2021

</details>




























## Ad-hoc Questions/Requests and SQL Queries

<details>
  <summary><b>Question 1</b></summary>

### Question 1
#### Question:
List all the markets where the customer 'Atliq Exclusive' operates in the APAC region.

#### SQL Code:
```sql
SELECT
    DISTINCT c.market AS market_name
FROM
    gdb023.dim_customer c
WHERE
    c.customer = 'Atliq Exclusive' AND
    c.region = 'APAC'
ORDER BY
    market_name ASC
;
```

#### SQL Output:
| market_name  |
|--------------|
| Australia    |
| Bangladesh   |
| India        |
| Indonesia    |
| Japan        |
| Newzealand   |
| Philippines  |
| South Korea  |

</details>





<details>
  <summary><b>Question 2</b></summary>

### Question 2

#### Question:
What is the percentage increase in the number of unique products sold in 2021 compared to 2020?
The final output should contain these fields:
* unique_products_2020
* unique_products_2021
* percentage_chg

#### SQL Code:
```sql
WITH
    unique_2020 AS
    (
        SELECT
            COUNT(DISTINCT s.product_code) AS unique_products_2020
        FROM
            gdb023.fact_sales_monthly s
        WHERE
            s.fiscal_year = 2020
    ),
    unique_2021 AS
    (
        SELECT
            COUNT(DISTINCT s.product_code) AS unique_products_2021
        FROM
            gdb023.fact_sales_monthly s
        WHERE
            s.fiscal_year = 2021
    )
SELECT
    u20.unique_products_2020,
    u21.unique_products_2021,
    ROUND(
        (u21.unique_products_2021 - u20.unique_products_2020)
        / u20.unique_products_2020
        * 100,
        2
    ) AS percentage_chg
FROM
    unique_2020 u20,
    unique_2021 u21
;
```

#### SQL Output:
| unique_products_2020 | unique_products_2021 | percentage_chg |
|----------------------|----------------------|----------------|
| 245                  | 334                  | 36.33          |

</details>




<details>
  <summary><b>Question 3</b></summary>

### Question 3
Provide the count of unique products for each product segment. The final output should contain these fields:
* segment
* product_count

The final output should be sorted in descending order of product count.

#### SQL Code:
```sql
SELECT
    p.segment,
    COUNT(p.product_code) AS product_count
FROM
    gdb023.dim_product p
GROUP BY
    p.segment
ORDER BY
    product_count DESC
;
```

#### SQL Output:
| segment     | product_count |
|-------------|---------------|
| Notebook    | 129           |
| Accessories | 116           |
| Peripherals | 84            |
| Desktop     | 32            |
| Storage     | 27            |
| Networking  | 9             |

</details>





<details>
  <summary><b>Question 4</b></summary>

### Question 4
Which product segment had the greatest increase in the count of unique products sold in 2021 compared to 2020? The final output should contain these fields:
* segment
* unique_products_2020
* unique_products_2021
* difference

#### SQL Code:
```sql
WITH
    unique_products_sold_by_segment_fiscal_year AS
    (
        SELECT
            s.fiscal_year,
            p.segment,
            COUNT(DISTINCT s.product_code) AS count_unique_products
        FROM
            gdb023.fact_sales_monthly s
        INNER JOIN
            gdb023.dim_product p
            ON s.product_code = p.product_code
        GROUP BY
            s.fiscal_year,
            p.segment
    )
SELECT
    fy20.segment,
    fy20.count_unique_products AS unique_products_2020,
    fy21.count_unique_products AS unique_products_2021,
    fy21.count_unique_products - fy20.count_unique_products AS difference
FROM
    unique_products_sold_by_segment_fiscal_year fy20
INNER JOIN
    unique_products_sold_by_segment_fiscal_year fy21
    ON fy20.segment = fy21.segment
WHERE
    fy20.fiscal_year = 2020 AND
    fy21.fiscal_year = 2021
ORDER BY
    difference DESC
;
```


#### SQL Output:
| Segment     | Unique Products 2020 | Unique Products 2021 | Difference |
|-------------|----------------------|----------------------|------------|
| Accessories | 69                   | 103                  | 34         |
| Notebook    | 92                   | 108                  | 16         |
| Peripherals | 59                   | 75                   | 16         |
| Desktop     | 7                    | 22                   | 15         |
| Storage     | 12                   | 17                   | 5          |
| Networking  | 6                    | 9                    | 3          |

</details>











<details>
  <summary><b>Question 5</b></summary>

### Question 5
Retrieve the product(s) with the highest and lowest manufacturing cost among all products from fiscal years 2020 to 2021. The final output should contain these fields:
* product_code
* product
* variant
* manufacturing_cost

### SQL Code:
```sql
SELECT
    mc.product_code,
    p.product,
    p.variant,
    mc.manufacturing_cost
FROM
    gdb023.fact_manufacturing_cost mc
INNER JOIN
    gdb023.dim_product p
    ON mc.product_code = p.product_code
WHERE
    mc.manufacturing_cost = (SELECT MAX(manufacturing_cost) FROM gdb023.fact_manufacturing_cost) OR
    mc.manufacturing_cost = (SELECT MIN(manufacturing_cost) FROM gdb023.fact_manufacturing_cost)
ORDER BY
    mc.manufacturing_cost ASC
;
```

### SQL Output:
| product_code   | product                | variant   | manufacturing_cost |
|----------------|------------------------|-----------|---------------------|
| A2118150101    | AQ Master wired x1 Ms | Standard 1| 0.8920              |
| A6120110206    | AQ HOME Allin1 Gen 2  | Plus 3    | 240.5364            |


</details>


<details>
  <summary><b>Question 6</b></summary>

### Question 6
Generate a report of the top 5 customers in the Indian market with the highest average pre-invoice discount percentage for the 2021 fiscal year. The final output should include the following fields:
* customer
* average_pre_invoice_discount_pct


### SQL Code:
```sql
WITH
    average_pre_invoice_discount_pct_ranked AS
    (
        SELECT
            c.customer,
            AVG(pid.pre_invoice_discount_pct) AS average_pre_invoice_discount_pct,
            DENSE_RANK() OVER(ORDER BY AVG(pid.pre_invoice_discount_pct) DESC) AS rnk
        FROM
            gdb023.fact_pre_invoice_deductions pid
        INNER JOIN
            gdb023.dim_customer c
            ON pid.customer_code = c.customer_code
        WHERE
            pid.fiscal_year = 2021 AND
            c.market = "India"
        GROUP BY
            c.customer
    )
SELECT
    apr.customer,
    apr.average_pre_invoice_discount_pct
FROM
    average_pre_invoice_discount_pct_ranked apr
WHERE
    rnk <= 5
ORDER BY
    rnk ASC
;
```

### SQL Output:
| customer     | average_pre_invoice_discount_pct |
|--------------|----------------------------------|
| Flipkart     | 0.3083                           |
| Viveks       | 0.3038                           |
| Ezone        | 0.3028                           |
| Croma        | 0.3025                           |
| Vijay Sales  | 0.2753                           |

</details>






<details>
  <summary><b>Question 7</b></summary>

### Question 7
Generate a report of monthly gross sales amount for the customer 'Atliq Exclusive' from fiscal years 2020 to 2021. Also include month-over-month change in gross sales amount. The final output should include the following fields:
* month
* fiscal_year
* gross_sales_amount
* gross_sales_amount_last_month
* mom_chg


### SQL Code
```sql
WITH
    gross_sales_by_month AS
    (
        SELECT
            s.date AS month,
            s.fiscal_year,
            SUM(s.sold_quantity * gp.gross_price) AS gross_sales_amount
        FROM
            gdb023.fact_sales_monthly s
        INNER JOIN
            gdb023.dim_customer c
            ON s.customer_code = c.customer_code
        INNER JOIN
            gdb023.fact_gross_price gp
            ON s.product_code = gp.product_code
            AND s.fiscal_year = gp.fiscal_year
        WHERE
            c.customer = "Atliq Exclusive"
        GROUP BY
            s.date,
            s.fiscal_year
    ),
    gross_sales_with_lag AS
    (
        SELECT
            *,
            LAG(gs.gross_sales_amount, 1, NULL) OVER(ORDER BY gs.month ASC) AS gross_sales_amount_last_month
        FROM
            gross_sales_by_month gs
    )
SELECT
    gsl.month,
    gsl.fiscal_year,
    gsl.gross_sales_amount,
    gsl.gross_sales_amount_last_month,
    CASE
        WHEN gsl.gross_sales_amount_last_month IS NULL THEN NULL
        ELSE (gsl.gross_sales_amount - gsl.gross_sales_amount_last_month) / gsl.gross_sales_amount_last_month
    END AS mom_chg
FROM
    gross_sales_with_lag gsl
ORDER BY
    gsl.month ASC
;
```



### SQL Output
| month       | fiscal_year | gross_sales_amount | gross_sales_amount_last_month | mom_chg    |
|-------------|-------------|---------------------|-------------------------------|------------|
| 2019-09-01  | 2020        | 4496259.6724        | NULL                          | NULL       |
| 2019-10-01  | 2020        | 5135902.3467        | 4496259.6724                  | 0.14226106 |
| 2019-11-01  | 2020        | 7522892.5608        | 5135902.3467                  | 0.46476550 |
| 2019-12-01  | 2020        | 4830404.7285        | 7522892.5608                  | -0.35790593|
| 2020-01-01  | 2020        | 4740600.1605        | 4830404.7285                  | -0.01859152|
| 2020-02-01  | 2020        | 3996227.7661        | 4740600.1605                  | -0.15702071|
| 2020-03-01  | 2020        | 378770.9700         | 3996227.7661                  | -0.90521787|
| 2020-04-01  | 2020        | 395035.3535         | 378770.9700                   | 0.04293989 |
| 2020-05-01  | 2020        | 783813.4238         | 395035.3535                   | 0.98416019 |
| 2020-06-01  | 2020        | 1695216.6008        | 783813.4238                   | 1.16278077 |
| 2020-07-01  | 2020        | 2551159.1584        | 1695216.6008                  | 0.50491634 |
| 2020-08-01  | 2020        | 2786648.2601        | 2551159.1584                  | 0.09230671 |
| 2020-09-01  | 2021        | 12353509.7938       | 2786648.2601                  | 3.43310696 |
| 2020-10-01  | 2021        | 13218636.1966       | 12353509.7938                 | 0.07003082 |
| 2020-11-01  | 2021        | 20464999.0997       | 13218636.1966                 | 0.54819293 |
| 2020-12-01  | 2021        | 12944659.6509       | 20464999.0997                 | -0.36747324|
| 2021-01-01  | 2021        | 12399392.9788       | 12944659.6509                 | -0.04212291|
| 2021-02-01  | 2021        | 10129735.5675       | 12399392.9788                 | -0.18304585|
| 2021-03-01  | 2021        | 12144061.2501       | 10129735.5675                 | 0.19885274 |
| 2021-04-01  | 2021        | 7311999.9547        | 12144061.2501                 | -0.39789500|
| 2021-05-01  | 2021        | 12150225.0139       | 7311999.9547                  | 0.66168286 |
| 2021-06-01  | 2021        | 9824521.0110        | 12150225.0139                 | -0.19141242|
| 2021-07-01  | 2021        | 12092346.3245       | 9824521.0110                  | 0.23083317 |
| 2021-08-01  | 2021        | 7178707.5902        | 12092346.3245                 | -0.40634287|

</details>








<details>
  <summary><b>Question 8</b></summary>

### Question 8
Which fiscal quarter of fiscal year 2020 had the highest total quantity of products sold? Generate a report showing total quantity of products sold per fiscal quarter for fiscal year 2020. The final output should include the following fields:
* `fiscal_quarter`
* `total_sold_quantity`

Sort the results in descending order of `total_sold_quantity`

```sql
WITH
    sales_monthly_2020_with_quarters AS
    (
        SELECT
            CASE
                WHEN MONTH(s.date) IN(9,10,11) THEN 'Q1'
                WHEN MONTH(s.date) IN(12,1,2) THEN 'Q2'
                WHEN MONTH(s.date) IN(3,4,5) THEN 'Q3'
                WHEN MONTH(s.date) IN(6,7,8) THEN 'Q4'
            END AS fiscal_quarter,
            s.sold_quantity
        FROM
            gdb023.fact_sales_monthly s
        WHERE
            s.fiscal_year = 2020
    )
SELECT
    sq.fiscal_quarter,
    SUM(sq.sold_quantity) AS total_sold_quantity
FROM
    sales_monthly_2020_with_quarters sq
GROUP BY
    sq.fiscal_quarter
ORDER BY
    total_sold_quantity DESC
;
```

### SQL Output:
| fiscal_quarter | total_sold_quantity |
|----------------|---------------------|
| Q1             | 7005619             |
| Q2             | 6649642             |
| Q4             | 5042541             |
| Q3             | 2075087             |

</details>





<details>
  <summary><b>Question 9</b></summary>

### Question 9
Which of the three customer channels (Direct, Retailer, Distributor) contributed the most to total gross sales in fiscal year 2021? Generate a report showing the gross sales amount (in millions) for each customer channel in fiscal year 2021, along with each customer channel’s percentage contribution to the total gross sales. The final output should include the following fields:
* channel
* gross_sales_mln
* percentage

### SQL Code
```sql
WITH
    gross_sales_2021_by_channel AS
    (
        SELECT
            c.channel,
            SUM(s.sold_quantity * gp.gross_price) AS gross_sales
        FROM
            gdb023.fact_sales_monthly s
        INNER JOIN
            gdb023.fact_gross_price gp
            ON s.product_code = gp.product_code
            AND s.fiscal_year = gp.fiscal_year
        INNER JOIN
            gdb023.dim_customer c
            ON s.customer_code = c.customer_code
        WHERE
            s.fiscal_year = 2021
        GROUP BY
            c.channel
    )
SELECT
    channel,
    ROUND(gs.gross_sales / 1000000, 2) AS gross_sales_mln,
    gs.gross_sales / (SELECT SUM(gross_sales) FROM gross_sales_2021_by_channel) AS percentage
FROM
    gross_sales_2021_by_channel gs
ORDER BY
    gross_sales_mln DESC
;
```

### SQL Output
| channel     | gross_sales_mln | percentage  |
|-------------|------------------|-------------|
| Retailer    | 1219.08          | 0.73233983  |
| Direct      | 257.53           | 0.15470739  |
| Distributor | 188.03           | 0.11295278  |

</details>






<details>
  <summary><b>Question 10</b></summary>

### Question 10
Identify the top 3 products by total quantity sold within each product division for fiscal year 2021. The final output should include the following fields:
* product_code
* division
* product
* variant
* total_sold_quantity
* rank_order

### SQL Code
```sql
WITH
    total_sold_qty_by_division AS
    (
        SELECT
            s.product_code,
            p.division,
            p.product,
            p.variant,
            SUM(s.sold_quantity) AS total_sold_quantity,
            DENSE_RANK() OVER(PARTITION BY division ORDER BY SUM(s.sold_quantity) DESC) AS rank_order
        FROM
            gdb023.fact_sales_monthly s
        INNER JOIN
            gdb023.dim_product p
            ON s.product_code = p.product_code
        WHERE
            s.fiscal_year = 2021
        GROUP BY
            s.product_code,
            p.division,
            p.product,
            p.variant
    )
SELECT
    ts.division,
    ts.product_code,
    ts.product,
    ts.variant,
    ts.total_sold_quantity,
    ts.rank_order
FROM
    total_sold_qty_by_division ts
WHERE
    ts.rank_order <= 3
ORDER BY
    ts.division, ts.rank_order ASC
;
```

### SQL Output
| division | product_code   | product         | variant              | total_sold_quantity | rank_order |
|----------|----------------|-----------------|-----------------------|---------------------|------------|
| N & S    | A6720160103    | AQ Pen Drive 2 IN 1 | Premium           | 701373              | 1          |
| N & S    | A6818160202    | AQ Pen Drive DRC    | Plus              | 688003              | 2          |
| N & S    | A6819160203    | AQ Pen Drive DRC    | Premium           | 676245              | 3          |
| P & A    | A2319150302    | AQ Gamers Ms        | Standard 2        | 428498              | 1          |
| P & A    | A2520150501    | AQ Maxima Ms        | Standard 1        | 419865              | 2          |
| P & A    | A2520150504    | AQ Maxima Ms        | Plus 2            | 419471              | 3          |
| PC       | A4218110202    | AQ Digit            | Standard Blue     | 17434               | 1          |
| PC       | A4319110306    | AQ Velocity         | Plus Red          | 17280               | 2          |
| PC       | A4218110208    | AQ Digit            | Premium Misty Green | 17275            | 3          |

</details>

