---
layout: default
title: ~
category: trade
tags: [trade]

---

![image](https://github.com/user-attachments/assets/4d191553-0f25-41f1-8e16-4919000e20f9)

![image](https://github.com/user-attachments/assets/153412e4-e4b4-4c52-82ae-897b1d526c2a)

- Make sure you comply with Nepal's laws and Merolagani's terms & conditions. Automated trading may violate Merolagani’s Terms of Service. Always check with platform administrators before proceeding.
plus GUI changes may make automation not work 

login merolaganiDOTcom w G

see how manual trading works, where price data is displayed, and how orders are placed.
- **Identify Automatable Actions**: Note any restrictions (like CAPTCHAs, OTPs, manual verifications).

then, Define Your Trading Logic

https://gist.github.com/AWScommunity/3391060fd97504427dd8fa74f951dd5c.js

<img width="582" height="467" alt="image" src="https://github.com/user-attachments/assets/bc476559-c708-427e-b326-cee67f3ce3a9" />

then

ask (+977) 01-5315101/5315184 If an API is available: Get access (document tokens, endpoints).

If not, Web Scraping (Most Likely)
- **Python libraries**: Use `requests` and `BeautifulSoup` to collect data.
- **Headless browser**: Use `Selenium` or `Playwright` for interactive/dynamic content.

**Example (Scraping)**:
```python
import requests
from bs4 import BeautifulSoup

url = 'https://merolagani.com/LatestMarket.aspx'
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')
# Parse tables for stock prices
```

Then, Build AI Agent

- **Model**: Train (or use a pre-built) ML model for trading signals.
- **Implementation**: Use `Python` (`scikit-learn`, `Tensorflow`, `PyTorch`) or rule-based bots.
- **Backtest**: Run your agent on historical Merolagani data.

---

Then, Automate Order Placement

#### If Merolagani Has API:
- Use API endpoints to place orders programmatically.

#### If NO API (most likely):
- Use browser automation (`Selenium`, `Playwright`) to fill out forms and submit orders.

**Selenium Example:**
```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get('https://merolagani.com/')

# Log in
username_input = driver.find_element('id', 'UserName')
password_input = driver.find_element('id', 'Password')
username_input.send_keys('your_username')
password_input.send_keys('your_password')
driver.find_element('id', 'btnLogin').click()

# Navigate to trading section and place order
# ... (identify the correct button/fields using driver.find_element())
```

---

Then,

- **Monitor trades**: Log every decision and result.
- **Error handling**: If trade fails, send notification/email.
- **Exit strategies**: Include safety stops and checks.

Then,

- **Server/Cloud**: Run on a VPS or local machine (with always-on internet).
- **Scheduler**: Use `cron` (Linux) or Task Scheduler (Windows) for periodic tasks.
- **Security**: Encrypt credentials. Do NOT share login information!

---

- **CAPTCHA/OTP**: Orders may be blocked by security checks.
- **Logging**: Log every action for audit and debugging.

Then,
Review performance regularly n Improvise Strategies

