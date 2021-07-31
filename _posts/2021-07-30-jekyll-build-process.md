---
layout: post
title:  "Here goes nothing"
date:   2021-07-30 20:18:23 +0700
categories: [meta]
---

# Build Site

{% highlight bash %}
cd /path/to/site  
echo "gem \"Jekyll\"" >> Gemfile   
echo "gem \"Webrick\"" >> Gemfile  
bundle install   
{% endhighlight %}

- Update \_config.yaml with "destination: ../targetsite/"  
Build site files and serve via:  

{% highlight bash %}
bundle exec jekyll serve 
{% endhighlight %}

Navigate to http://localhost:4000  
