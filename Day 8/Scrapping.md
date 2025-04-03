# Web Scraping Notes

## 1. Introduction to Web Scraping

Web scraping is the process of extracting data from websites automatically. It involves retrieving web pages and parsing their content to obtain useful information. Web scraping can be done using various programming languages, but Python is one of the most popular choices due to its powerful libraries.

### **1.1 Applications of Web Scraping**

- **Data Collection for Research and Analysis**: Many researchers and data analysts use web scraping to collect vast amounts of data for analysis in fields such as finance, healthcare, and marketing.
- **Price Monitoring and Comparison**: Businesses use web scraping to monitor competitors' prices and adjust their pricing strategies accordingly.
- **News Aggregation**: Websites like Google News aggregate news articles from different sources, which can be done through web scraping.
- **Social Media Sentiment Analysis**: Scraping posts and comments from social media platforms can help analyze public sentiment about brands, products, or political topics.
- **Job Listing Extraction**: Web scraping helps in gathering job listings from multiple websites for job seekers and recruitment agencies.

## 2. Web Scraping Basics

Web pages are built using **HTML**, and data is often structured using tags such as `<div>`, `<p>`, `<table>`, and `<span>`. Scraping involves navigating through these elements and extracting the required information.

### **2.1 Required Tools**

To perform web scraping efficiently, the following tools are commonly used:

- **Python**: A programming language that provides numerous libraries for web scraping.
- **Libraries**:
  - `requests`: Fetches web pages by sending HTTP requests.
  - `BeautifulSoup`: Parses HTML and extracts data in a structured format.
  - `Selenium`: Automates browser actions, making it useful for JavaScript-heavy websites.

### **2.2 Understanding HTML Structure**

Before scraping a webpage, it's important to understand its structure:

1. Open the webpage you want to scrape.
2. Right-click and select **"Inspect"** to open Developer Tools.
3. Use the **Elements tab** to find the HTML tags containing the data you need.
4. Identify unique class names, IDs, or attributes that can help locate specific elements.

## 3. How to Check if a Website Allows Scraping

Before scraping a website, follow these steps to determine if it is allowed:

### **3.1 Check `robots.txt`**

Most websites have a `robots.txt` file that defines which parts of the site can be scraped. Visit:

```
https://example.com/robots.txt
```

Look for **Disallow** directives:

```
User-agent: *
Disallow: /private-data/
```

If a section is disallowed, avoid scraping it.

### **3.2 Review the Website’s Terms of Service**

Some websites explicitly prohibit scraping in their **Terms of Service**. Look for terms mentioning "scraping," "automated access," or "data extraction."

### **3.3 Look for API Access**

Websites like LinkedIn, Twitter, and Facebook provide APIs for structured data access. If an API exists, use it instead of scraping.

### **3.4 Test with an HTTP Request**

Run a simple test request using Python:

```python
import requests
url = "https://example.com"
response = requests.get(url)
print(response.status_code)
```

- **200 OK** → Scraping may be allowed.
- **403 Forbidden / 401 Unauthorized** → Likely restricted.
- **429 Too Many Requests** → Rate limiting is in place.

### **3.5 Observe Bot Detection Measures**

Some websites use **CAPTCHAs, IP blocking, or JavaScript challenges**. If a site frequently redirects or requires login, it likely restricts scraping.

## 4. Web Scraping Tutorial (Using `requests` and `BeautifulSoup`)

### **Step 1: Install Required Libraries**

To begin, install the necessary Python libraries using pip:

```bash
pip install requests beautifulsoup4
```

### **Step 2: Fetch the Web Page**

Use the `requests` library to send an HTTP request to a website and retrieve its content:

```python
import requests
from bs4 import BeautifulSoup

url = "https://example.com"
response = requests.get(url)
print(response.status_code)  # Should print 200 if the request is successful
```

If the response status is `200`, the request was successful. Other status codes (e.g., `404`, `403`) indicate issues like missing pages or restricted access.

### **Step 3: Parse HTML Content**

Once the web page is retrieved, use `BeautifulSoup` to parse its content:

```python
soup = BeautifulSoup(response.text, "html.parser")
print(soup.prettify())  # View the formatted HTML structure
```

This allows you to view the entire HTML content in a structured way.

### **Step 4: Extract Data (Example: Get All Headlines)**

To extract specific data, use `find_all()` to locate elements:

```python
headlines = soup.find_all("h2")  # Extracts all h2 elements
for headline in headlines:
    print(headline.text)
```

This code finds all `<h2>` elements (commonly used for headlines) and prints their text content.

### **Step 5: Handling Dynamic Content (Using Selenium)**

Some websites load data dynamically using JavaScript, which `requests` and `BeautifulSoup` cannot handle. In such cases, Selenium is used:

#### **Installing Selenium**

```bash
pip install selenium
```

#### **Using Selenium to Scrape Dynamic Content**

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

# Set up the WebDriver
browser = webdriver.Chrome()
browser.get("https://example.com")

# Extract dynamic content
elements = browser.find_elements(By.TAG_NAME, "h2")
for el in elements:
    print(el.text)

browser.quit()
```

Selenium opens a real web browser, allowing you to interact with dynamically loaded elements.

## 5. Websites Suitable for Scraping

The following websites allow web scraping:

- **https://books.toscrape.com/** (Bookstore data)
- **https://quotes.toscrape.com/** (Quote collection)
- **https://news.ycombinator.com/** (Tech news)
- **https://www.imdb.com/** (Movie information)
- **https://www.wikipedia.org/** (Encyclopedia content)

## 6. Web Scraping Ethics & Best Practices

Web scraping should be done responsibly. Follow these best practices:

- **Respect robots.txt**: Always check if scraping is allowed.
- **Avoid excessive requests**: Use time delays to prevent getting blocked.
  ```python
  import time
  time.sleep(2)  # Wait for 2 seconds before making the next request
  ```
- **Use headers**: Mimic a real browser to avoid detection.
- **Store data efficiently**: Save data in CSV or JSON format.

---

Happy Scraping! 🚀
