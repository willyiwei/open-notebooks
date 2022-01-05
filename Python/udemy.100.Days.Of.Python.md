# Udemy 100 Days of Code KB

## Python Packages

| Usage                  | Python Packages    |                                                                                           |
| ---------------------- | ------------------ | ----------------------------------------------------------------------------------------- |
| CVS, JSON and Big Data | pandas             |                                                                                           |
| HTTP Client            | requests           |                                                                                           |
| GUI Programs           | tkinter, turtle    |                                                                                           |
| Web Scrabing           | Beautiful Soup     | Easy to use; No ability to enter forms or click buttons; Best to scrap simple HTML files. |
|                        | Selenium Webdriver |                                                                                           |
|                        |                    |                                                                                           |

## Selenium

### Useful find_* Methods

* find_element(s)_by_id: usually id is unique.
* find_element(s)_by_name: good for finding forms because forms usually need names to store the values (into variables).
* find_element(s)_by_class_name:
* find_element(s)_by_css_selector: Another good way to locate an element.

if all above fail:

* find_element(s)_by_xpath, the trick is to use Chrome Developer Tool to "Copy XPath".
