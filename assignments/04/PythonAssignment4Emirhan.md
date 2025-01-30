## Parsing product orders with Python

In this directory, you will find another file called `csv/orders.csv` and also a short Python script that reads the file and parses all numbers with a regular expression. Please extend the script such that it also print the following extracted text pieces.

1. Extract all order numbers from the text.

   ```python
   order_numbers = re.findall(r"Order #(\d+)", " ".join(data))
   ```

2. Extract all product names.

   ```python
   products = re.findall(r"Product: ([\w\s]+)\t", " ".join(data))
   ```

3. Extract all prices.

   ```python
   prices = re.findall(r"Price: \$(\d+\.\d{2})", " ".join(data))
   prices = [float(price) for price in prices]
   ```

4. Extract all order dates.

   ```python
   dates = re.findall(r"Date: (\d{4}-\d{2}-\d{2})", " ".join(data))
   ```

5. Find all orders for products priced over $500. (You are allowed to use Python to filter the list.)

   ```python
   high_price_orders = [f"Order #{order_numbers[i]}: {products[i]} - ${prices[i]}" for i in range(len(prices)) if prices[i] > 500]
   ```

6. Change the date format to DD/MM/YYYY. (Note the re.sub() method)

   ```python
   formatted_dates = [re.sub(r"(\d{4})-(\d{2})-(\d{2})", r"\3/\2/\1", date) for date in dates]
   ```

7. Extract product names that have more than 6 characters.

   ```python
   long_product_names = [product for product in products if len(product) > 6]
   ```

8. Count the occurrence of each product in the text. (You may want to use the Counter class from the collections package.)

   ```python
   product_counts = Counter(products)
   ```

9. Extract the orders with prices ending in .99.

   ```python
   orders_with_99 = [f"Order #{order_numbers[i]}: {products[i]} - ${prices[i]}" for i in range(len(prices)) if str(prices[i]).endswith(".99")]
   ```

10. Find the cheapest product. (You may want to use Python's min() method.)

   ```python
   cheapest_index = prices.index(min(prices))
   cheapest_product = f"Order #{order_numbers[cheapest_index]}: {products[cheapest_index]} - ${prices[cheapest_index]}"
   ```
