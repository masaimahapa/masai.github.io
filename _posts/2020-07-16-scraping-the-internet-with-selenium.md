---
title: "Scraping the web using Selenium"
date: 2020-07-16
tags: [data science]
header:
    image: "/images/selenium/scrape.png"
excerpt: "web scraping, data mining, data science"
---

# Scraping the internet with Selenium
A vast majority of the world’s data today is found on the internet. It comes in all sorts of different forms, shapes and sizes available for you to use. Web scraping is like a super power which allows us to get a wealth of data into our hands.

Sometimes, when web pages are dynamically loaded it gets really tricky to scrape websites. For this very reason, Selenium, which automates tasks in the browser can work around this problem with ease compared to other tools like [scrapy](https://scrapy.org/).

### Why scrape?
For the longest time, I thought web scraping was not so important to learn. I can just simply get an API (Application Programming Interface), and pull data in a structured format. Well at least that is what I had though. In reality, things are not so perfect.

Recently, I started working at a lighting reseller here in Johannesburg. Most of the data is captured manually from the web pages of suppliers into excel files which takes forever to get done considering the fact that each supplier has hundreds and even thousands of products on their website. After a day, I quickly realized that my data science Python chops would come in handy in order to automate the boring stuff.

So I quickly learnt how to use Scrapy, which is an amazing python Library for scraping data off of the web. It was intimidating at first, but what was more intimidating to me was spending my life away entering information manually into an excel sheet, one by one, only to be told I made many mistakes typing in the product ID of the 784th product.

I quickly hit a wall. The website I was trying to scrape is dynamically loaded, so the HTML content is created by Javascript as you load/scroll through the page. Web scraping winter had arrived sooner than I thought. Since I am a highly qualified professional Googler, I came to the realization that I can use a different tool to overcome this problem. Selenium.

[Selenium](https://www.selenium.dev/) is a browser task automation tool which is used to test web apps, so it does what a human would do. You can use it to fill in forms, click on buttons, etc. So luckily it was not too hard to make the switch as the XPath and CSS selectors I had learnt earlier are still applicable.

After a few minutes of the code running, I had completed my first scrape of a website scoring over a thousand items as well as their specs into an excel sheet. 

### How to get started
You firstly need to get a chromedriver. This is what will allow you to do stuff automatically in the browser. Find a compatible one for your version of [chrome here.](https://chromedriver.chromium.org/downloads)

```python
    from selenium import webdriver
    
    driver = webdriver.Chrome('/path/to/the/chromedriver')
    driver.get('https://klight.co.za/products/all')

```

![KLight screenshot](/images/selenium/klight-all.png)
![KLight screenshot](/assets/img/klight.png)

<img src="/assets/img/klight.png" alt="">

Once you have landed on a page, you can now find text, links and images by their id, HTML tag names (e.g p, h1, li), using a [css selector ](https://www.w3schools.com/cssref/css_selectors.asp), etc.

```python
    categories= driver.find_elements_by_css_selector('div.category-tile h5')
    
    for cat in categories:
    print(cat.text)

```
Output:
```
CRYSTAL CHANDELIERS, CHANDELIERS & PENDANTS, LED FITTINGS, METAL PENDANTS, METAL WIRE PENDANTS,  GLASS PENDANTS , MIXED MEDIA PENDANTS, COMMERCIAL PENDANTS AND SPOT LIGHTS, FLUORESCENT FITTINGS, READING WALL LIGHTS, DECORATIVE WALL LIGHTS, BATHROOM AND MIRROR LIGHTS, 
FLOOR LAMPS, TABLE LAMPS, LED & DECORATIVE BULBS, CEILING FITTINGS, SPOT LIGHTS GU10 & G9, 230V HIGH VOLTAGE,  SPOT LIGHTS, 12V LOW VOLTAGE, TRACK SPOT LIGHTS LED & GU10, SURFACE MOUNTED 12V OR 230V LED & GU10, DOWN LIGHTS LED, DOWN LIGHTS GU10, 230V HIGH VOLTAGE, DOWN LIGHTS, 12V LOW VOLTAGE, DOWN LIGHTS, METAL HALIDES, DOWN LIGHTS, COMPACT FLUORESCENT, LED GARDEN AND OUTDOOR LIGHTS, GARDEN AND OUTDOOR LIGHTS, LED STRIP LIGHTS 230V & 12V, POWER SUPPLIES & ACCESSORIES, LED ALUMINIUM PROFILES, LED DRIVERS, LUXMAN TRANSFORMER & ACCESSORIES
ELECTRICAL CABLES, END OF RANGE SPECIAL
```

That's it. You now have all the categories on this website and can choose what to do from here such as go to products and get their specs. I will make a blog post of how to crawl around the web and store the information soon and share my experience, the challanges I faced and how I overcame them.

## Conclusion
My current job has really taught me that there is a lot of low hanging fruit in the world. I am learning to think about how best to solve problems and not how best a problem can be solved with machine learning.

I hope this is able to get you fired up to learn web scraping to get data from the world wide web. Afterall, what is a data scientist without data?
