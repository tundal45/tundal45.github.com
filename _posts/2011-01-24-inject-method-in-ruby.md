---
layout: post
title: Enumerable#inject in Ruby | tundal45@github:~
short_title: Enumerable#inject in Ruby
date: 2011-01-24 9:08:23
---

Continuing the trend of [documenting the
questions]({{site.baseurl}}/include-vs-extend-in-ruby.html) that come up
while I start catching up with [Practicing
Ruby](http://letter.ly/practicing-ruby), I thought a post on
[`Enumerable#inject`](http://rdoc.info/stdlib/core/1.9.2/Enumerable#inject-instance_method)
was in order. While I could go and try to explain the inject method
myself, I think I would be better off letting [Jay
Fields](http://jayfields.com/) take charge because he wrote a really
great [post](http://blog.jayfields.com/2008/03/ruby-inject.html) about
it.

I have always been confused yet intrigued by `inject` but Jay's post
definitely clarified a lot of things for me. The key takeaway for me
from his post was that while there are other ways through method
chaining that you can accomplish some of the object construction tasks,
where `inject` shines is in its simplicity to allow additional
operations on the elements being iterated over during object
construction. While chaining is a little more concise, I personally
found the examples using `inject` to be more readable.

<!--script src="https://gist.github.com/793208.js?file=inject.rb"></script-->
{% highlight ruby %}

places = %w( Reno Chicago Fargo Minnesota Buffalo Toronto Winslow Sarasota 
             Wichita Tulsa Ottawa Oklahoma Tampa Panama Mattawa La Paloma 
             Bangor Baltimore Salvador Amarillo Tocapillo Baranquilla and 
             Perdilla)

puts places.inject("I've been to: ") { |result, place| "#{result}#{place}, " } + "I'm a killer"

{% endhighlight %}

Since Jay mentioned object construction, I figured a string example
would give a better picture of how the argument passed to inject is only
used in the first iteration of the block whereas the second argument
contains the element from the `places` array for that current iteration.

Once again, if I am wrong about something or unclear in the post, please
feel free to point that out in the comments section. My goal with
positng things that I am reading about is to document what I am learning
and crystallize the ideas in my head by trying to come up with some code
examples. I also strongly urge you to sign up for the [Practicing
Ruby](http://letter.ly/practicing-ruby) so that you can be treated to
ruby awesomeness twice a week for only $8 a month and support [Ruby
Mendicant University](http://university.rubymendicant.com) in the
process.

**UPDATE:** As per the feedback from Matt Yoho below, I have updated the
gist to use string interpolation instead of string concatenation using
the `+` operator to avoid the case where Ruby creates a whole bunch of
strings. Gregory Brown also mentioned that using inject with Strings is
dangerous for performance reasons. Both Matt & Greg voiced concerns
about how inject can sometimes be overused.

I want to _emphasize_ the fact that the posts here are part of my
learning process and therefore should be taken with a grain of salt. I
will be making a lot of mistakes and the reason I am posting them here
is so that I can get feedback from people, like I did in this case, who
know better and learn/improve from that interaction.

**UPDATE 2:** Since writing this post, Greg has made a tough decision
and **the [practicing ruby newsletter](http://letter.ly/practicing-ruby)
is going to be discontinued** in the coming weeks. Therefore, I suggest
that you **only subscribe if you are interested in receiving the back
issues and/or supporting RMU**. I also would like to remind you that if
you wish to support RMU, there is a
[pledgie](http://pledgie.com/campaigns/13580) set up and you can help
ensure that RMU continues to run sustainably by donating however much
you can. Thank you for your support.
