# Automated-web-data-scraper
This project is a **Web Scraping & Data Extraction Tool** built with Python. It demonstrates how to programmatically navigate a website, extract specific data points, and transform unstructured HTML into a structured CSV dataset.

---

## 🚀 Key Features

* **HTTP Request Handling:** Uses the `requests` library with custom headers to simulate real browser behavior and handle connection timeouts.
* **HTML Parsing:** Leverages **BeautifulSoup4** to traverse the DOM and target specific CSS classes and tags.
* **Defensive Programming:** Features robust error handling and "NoneType" safety checks to ensure the scraper doesn't crash if a specific piece of data (like a price or title) is missing from a page.
* **Persistent Data Storage:** Automatically generates a `book_data.csv` file. If the file already exists, it intelligently appends new data rather than overwriting.
* **Temporal Tracking:** Every record is saved with a high-resolution **timestamp**, allowing for price tracking and data auditing over time.

---

## 🛠️ Project Architecture

The script follows a linear data pipeline that moves data from the web to a local storage format.

1. **Request:** The script sends an HTTP GET request to the target URL.
2. **Parse:** The raw HTML content is converted into a searchable BeautifulSoup object.
3. **Extract:** A loop identifies all "product pods" and pulls the Title, Price, and Availability.
4. **Format:** The data is cleaned (stripped of whitespace) and paired with a timestamp.
5. **Save:** The `csv` module handles the writing process, including headers for new files.

---

## 💻 Technical Highlights

* **BeautifulSoup Locators:** Uses `.find()` and `.find_all()` to isolate specific elements like `<article class="product_pod">`.
* **Exception Management:** Implements `try-except` blocks for both Network errors (e.g., 404 or Timeout) and File system errors (e.g., Permission denied when a CSV is open in Excel).
* **OS Integration:** Uses the `os` module to check for file existence, ensuring CSV headers are only written once.
* **User-Agent Spoofing:** Includes a `User-Agent` header to prevent basic bot-blocking mechanisms.

---

## 📖 How to Run

1. **Install Dependencies:**
```bash
pip install requests beautifulsoup4

```


2. **Run the Scraper:**
```bash
python scraper.py

```


3. **Check Results:** Open `book_data.csv` in any spreadsheet software to see your scraped data.

---

* Scraping multiple pages (Pagination)?
* Downloading book cover images?
* Filtering books by price range?
* Sending an email alert when a price drops?

What functionality should we build in next?
