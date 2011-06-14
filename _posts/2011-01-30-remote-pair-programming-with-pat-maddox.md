---
layout: post
title: Remote Pair Programming with Pat Maddox | tundal45@github:~
short_title: Remote Pair Programming with Pat Maddox
date: 2011-01-30 8:57:49
---

When I woke up Saturday, my goal was to write a post reflecting on my
experience [pair
programming](http://en.wikipedia.org/wiki/Pair_programming) remotely
with [Pat Maddox](http://twitter.com/#!/patmaddox) who had recently
invited anyone who is interested to [pair with
him](http://patmaddox.com/blog/pair-with-me). Once I started thinking
about how I wanted to approach the post, I thought I needed to talk
about remote pair programming in general and how it has been a great way
for me to [learn and interact with more experienced
rubyists]({{site.baseurl}}/remote-pair-programming-to-learn.html).
However, a converstaion with Evan helped me realize that what I have
stumbled upon has a [much greater value outside of being a great
learning tool for
me]({{site.baseurl}}/stand-remotely-on-the-shoulder-of-giants.html). So
here I am at around 9 PM on a Sunday night finally starting to put my
thoughts down on my experience pairing with Pat Friday evening.

First of all, I want to thank Pat for making time to pair with me as
well as for taking the initiative to invite people to pair with him. It
is really great opportunity not just for beginners like me who can learn
a lot from pairing with someone of Pat's caliber but also for other
members of the community to be able transcend the limitations of
physical distances and come together to work on a problem. The whole
concept of leveraging the internet and tools that we have at our
disposal that allows us to collaborate with one another deserves the
kind of spotlight that initiatives like Pat's will bring to it. However,
I have already talked about that in previous posts and want to focus
more on the specifics of the experience pairing with Pat here.

[Test Driven Development
(TDD)](http://en.wikipedia.org/wiki/Test-driven_development) is
something that is very new to me and has only recently been part of my
practice in my [journey]({{site.baseurl}}/the-story-so-far.html) through
[the long
road](http://apprenticeship-patterns.labs.oreilly.com/ch03.html#the_long_road)
of learning Ruby and becoming a better programmer. Therefore, it is
still a skill that I struggle with. So it was great to work on a [code
kata](http://codekata.pragprog.com/2007/01/kata_four_data_.html) with
Pat and see how he [started out
with](https://github.com/patmaddox/data_kata/blob/master/spec/data_kata_spec.rb#L63-69)
an [acceptance test](http://c2.com/cgi/wiki?AcceptanceTest) that was
going to fail. This was the test that would tell us that we are done,
once it passes. However, to start making progress, we decided to make
the acceptance test pending and focus on figuring out what the [maximum
temperature for that day
was](https://github.com/patmaddox/data_kata/blob/master/spec/data_kata_spec.rb#L77-83).
Similarly, we wrote another test that [told us the number of
days](https://github.com/patmaddox/data_kata/blob/master/spec/data_kata_spec.rb#L73-76)
in [our
dataset](https://github.com/patmaddox/data_kata/blob/master/spec/weather.dat).
While these tests were not really testing the crux of the application,
they helped us make progress on the problem and that was a great tip to
learn.

It was clear that Pat has been doing pair programming with people from
various skill levels. He was very good about encouraging me to drive and
always asking what I thought of the approach we were taking. I
immediately felt at ease with sharing my opinions as well as asking
questions whenever I got confused about the code. Pairing on a Kata was
also good because it was small enough problem that we could understand
the domain pretty quickly but big enough to provide interesting problems
to solve. One of the things we had to ensure was [to
ignore](https://github.com/patmaddox/data_kata/blob/master/spec/data_kata_spec.rb#L38-48)
the
[unnecesary](https://github.com/patmaddox/data_kata/blob/master/spec/weather.dat#L1-8)
[text](https://github.com/patmaddox/data_kata/blob/master/spec/weather.dat#L39-40)
in the weather data file. We also encountered a bug on [line
46](https://github.com/patmaddox/data_kata/blob/master/spec/data_kata_spec.rb#L46)
where our previous code looked as follows:

<!--script src="https://gist.github.com/803566.js"> </script-->
{% highlight ruby %}

@days << parse_line(line) if in_data_section && line.strip.match(/^\d/)

{% endhighlight %}

The problem was that while we made sure to strip the line when we looked
for the line with weather data, we sent the parser the line with
preceeding spaces which caused our parser to extract the wrong weather
data. This kind of bug would have taken a while to figure out if it was
just one person programming but between the two of us chatting, we were
quickly able to find it, fix it and be well on our way. The test suite,
no matter how sparse it is, definitely helped too :).

Even though we only got around to finishing up part 1 of the kata, I
look forward to pairing with Pat again in the future to work on parts
two and three of the Kata. It was a really great learning experience and
I encourage anyone who is interested in Ruby to take Pat up on his offer
and pair with him.
