# Job Posting Web Scraper

An automated web scraping tool that extracts job posting information from job board websites using Python and Beautiful Soup. This scraper collects job titles, company names, locations, and descriptions, storing them in a structured CSV format.

---

## 👨‍💻 Developer

Bislan Pisaev

---

## 📋 Project Overview

This Python-based web scraper automates the collection of job posting data from various job board websites. It parses HTML content, extracts relevant information, and stores it in a structured format for easy analysis and job searching.

---

## 🚀 Features

- **Automated Data Extraction:** Scrapes job titles, company names, locations, and descriptions
- **Multi-Page Support:** Handles pagination to collect data from multiple pages
- **Data Storage:** Saves extracted information to CSV files
- **Rate Limiting:** Implements request throttling to avoid server overload
- **Reusable Functions:** Modular design for easy customization
- **Error Handling:** Robust error management for reliable scraping
- **Testing Suite:** Comprehensive unit tests included

---

## 🛠️ Technologies Used

- **Python 3.x**
- **Beautiful Soup 4:** HTML parsing and web scraping
- **Requests:** HTTP library for making web requests
- **CSV:** Data storage and export
- **Pytest:** Testing framework

---

## 📂 Project Structure
```
JobWebScrapper/
├── src/
│   ├── __init__.py
│   ├── app.py              # Main application entry point
│   ├── models.py           # Data models for job postings
│   └── scraper.py          # Core scraping logic
├── tests/
│   ├── __init__.py
│   ├── test_scraper.py     # Unit tests for scraper
│   └── test_materials/     # Test fixtures and data
├── pyproject.toml          # Project dependencies (Poetry)
├── poetry.lock             # Locked dependency versions
├── Makefile               # Build and task automation
├── .pylintrc              # Python linting configuration
├── Task.md                # Project requirements
└── README.md              # Project documentation
```

---

## ⚙️ Installation

### Prerequisites

- Python 3.8 or higher
- pip or Poetry package manager

### Setup

**1. Clone the repository**
```bash
git clone https://github.com/pisaevv/JobWebScrapper.git
cd JobWebScrapper
```

**2. Install dependencies**

Using Poetry (recommended):
```bash
poetry install
```

Or using pip:
```bash
pip install beautifulsoup4 requests pytest
```

---

## 💻 Usage

### Basic Usage
```python
from src.scraper import scrape_jobs

# Scrape jobs from a job board URL
jobs = scrape_jobs('https://example-job-board.com/jobs')

# Data is automatically saved to CSV
```

### Running the Application
```bash
python src/app.py
```

### Running Tests
```bash
pytest tests/
```

Or using Make:
```bash
make test
```

---

## 📊 Output Format

The scraper exports data to CSV with the following structure:

| Job Title | Company Name | Location | Description |
|-----------|-------------|----------|-------------|
| Software Engineer | Tech Corp | New York, NY | Full job description... |
| Data Analyst | DataCo | Remote | Full job description... |

---

## 🔧 Configuration

### Target Website

Modify the target URL in `src/scraper.py`:
```python
TARGET_URL = 'https://your-job-board.com/jobs'
```

### Rate Limiting

Adjust request delays to respect server resources:
```python
import time
time.sleep(2)  # Wait 2 seconds between requests
```

### Page Limit

Set maximum number of pages to scrape:
```python
MAX_PAGES = 10
```

---

## 🎯 Key Features Explained

### Multi-Page Scraping

The scraper automatically detects and follows pagination:
```python
def scrape_multiple_pages(base_url, max_pages=5):
    for page in range(1, max_pages + 1):
        url = f"{base_url}?page={page}"
        # Scrape each page
```

### HTML Parsing

Identifies and extracts specific HTML elements:
```python
job_title = soup.find('h2', class_='job-title').text
company = soup.find('span', class_='company-name').text
location = soup.find('div', class_='location').text
```

### Data Models

Structured data representation using Python classes:
```python
class Job:
    def __init__(self, title, company, location, description):
        self.title = title
        self.company = company
        self.location = location
        self.description = description
```

---

## 🧪 Testing

Run the test suite:
```bash
pytest tests/ -v
```

Test coverage includes:
- HTML parsing accuracy
- Data extraction validation
- Error handling scenarios
- Multi-page navigation

---

## 📝 Requirements (from Task.md)

This project fulfills the following requirements:

✅ Beautiful Soup library integration  
✅ Target job board website configuration  
✅ HTML element identification and extraction  
✅ Python script for parsing and data extraction  
✅ CSV-based data storage mechanism  
✅ Structured data organization  
✅ Reusable function architecture  
✅ Multi-page scraping capability  
✅ Request rate limiting  

---

## 🐛 Troubleshooting

**Issue: Module not found**
```bash
pip install beautifulsoup4 requests
```

**Issue: Scraper not finding elements**
- Inspect the target website's HTML structure
- Update CSS selectors in `scraper.py`

**Issue: Rate limiting errors**
- Increase delay between requests
- Check website's robots.txt for scraping policies

---

## 🚀 Future Enhancements

- [ ] Add support for multiple job board websites
- [ ] Implement database storage (PostgreSQL/MongoDB)
- [ ] Create web UI for viewing scraped data
- [ ] Add email notifications for new job postings
- [ ] Implement advanced filtering options
- [ ] Add export to JSON/Excel formats

---

## ⚖️ Legal & Ethical Considerations

**Important:** Always check the website's `robots.txt` and Terms of Service before scraping. This tool is for educational purposes. Use responsibly and respect rate limits.

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 🙏 Acknowledgments

- Beautiful Soup documentation
- Python web scraping community
- Job board websites for publicly available data

---

*Built for automated job search and market analysis*
