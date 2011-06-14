---
layout: post
title: Ruby Quirks - String#[] | tundal45@github:~
short_title: Ruby Quirks - String#[]
date: 2010-07-10 6:35:22
---

Ruby String class has `[]` operator that allows us to get a substring
for a given string. For example:

{% highlight ruby %}

name = "Ashish"
str = name[2,3] # str contains "his"

{% endhighlight %}

However, if you pass a single index to the `[]` operator, the response
is not something you would expect. For example:

{% highlight ruby %}

char = name[1] # char contains 115, the ASCII representation of the character s

{% endhighlight %}

While we are in the topic of characters and their ASCII representation,
Ruby provides a `?` operator to evaluate the ASCII representation of a
string. For example:

{% highlight ruby %}

?a  # returns  97
?A  # returns 65
?s  # returns 115
?AA # results in  SyntaxError

{% endhighlight %}

This quirk can be seen in Ruby 1.8.7 and earlier versions of Ruby.
However, from 1.9.1, the behavior is as expected. For example, in 1.9.1
and beyond:

{% highlight ruby %}

?a          # returns a
"Ashish"[1] # returns s

{% endhighlight %}
