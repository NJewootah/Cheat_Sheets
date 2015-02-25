# Watir Cheat Sheet

**Setting up the environment**

To require the gem

```ruby
require 'Watir'

```

The following code creates an instance of the driver and stores it in the browser variable. A firefox browser is also opened.

```ruby
browser = Watir::Browser.new :ff

```

You can configure the firefox browser as you see fit; maximizing the window for example.

```ruby
browser.manage.window.maximize

```

**Website navigation**

The selenium object can be used to navigate across the web. Some of the more common methods have been listed:

* Access a website using the url

```ruby
browser.goto "http://tumblr.com/login"

```

* Go back to the previous page

```ruby
browser.back

```

**Access the website elements**

Elements on websites can be focused through their tags,ids or other attributes and used to execute certain operations. The element's id is used to access the email text field in the login form on Tumblr

```ruby
browser.text_field(placeholder: "Email")

```

Once the appropriate element is focused, operations such as inserting a text in a text field or submitting form can then be executed.

```ruby
# Insert text to the text field
browser.text_field(placeholder: "Email").send_keys("tumblrtesting1991@hotmail.com")

# Submit form
browser.button(id: "signup_forms_submit").click

# Selecting drop down list
browser.div(class: "close_button").click