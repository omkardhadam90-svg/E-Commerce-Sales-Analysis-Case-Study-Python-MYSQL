# E-Commerce Sales Analysis — Case Study  
### Turning Sales Data Into Smarter Decisions for Growth    
**Tech Stack:** Python, MySQL

---

## Project Overview  
This project analyzes sales performance for an Indian fashion retailer selling on Amazon.in.  
The company is facing **high cancellations**, **delivery delays**, and **fulfillment issues**.

The goal of this case study is to uncover insights using, 
**Python** for data cleaning and **MySQL** for business analysis. <br>
<br>
This project answers crucial business questions such as:

- Why are cancellations increasing?
- Is **Amazon Fulfillment** or **Merchant Fulfillment** performing better?
- Which products bring the highest revenue?
- Which states/cities should get more marketing investment?
- Does expedited shipping really improve delivery success?


The project provides recommendations for improving sales, reducing cancellations, and optimizing fulfillment.

---

## Dataset Description
| Column | Description |
|--------|-------------|
| Order ID | Unique order number |
| Date | Order date |
| Status | Shipped / Cancelled / Delivered |
| Fulfillment | Amazon / Merchant |
| Sales Channel | Amazon.in |
| ship-service-level | Standard / Expedited |
| Style | Product style code |
| Category | Set, Kurta, Western Dress, Top |
| Size | XS–6XL |
| Courier Status | Shipping status |
| Qty | Quantity (0 for cancelled orders) |
| Amount | Order value |
| ship-city | Customer city |
| ship-state | Customer state |

---

## Data Cleaning & Preprocessing (Python)
Performed using **pandas**, **NumPy**, and **matplotlib**:

- Fixed incorrect datatypes  
- Removed duplicates  
- Handled null values  
- Detected outliers using boxplots  
- Corrected inconsistent formatting  
- Cleaned categorical columns  
- Exported cleaned dataset to MySQL



---

##  Business Analysis Using SQL

##  **1. Sales Overview**
###  Total revenue generated from successfully completed orders (exclude cancelled orders).
#### -> select sum(Amount) as Revenue_by_Completed_Orders from sales
####    where Status="Delivered";  

### What is the overall cancellation rate? Calculate both by order count and by revenue value.

#### Cancelation rate by Order Count :- 
#### -> select round(count(Order_ID)/(select count(Order_ID) from sales)*100,2) as Cancellation_rate_By_Order_count from sales 
#### where Status="Cancelled";

#### Cancelation rate by Revenue:- 
#### -> select round(sum(Amount)/(select sum(Amount) from sales)*100,2) as Cancellation_rate_By_Revenue from sales 
#### where Status="cancelled";
---

###  **2. Fulfillment Analysis (Amazon vs Merchant)**  
- Merchant Fulfillment has **higher successful deliveries**  
- Amazon Fulfillment has **0 delivered orders** → all remain "Shipped / Transit / Pending"  
- High pending time leads directly to cancellations  

📌 **Conclusion:**  
Merchant Fulfillment is better today,  
but Amazon Fulfillment has a *higher volume and higher future potential* **if delivery issues are fixed**.

---

### ✔ **3. Product Performance Analysis**
- **Top Revenue Categories (Merchant Fulfillment):**  
  - Set — **₹88,00,562 (47%)**  
  - Kurta — **₹47,15,208 (25.3%)**  
  - Western Dress — **₹38,67,845 (20.7%)**

- Top 5 best-selling styles  
- Category cancellation analysis  
- Average selling price per category  
- Size distribution analysis  

---

### ✔ **4. Regional Analysis**
- Maharashtra, Karnataka, and Tamil Nadu are top-performing states  
- Top revenue cities identified  
- State-wise cancellation rate analyzed  
- Top 5 city–category revenue combinations  

---

### ✔ **5. Shipping Service Level Analysis**
- Standard Shipping → all successful completions  
- Expedited Shipping → **0 delivered orders**  
- Expedited service currently unreliable  

📌 **Conclusion:**  
Standard shipping is the only stable method as of now.  
Expedited service requires operational fixes.

---

## 🧠 Key Insights

### 🔥 1. High Cancellation Rate  
Mainly due to:
- Long pending times  
- Slow shipping in Amazon Fulfillment  
- Zero successful expedited deliveries  

---

### 🔥 2. Merchant Fulfillment is currently stronger  
Due to higher delivery completion and lower cancellations.

---

### 🔥 3. Product Categories
**Set** and **Kurta** are the top-performing categories and should be prioritized for restocking.

---

### 🔥 4. Regions for Growth  
States with the highest active buyers:
- Maharashtra  
- Karnataka  
- Tamil Nadu  

These states should receive additional marketing investment.

---

## 🛠️ Business Recommendations

### 1️⃣ Improve Amazon Fulfillment Delivery  
- Address delays  
- Increase processing speed  
- Reduce pending time  
- This will lower cancellations drastically  

### 2️⃣ Increase Marketing Spend in Top 3 States  
- Maharashtra  
- Karnataka  
- Tamil Nadu  

### 3️⃣ Expand Inventory for High-Demand Categories  
- Set  
- Kurta  

### 4️⃣ Reduce Cancellation Rate  
- Ensure timely dispatch  
- Monitor orders stuck in transit  
- Improve shipping workflow  

---

## ▶️ How to Run This Project

### **1. Clone the project**
```sh
git clone https://github.com/yourusername/ecommerce-sales-analysis-case-study.git
cd ecommerce-sales-analysis-case-study


 
