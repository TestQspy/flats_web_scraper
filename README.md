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
Here concept is based on three classes:
1. **DriverSettings** - here we store every option that selenium driver needs for proper work.
      
      *binary_location* - variable that stores path to your browser exe file. In my case it is brave.exe
      
      *driver_executable_path* - path to your browser driver exe. In my case, brave is based on chromium so I used chromedriver.exe
      
      *vpn_extension_path* - variable that stores .crx file of chrome extension. In this case it is responsible for using VPN in my instance of test brave browser. For this              purpose I used extensions source code extractor on http://crxextractor.com/, using link of extension found in store.
      
      Others attributes are intuitive in my opinion, therefore I will not describe them in detail here.
    
2. **FlatOffer** - it stores chosen attributes of real estate, which I believe will be crucial in future analyzes.

      Some of the attributes that may be confusing:
      
      *prod_yera* - indicates to production year of whole building in which flat is.
      
      *finish_condition* - it tells us whether the apartment is suitable for living, and in which condition it is. There are three options:
      
            1) For living
            2) To finish
            3) For renovation
       
       
      
