# Analyzing-Customer-Orders-Using-Python-Data-Structures
This project demonstrates how Python data structures can effectively process and analyse customer order  data. Using lists, tuples, dictionaries, and sets combined with loops and conditionals enables meaningful  customer segmentation and product analysis. 

PYTHON CODE: 
 
# 1. Create a list of customer names 
customer_names = ['Amit', 'Bansi', 'Chiru', 'David', 'Evandro', 'Felix'] 
 
# 2. Store order details as tuples inside a list 
# Format: (Customer Name, Product, Price, Category) 
order_details = [ 
    ('Amit', 'Laptop', 1200, 'Electronics'), 
    ('Amit', 'Mouse', 25, 'Electronics'), 
    ('Bansi', 'T-Shirt', 20, 'Clothing'), 
    ('Bansi', 'Jeans', 45, 'Clothing'), 
    ('Bansi', 'Headphones', 50, 'Electronics'), 
    ('Chiru', 'Smartphone', 800, 'Electronics'), 
    ('David', 'Coffee Maker', 80, 'Home Essentials'), 
    ('Evandro', 'Book', 15, 'Books'), 
    ('Evandro', 'Pen', 5, 'Stationery'), 
    ('Felix', 'Monitor', 150, 'Electronics'), 
    ('Felix', 'T-Shirt', 20, 'Clothing') 
] 
 
# 3. Use a dictionary where keys are names and values are lists of products 
customer_orders_dict = {} 
for name, product, price, category in order_details: 
    if name not in customer_orders_dict: 
        customer_orders_dict[name] = [] 
    customer_orders_dict[name].append(product) 
 
# 4. Dictionary mapping product to category 
product_category_map = {product: category for name, product, price, category in order_details} 
 
# 5. Set of unique product categories 
unique_categories = set(category for name, product, price, category in order_details) 
print("--- Available Products ---") 
print(unique_categories) 
print("\n") 
 
#6. analyze customer data 
customer_spending = {} 
customer_classes = {} 
 
# 7. Calculate total spending per customer 
for name, product, price, category in order_details: 
    if name in customer_spending: 
        customer_spending[name] += price 
    else: 
        customer_spending[name] = price 
 
# 8. Classify customers based on spending 
for name, total in customer_spending.items(): 
    if total > 100: 
customer_classes[name] = 'High-Value' 
elif 50 <= total <= 100: 
customer_classes[name] = 'Moderate' 
else: 
customer_classes[name] = 'Low-Value' 
# 9. Total revenue per product category 
category_revenue = {} 
for name, product, price, category in order_details: 
category_revenue[category] = category_revenue.get(category, 0) + price 
# 10. Unique products set 
unique_products = set(product for name, product, price, category in order_details) 
# 11. List comprehension: Customers who purchased Electronics 
# We look at order_details to find names where category is 'Electronics' 
electronics_buyers = list(set([name for name, product, price, category in order_details if category == 
'Electronics'])) 
# 12. Top 3 highest-spending customers (Sorting) 
# sorted() returns a list of tuples (key, value), we sort by value (x[1]) in descending order 
top_spenders = sorted(customer_spending.items(), key=lambda x: x[1], reverse=True)[:3] 
# 13. Organize and display data for reports 
print("--- Customer Spending & Classification ---") 
print(f"{'Customer':<10} | {'Total Spend':<12} | {'Class':<10}") 
print("-" * 40) 
for name, total in customer_spending.items(): 
print(f"{name:<10} | ${total:<11} | {customer_classes[name]}") 
print("\n") 
print("--- Category Revenue ---") 
for category, revenue in category_revenue.items(): 
print(f"{category}: ${revenue}") 
print("\n") 
print("--- Top 3 High-Value Customers ---") 
for i, (name, spend) in enumerate(top_spenders, 1): 
print(f"{i}. {name} (${spend})") 
print("\n") 
# 14. Multiple product purchasing customers 
multi_category_buyers = [] 
for name in customer_names: 
# Get all categories this specific customer bought from 
customer_cats = {category for n, p, pr, category in order_details if n == name} 
if len(customer_cats) > 1: 
multi_category_buyers.append(name) 
# 15. Customers who bought both Electronics and Clothing 
# Identify buyers for each category first 
electronics_set = {name for name, prod, price, cat in order_details if cat == 'Electronics'} 
clothing_set = {name for name, prod, price, cat in order_details if cat == 'Clothing'} 
# 16. Intersection 
both_cat_buyers = electronics_set.intersection(clothing_set) 
print("--- Advanced Insights ---") 
print(f"Customers buying from multiple categories: {multi_category_buyers}") 
print(f"Customers who bought both Electronics & Clothing: {both_cat_buyers}") 
OUTPUT:
