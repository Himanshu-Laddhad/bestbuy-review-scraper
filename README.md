# HW4 – Best Buy Product Review Scraper

**Course:** MGTA 590 – Web Data Analytics | Purdue University
**Skills:** Python · urllib · Regex · HTML Parsing · Web Scraping · CSV Export

---

## Overview

This project scrapes customer reviews from Best Buy product pages using Python's `urllib` library and regular expressions — without any third-party scraping framework. It handles compressed HTTP responses, constructs paginated review URLs dynamically, extracts reviewer names and review text from raw HTML, and exports the data to structured CSV files.

Two Apple iPhone models are scraped across the assignment's two questions, demonstrating the scraper's generalizability.

---

## What It Does

1. **Sends HTTP requests** with realistic browser headers (User-Agent, Accept-Encoding, Referer, etc.) to avoid basic bot detection
2. **Handles gzip-compressed responses** transparently using Python's `gzip` module
3. **Detects total review count** by parsing the `results-summary` div with regex
4. **Generates paginated review URLs** automatically (20 reviews/page)
5. **Extracts reviewer names and review text** from raw HTML using `str.find()` and regex
6. **Sanitizes fields** for safe CSV output (escaping commas, quotes, and newlines)
7. **Exports results** to `first_question.csv` and `second_question.csv`

---

## Files

| File | Description |
|---|---|
| `laddhad_himanshu_hw4.ipynb` | Main notebook with full scraper and explanations |
| `first_question.csv` | Scraped reviews for iPhone 14 Pro Max (Verizon, 128GB) |
| `second_question.csv` | Scraped reviews for iPhone 16 Pro Max (AT&T, 256GB) |

---

## Products Scraped

| Question | Product | SKU |
|---|---|---|
| Q1 | Apple iPhone 14 Pro Max 128GB Deep Purple (Verizon) | 6487406 |
| Q2 | Apple iPhone 16 Pro Max 256GB Black Titanium (AT&T) | (extracted from URL) |

---

## Output Schema

```
Product name, Review_username, Review_Content
apple-iphone-14-pro-max-..., NJuice, "I am not going to get into the thick of it..."
```

---

## Key Concepts Demonstrated

| Concept | Description |
|---|---|
| Custom HTTP headers | Mimicking a real browser to bypass basic restrictions |
| Gzip decompression | Handling `Content-Encoding: gzip` responses |
| Regex (`re` module) | Extracting structured data from HTML strings |
| String parsing (`str.find()`) | Navigating HTML without a full parser |
| Pagination logic | Auto-generating page URLs from total review count |
| CSV sanitization | Properly escaping fields for valid CSV output |

---

## Tech Stack

- **Language:** Python 3
- **Environment:** Jupyter Notebook
- **Libraries:** `urllib.request`, `re`, `gzip` (all standard library)

---

## How to Run

1. Open `laddhad_himanshu_hw4.ipynb` in Jupyter.
2. Run all cells (`Kernel → Restart & Run All`).
3. `first_question.csv` and `second_question.csv` will be written to the working directory.

> **Note:** Best Buy's HTML structure may change over time. If the scraper fails to extract reviews, the page structure may have been updated since this code was written.

---

## Ethical Scraping Note

All requests include a `Referer: https://www.google.com/` header and a realistic User-Agent string. The scraper does not bypass login walls, CAPTCHAs, or any rate limiting. Please review [Best Buy's Terms of Service](https://www.bestbuy.com/site/help/terms-conditions/pcmcat204400050067.c) before running.
