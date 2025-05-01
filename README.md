# Task7

Imported SQLITE3, Pandas, Matplotlib, Seanborn

Created database sales db

Created sales table 

Inserted data into table.

conn = sqlite3.connect('sales.db')
query = "select * from Sales"
df = pd.read_sql(query,conn)
df.head()

=To select all data from sales table

conn = sqlite3.connect('sales.db')
query = f"""
    SELECT id, name, state, amount
    FROM sales
    ORDER BY amount DESC
    LIMIT {2}
    """
df = pd.read_sql(query,conn)
df.head()

=To select top 2 id, name, state, amount from sales.

Top 1 customer is John Smith from Texas which has total amount of sales 92.30
Top 2 customer is Jane doe from california which has total amount of sales 85.43

query = "SELECT name, SUM(amount) AS total_amount FROM sales GROUP BY name"
df_sales = pd.read_sql(query, conn)

plt.figure(figsize=(8, 5))
sns.barplot(x="name", y="total_amount", data=df_sales)
plt.xticks(rotation=45)
plt.xlabel("Name")
plt.ylabel("Total Amount")
plt.title("Total Sales Amount by Name")
plt.tight_layout()
plt.show()

= To find Total sales amount by name
John Smith 

query = "SELECT state, SUM(amount) AS total_amount FROM sales GROUP BY state"
df_sales = pd.read_sql(query, conn)

plt.figure(figsize=(8, 5))
sns.barplot(x="state", y="total_amount", data=df_sales)
plt.xticks(rotation=45)
plt.xlabel("State")
plt.ylabel("Total Amount")
plt.title("Total Sales Amount by State")
plt.tight_layout()
plt.show()

= To find Total sales amount by state
Texas
