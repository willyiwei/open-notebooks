# Selenium

#python

## Three Ways to Use Web Drivers

1. Use Webdriver Manager for Python: https://github.com/SergeyPirogov/webdriver_manager
   
   ```python
   # Use Webdriver Manager for Python: https://github.com/SergeyPirogov/webdriver_manager
   
   # Import code:
   from selenium import webdriver
   from webdriver_manager.chrome import ChromeDriverManager
   from selenium.webdriver.chrome.service import Service
   
   # Use the `install()` method to set `executabe_path` in a new `Service` instance:
   service = Service(executable_path=ChromeDriverManager().install())
   
   # Pass in the `Service` instance with the `service` keyword: 
   driver = webdriver.Chrome(service=service)
   ```

2. Add the executable, e.g. `/Users/wyi/selenium/chromedriver` into $PATH

3. Hard code the executable path into Python code.

I prefer the #1 way because the Chrome version keeps updated and the web driver needs to be updated too.

## About find_element(s)_* Methods

The `find_element_by_name` method is deprecated, and we should use `find_element()` instead.

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()

driver.get("https://www.python.org/")
assert 'Python' in driver.title

time_element = driver.find_element(By.NAME, "time") # Find the element with the tag name "time"
```

## Keys are not alphabet letters

```python
from selenium.webdriver.common.keys import Keys

element.send_keys(Keys.ENTER)
```

## Selenium Custom Exception

It is `NoSuchElementException`

```python
from selenium.common.exceptions import NoSuchElementException
```



## Selenium to handle Pop Up windows

In Selenium, each window has a identification handle, we can get all the window handles with:

`driver.window_handles`

The above line of code returns a list of all the window handles. The first window is at position 0 e.g.

`base_window = driver.window_handles[0]`

New windows that have popped out from the base_window are further down in the sequence e.g.

`fb_login_window = driver.window_handles[1]`

We can switch our Selenium to target the new facebook login window by:

`driver.switch_to.window(fb_login_window)`

You can print the driver.title to verify that it's the facebook login window that is currently target:

`print(driver.title)`

or

`assert "Facebook" in driver.title`

The full code to switch to the new pop-up window is thus:

```python
base_window = driver.window_handles[0]
fb_login_window = driver.window_handles[1]
driver.switch_to.window(fb_login_window)
print(driver.title)
```



If successful the printed title should be "Facebook" and not "Tinder | Match. Chat. Date."
