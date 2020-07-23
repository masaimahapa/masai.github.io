---
title: "Scraping the internet using Selenium"
date: 2020-07-23
tags: [data science]
header:
    image: "/images/selenium/scrape.png"
excerpt: "web scraping, data mining, data science"
---

This post is targeted to data scientists and software developers thinking about getting started with web scraping.


A vast majority of the world’s data today is found on the internet. It comes in all sorts of different forms, shapes and sizes available for you to use. Web scraping is like a super power which allows us to get a wealth of data into our hands.

Some websites only show information as you scroll through them or click on buttons, these are known as dynamically loaded websites. It can get really tricky to scrape such websites. For this very reason, Selenium, which automates tasks in the browser can work around this problem with ease compared to other tools like  [scrapy](https://scrapy.org/).

### Why scrape?
For the longest time, I thought web scraping was not so important to learn. I can just simply get an API (Application Programming Interface), and pull data in a structured format. Well at least that is what I had thought. In reality, things are not so perfect.

At one firm I worked for at some point, most of the data is captured manually from the web pages of suppliers into excel files which involves a lot of manual tasks and may take a long time to get done considering the fact that each supplier has hundreds and even thousands of products on their website. After a day, I quickly realized that my data science Python chops would come in handy in order to automate the repetitive tasks.

So I quickly learnt how to use Scrapy, which is an amazing python library for scraping data off of the web. It was intimidating at first, but overcoming this challenge would allow me to be orders of magnitude more efficient, making less errors and affording me more time to study other data science related topics. 

I quickly hit a wall. The website I was trying to scrape is dynamically loaded, so the HTML content is created by Javascript as you load/scroll through the page. Think of everytime you go on Twitter and you see different content each time you log in and as you scroll down your feed. Web scraping winter had arrived sooner than I thought. So after spending some time on StackOverflow, I came to the realization that I can use a different tool to overcome this problem. Selenium.

[Selenium](https://www.selenium.dev/) is a browser task automation tool which is used to test web apps, so it does what a human would do. You can use it to fill in forms, click on buttons, etc. So luckily it was not too hard to make the switch as some of the fundamentals remained the same.

After a few minutes of the code running, I had completed my first scrape of a website scoring over a thousand items as well as their specs into an excel sheet.

### How to get started
For a quick demo, lets get today’s news headlines from the News24 website.

1. You firstly need to get a chromedriver. This is what will allow you to automate tasks in the browser. Find a compatible one for your version of [chrome here.](https://chromedriver.chromium.org/downloads).

2. Install Selenium in your Python environment.

```
    pip install selenium
```


3. Open the web page
```python
    from selenium import webdriver
    
    driver = webdriver.Chrome('/path/to/the/chromedriver')
    driver.get('https://www.news24.com/')

```

news24:
![news24 screenshot](/images/selenium/news24.png)

<img src="/images/selenium/news24.png" alt="">

4. Get what you need
Once you have landed on a page, you can now find text, links and images by their id, HTML tag names (e.g p, h1, li), using a [css selector ](https://www.w3schools.com/cssref/css_selectors.asp), etc.

```python
    #links ('a') inside any div ('div') with a class name of ('most-read-widget__tab')
    headlines=driver.find_elements_by_css_selector('div.most-read-widget__tab a')
    
    for index, title in enumerate(headlines, 1):
        if title.text:
            #if the title has text, get the link and text
            link= title.get_attribute('href')
            headline= title.text
            print(index, headline)
            print(f'link : {link}')
            print('')

```
Output:
```
1 LIVE | All public schools will be shut for 4 weeks
link : https://www.news24.com/news24/southafrica/news/coronavirus-all-the-latest-news-about-covid-19-in-south-africa-and-the-world-20200312

2 Cabinet to be told to close schools for 3 weeks amid Covid-19 peak - report
link : https://www.news24.com/news24/southafrica/news/cabinet-to-be-told-to-close-schools-for-3-weeks-amid-covid-19-peak-report-20200723

3 Researchers find 'huge discrepancy' between reported number of Covid-19 fatalities and excess deaths
link : https://www.news24.com/news24/southafrica/investigations/researchers-find-huge-discrepancy-between-reported-number-of-covid-19-fatalities-and-excess-deaths-20200723

4 OPINION | South Africa won't be fixed - and the worst is on the way
link : https://www.news24.com/news24/columnists/guestcolumn/opinion-south-africa-wont-be-fixed-and-the-worst-is-on-the-way-20200723

5 Dlamini-Zuma gets flak for focusing on 'zol and alcohol' while municipalities are looted
link : https://www.news24.com/news24/southafrica/news/dlamini-zuma-gets-flak-for-focusing-on-zol-and-alcohol-while-municipalities-are-looted-20200722
```

The headlines do not look too good as by the time of writing, we are in the middle of the Covid 19 pandemic. These articles you could use for sentiment analysis or whatever downstream use case you have. 

I will make a blog post of how to crawl around the web and store the information soon and share my experience, the challenges I faced and how I overcame them.

## Conclusion
My current role has really taught me that there is a lot of low hanging fruit in the world. I am learning to think about how best to solve problems and not how best a problem can be solved with machine learning.
I hope this is able to get you fired up to learn web scraping to get data from the world wide web. Afterall, what is a data scientist without data?

