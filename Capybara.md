# Capybara Cheat Sheet

**Setting up the environment**

To require the gem

```ruby
require 'capybara'

```

The following code creates an instance of the driver and stores it in the browser variable. A firefox browser is also opened.

```ruby
browser = Capybara::Session.new(:selenium)

```

You can configure the firefox browser as you see fit; maximizing the window for example.

```ruby
browser.manage.window.maximize

```

**Website navigation**

The selenium object can be used to navigate across the web. Some of the more common methods have been listed:

* Access a website using the url

```ruby
session.visit('http://www.tumblr.com/login')

```

* Go back to the previous page

```ruby
browser.back

```

**Access the website elements**

Forms can be accessed and manipulated simply and quickly using Capybara. A text field insert is shown below.

```ruby
# Inserting text in the email text field
session.fill_in('Email',:with => "tumblrtesting1991@hotmail.com")

# Submitting a form
session.click_button('Post')

```

However other elements such as div tags can be more complex as shown below.

```ruby
# Insert text in a div
session.find('.title-field .editor-plaintext').set('Bond')

# Output success/failure message to terminal
if session.first('.title').text == 'Bond' && session.first('.body-text').text == 'James Bond'
  puts "Message successfully uploaded"
else
  puts "Message failed to upload"
end

```

**Waiting on website elements**

Some elements are not available instantly as they are only enabled or loaded once other operations/elements have run/loaded. The wait method is useful here to enable the waiting time for the elements to load.

```ruby
# Waiting for the media list to be loaded
expect(session.find('#post_buttons').find('.new_post_label_text').to have_content('Text'))

```




