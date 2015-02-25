# Selenium Cheat Sheet

**Setting up the environment**

To require the gem

```ruby
require 'selenium-webdriver'

```

The following code creates an instance of the driver and stores it in the browser variable. A firefox browser is also opened.

```ruby
browser = Selenium::WebDriver.for :firefox

```

You can configure the firefox browser as you see fit; maximizing the window for example.

```ruby
browser.manage.window.maximize

```

**Website navigation**

The selenium object can be used to navigate across the web. Some of the more common methods have been listed:

* Access a website using the url

```ruby
browser.navigate.to "http://tumblr.com/login"

```

* Go back to the previous page

```ruby
browser.back

```

**Access the website elements**

Elements on websites can be focused through their tags,ids or other attributes and used to execute certain operations. The element's id is used to access the email text field in the login form on Tumblr

```ruby
browser.find_element(id: "signup_email")

```

Once the appropriate element is focused, operations such as inserting a text in a text field or submitting form can then be executed.

```ruby
# Insert text to the text field
browser.find_element(id: "signup_email").send_keys("tumblrtesting1991@hotmail.com")

# Submit form
browser.find_element(id: "signup_form").submit

```

**Waiting on website elements**

Some elements are not available instantly as they are only enabled or loaded once other operations/elements have run/loaded. The wait method is useful here to enable the waiting time for the elements to load.

```ruby
# Creating the Wait object
wait = {:five => Selenium::WebDriver::Wait.new(:timeout => 5),
        :ten => Selenium::WebDriver::Wait.new(:timeout => 10)}

# Calling the until method on the website navigation
wait[:ten].until{browser.navigate.to "http://tumblr.com/login"}
```
