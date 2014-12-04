---
layout: post
title: Template
date:   2014-11-12 17:59:15
categories: jekyll update
---

## what is a template

What is a template. In order to generate **html** which is the language interpreted by the browser.

In order to stay close to the html we have chosen to use [handlebarsjs](http://handlebarsjs.com).

A template is written in handlebars language which is really close to the html.

Once written in handlebars template, the template is compiled into a  **JavaScript** function. Then you can call it from any piece of js code.

Once you have the template, the process is quite simple:
In order to get plain **html** from a template you have to give it data.

Maybe a little example would help:
The following example is a template which should generate a title. The file template is named **home.hbs** 
{% highlight html %}
{% raw %}
 <h1>{{title}}</h1>
 {% endraw %} 
{% endhighlight %}
Then you can call it this way
{% highlight javascript %}
  var homeTemplate = require('home');
  var templateData = {title: 'Welcome to the fantastic app'}; 
  homeTemplate(templateData); 
  // render 
  //<h1>Welcome to the fantastic app</h1> ’’’
{% endhighlight %}

## Focus use

In focus all templates are use within the views.
When an event is triggered to the view such as `model:change`, the view renders its template into its ** DOM Element. **

![Data Model]({{ site.url }}/{{site.baseurl}}/assets/template.png)

## Templates helpers

In order to be able to industrialize the behaviour in the templates, we built some handlebars helpers.
There are to types of them:
- The **simple helpers** which renders a content: `{{input_for "firstName"}}`. These helpers takes parameters and they are often associated with data.
- The **block helpers** wich are more like open / closing html tags: `{{#criteria}}<p>Other content</p>{{/criteria}}`.

Helper lists (certainly non exhaustive):


| viewHelper  | What does it do?                                                                                                     | default               | options                                                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| input_for   | Render an input in a form, with label and formating. The first argument is mandatory and contains the property name. | input_for "firstName" | **isNoLabel**, in order to display or not the label. **noHtml** in order to generate only the input and no div wrapper around it. `input_for "firstName" isNoLabel=true` |
| display_for | Render a field in a panel, with label and formating.The first argument is mandatory and contains the property name   | display_for ""        |                                                                                                                                                                          |
|             |                                                                                                                      |                       |                                                                                                                                                                          |
|             |                                                                                                                      |                       |                                                                                                                                                                          |

