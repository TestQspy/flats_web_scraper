# Otodom Scraper
Scraper for my master's thesis project

## Description
A simple program for extracting data from offers available on the otodom.pl, website with offers of real estate for sale 

For this purpose I used libraries such as: Selenium, BeautifulSoup
```python
# import libraries
# all imports should be in OtodomScraper class without pandas lib
from selenium import webdriver
from bs4 import BeautifulSoup as bs
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.ui import WebDriverWait
```

### Otodom Scraper - OOP
Here the concept is based on three classes:
1. **DriverSettings** - here we store every option that selenium driver needs for proper work.
      
      *binary_location* - variable that stores path to your browser exe file. In my case it is brave.exe
      
      *driver_executable_path* - path to your browser driver exe. In my case, brave is based on chromium so I used chromedriver.exe
      
      *vpn_extension_path* - variable that stores .crx file of chrome extension. In this case it is responsible for using VPN in my instance of test brave browser. For this              purpose I used extensions source code extractor on http://crxextractor.com/, using link of extension found in store.
      
      Others attributes are intuitive in my opinion, therefore I will not describe them in detail here.
    
2. **FlatOffer** - it stores chosen attributes of real estate, which I believe will be crucial in future analyzes.

      Some of the attributes that may be confusing:
      
      *prod_yera* - indicates to production year of whole building in which flat is.
      
      *finish_condition* - it tells us whether the apartment is suitable for living, and in which condition it is. There are three options:
      
            For living
            To finish
            For renovation
       
3. **OtodomScraper** - main class in the project, it has webdriver chrome options object, DriverSettings and FlatOffer objects in it. About class an its methods you can read in docstrings.


### Otodom Scraper - not OOP
Basicly everything is like in description above, but without classes and methods etc.

## Working schema ##

Schema is simple:
1. Create seleniu driver object with custom options.
2. "Feed" driver with otodom URL with filters or not your choice, but it must be after search button click.
3. Close cookies banner because it covers next-page button.
4. Get page soup with beautifulsoup.
5. Start loop through all article elements on site - there are sotred all offers.
6. Check if offer id is in id list if yes then print doubled offer else add id to list.
7. First 5 attributes are gathered from main page (price, room number etc.).
8. Open new tab.
9. Switch driver to it.
10. Try to get other attributes, if there was no problem break while loop else refresh until offer shows up or delete last row and close the tab.
11. After iterate through all offert on page click next-page button.
12. Go to step 5.
