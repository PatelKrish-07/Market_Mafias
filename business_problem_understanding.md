# Business Problem Understanding

Here is a simple breakdown of the business rules and how they relate directly to our dataset.

**1. Who is the customer?**
Anyone with a `CustomerID` in our data. Because some customers buy massive quantities of items, we are likely dealing with both everyday shoppers and wholesale businesses.

**2. What counts as a valid purchase?**
A real, completed order. In the data, this means:

* `Quantity` is greater than 0.

* `UnitPrice` is greater than 0.

* `CustomerID` is not blank (we need to know who bought it).

**3. How should cancellations be treated?**
We do not delete them! Cancellations (where `InvoiceNo` starts with 'C' and `Quantity` is negative) are valuable data. We separate them into their own list to calculate return rates and see if certain products are returned often.

**4. What does customer value mean?**
We measure a customer's true value using "RFM":

* **Recency:** How many days since their last `InvoiceDate`?

* **Frequency:** How many unique `InvoiceNo`s do they have?

* **Monetary:** What is the total sum of their `TransactionValue`?

**5. How can marketing use customer segments?**
By grouping customers based on their RFM scores, marketing can send targeted campaigns. For example, they can offer VIP discounts to "High-Value Loyal" customers and "We miss you" coupons to "Inactive" customers.

**6. What information is available before making a recommendation?**
We can only look at what a customer has already bought. We use their past `StockCode` history and look at which products are frequently bought together by other customers to suggest new items.