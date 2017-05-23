---
title: Add a Promotional Header to Your Shopify Theme
date: 2015-12-01
tags: 
 - how-to 
 - shopify
 - css
 - javascript
 - ruby
 - liquid
category: articles
---

I just wanted to write up a quick how-to on adding a little promotional div to the top of your Shopify store. This could come in handy with the holidays coming up! In my shops, we're using it to promote flash coupon codes and shipping discounts.

It is essentially just going to be a full-width div with one-line of text and a background color, all of which you'll set in your theme settings.json file. After the initial set-up in this article, you won't have to touch Liquid code again. 

## Add the Liquid template code

Open your [`theme.liquid`](https://help.shopify.com/themes/development/layouts/theme-liquid) file (found in the `/layouts` folder), and right after your opening `<body>` tag add the following bit of code:

{% codeblock lang:ruby theme.liquid %}{% raw %}
{% if settings.promotionalBar-visible %}
  {% include 'promotionalBar' %}
{% endif %}  
{% endraw %}{% endcodeblock %}

You can likely see where this is going just by looking at that code. We're going to create a snippet called 'promotionalBar', which will have a true/false toggle in our theme's settings file. 

First, let's create the snippet. In your [`snippets`](https://help.shopify.com/themes/development/templates#snippets) folder, create a new snippet and call it 'promotionalBar'. Add this text to it:

{% codeblock lang:html promotionalBar.liquid %}{% raw %}
<div class="promotionalBar">
  {{ settings.promotionalBar-text }}
</div>
{% endraw %}{% endcodeblock %}

## Add the SCSS styles

 Now, let's go ahead and set up the styling in our `styles.scss.liquid` file. If you have variables at the top you can add these two lines:

{% codeblock lang:scss styles.css.liquid %}{% raw %}
// promotionalBar.liquid
$promotional-bar-background-color: {{ settings.promotionalBar-background-color }};
$promotional-bar-text-color: {{ settings.promotionalBar-text-color }};
{% endraw %}{% endcodeblock %}

And then add this selector alongside your other classes:

{% codeblock lang:scss styles.css.liquid %}{% raw %}
.promotionalBar {
  color: $promotional-bar-text-color;
  background: $promotional-bar-background-color;
  text-align: center;
  font-size: .8em;
  font-weight: bold;
}
{% endraw %}{% endcodeblock %}

If you don't have variables in your stylesheet, just move the `settings.promotionalBar-*` from the first codeblock variables directly into the CSS.


# Create the settings to control it

Now, open your [`settings_schema.json`](https://help.shopify.com/themes/development/theme-editor/settings-schema) file, which you'll find in the `/config` directory, and add the following object to this file:

{% codeblock lang:javascript settings_schema.json %}
{
    "name": "Promotional Add-Ons",
    "settings": [
        {
            "type": "paragraph",
            "content": "Enable or disable the promotional bar" 
        }, {
            "type": "checkbox",
            "id": "promotionalBar-visible",
            "label": "Show Promotional Bar at the top of every page?"
        }, {
            "type": "text",
            "id": "promotionalBar-text",
            "label": "Message for promotional bar"
        }, {
            "type": "color",
            "id": "promotionalBar-background-color",
            "label": "Background color",
            "default": "#000000"
        }, {
            "type": "color",
            "id": "promotionalBar-text-color",
            "label": "Text color",
            "default": "#FFFFFF"
        }
    ]
}
{% endcodeblock %}

Save that file, and now you are done editing your template!

## Go to your theme settings

Go to your Shopify theme section and click the "Customize" button for the theme. This will take you to a WYSIWYG editor, and on the right side you'll see the newly added "Promotional Add-Ons" section! EThis is where you'll be setting the message itself, as well as the background color and text color. 

Please let me know on [Twitter](https://twitter.com/ericpatr) if you found this helpful or have any questions! I'd like to write more guides like this in the future if there is any interest! 