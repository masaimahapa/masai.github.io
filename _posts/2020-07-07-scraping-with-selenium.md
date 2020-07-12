---
title: "Scraping the web using Selenium"
date: 2020-07-07
tags: [data science]
header:
    image: "/images/selenium/scrape.png"
excerpt: "web scraping, data mining, data science"
---

# Web scraping with Selenium
Sometimes, when web pages are dynamically loaded it gets really tricky to scrape websites. For this very reason, Selenium, which automates tasks in the browser can work around this problem with ease.

### Why scrape?
Initially, you may wonder where is the value in scraping. This will become very clear when you need to get data and there are no APIs available.

Whats a data scientist without data? LOL, A scientist.

```python
    import selenium
    from selenium.driver import driver

    driver.get('github.com/some_page')
```
## Conclusion
Learn to scrape