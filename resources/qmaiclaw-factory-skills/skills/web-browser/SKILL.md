# Web Browser

**Source**: Custom workspace skill

Control web browser programmatically for scraping, testing, and automation.

## Playwright (Recommended)

```bash
# Install
npm install playwright
npx playwright install chromium

# Basic usage
node -e "
const { chromium } = require('playwright');
(async () => {
  const browser = await chromium.launch();
  const page = await browser.newPage();
  await page.goto('https://example.com');
  const content = await page.content();
  console.log(content);
  await browser.close();
})();
"
```

## puppeteer

```bash
# Install
npm install puppeteer

# Basic usage
node -e "
const puppeteer = require('puppeteer');
(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.goto('https://example.com');
  const content = await page.content();
  console.log(content);
  await browser.close();
})();
"
```

## Selenium

```bash
# Install
pip install selenium
# Download chromedriver

# Basic usage
from selenium import webdriver
driver = webdriver.Chrome()
driver.get('https://example.com')
print(driver.page_source)
driver.quit()
```

## curl (For Simple Pages)

```bash
# GET request
curl https://example.com

# With headers
curl -H "User-Agent: Mozilla/5.0" https://example.com

# POST request
curl -X POST -d "key=value" https://example.com

# Follow redirects
curl -L https://example.com

# Save to file
curl -o output.html https://example.com
```

## wget (Download files)

```bash
# Download page
wget https://example.com

# Download recursively
wget -r https://example.com

# Quiet mode
wget -q https://example.com

# Specify output
wget -O output.html https://example.com
```

## Tips

- Use `--headless` for browser automation without GUI
- Set `viewport` for responsive testing
- Use `waitForSelector` to wait for elements
- Set `userAgent` to mimic real browser

---

*Install date: 2026-04-27*
