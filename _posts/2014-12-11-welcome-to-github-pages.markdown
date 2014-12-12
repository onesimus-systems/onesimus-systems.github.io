---
layout: post
title:  "Welcome to Github Pages!"
date:   2014-12-11 23:08:00
categories: update
---
Over the coming days (or weeks), I'll be building the Onesimus Systems website from Github Pages. Hosting was getting a tad
expensive (at least for this small site) and running a droplet seems like a waste. Github Pages should serve as a nice platform
for building. It'll probably take some time to get used to Jekyll and Front Matter, but I'm sure I can handle it.

This website will serve as the official blog and news source for Onesimus Systems. All release news and whatnot will be
published here.

Jekyll offers powerful support for code snippets (I prefer Go, who uses Ruby these days? Honestly.):

{% highlight go %}
func printHi(s string) {
    fmt.Printf("Hi, %s", s)
}
printHi("Tom")
#=> prints "Hi, Tom" to STDOUT.
{% endhighlight %}
