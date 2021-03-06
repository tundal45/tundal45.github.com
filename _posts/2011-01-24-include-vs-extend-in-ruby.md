---
layout: post
title: include Vs. extend in Ruby | tundal45@github:~
short_title: include Vs. extend in Ruby
date: 2011-01-24 8:37:29
---

So after a productive weekend of finally reflecting on
[my]({{site.baseurl}}/the-new-york-ruby-meetup.html)
[ruby]({{site.baseurl}}/ruby-dcamp-one-weekend-of-pure-awesome.html)
[community]({{site.baseurl}}/my-rmu-experience-core-skills.html)
[immersion]({{site.baseurl}}/the-story-so-far.html) in 2010, I decided
enough was enough and I need to dive right into the [Practicing
Ruby](http://letter.ly/practicing-ruby) newsletter. The first topic that
spans the two issues was on Ruby's Method Lookup path, a fundamental
concept for rubyists to know, internalize & understand. If you want to
find out about this topic & other great reads, I highly recommend that
you sign up for [Practicing Ruby](http://letter.ly/practicing-ruby). For
$8 a month, it is a worthwhile investment in building your understanding
of Ruby. If you are someone who seeks value add not just to yourself and
prefers that your actions also help others, you will be happy to learn
that the proceeds of the newsletter help in supporting [Ruby Mendicant
University](http://university.rubymendicant.com).

You may be wondering what this all has with Include vs Extend in Ruby.
Well, the example code that [Gregory
Brown](http://twitter.com/#!/seacreature) used in the newsletter used
both include & extend and that made me wonder what the difference
between them was. My gut reaction was that maybe you use include when
you are defining classes and use extend when you want to mixin the
functionality of modules directly into the object's singleton class,
i.e, the object itself. Good thing I decided to
[check](http://duckduckgo.com/?q=difference+between+include+and+extend+in+ruby)
because I would have been wrong. [John
Nunemaker](http://twitter.com/#!/jnunemaker) has a [nice
post](http://railstips.org/blog/archives/2009/05/15/include-vs-extend-in-ruby/)
on this that I recommend checking out but the gist is that when you
extend a module, the methods defined in that module become class methods
of the class whereas when you include a module, the methods become
instance methods. If you want to know the difference between class &
instance methods, John Nunemaker once again [comes to your
rescue](http://railstips.org/blog/archives/2009/05/11/class-and-instance-methods-in-ruby/)

So there you have it, some resources to read through to understand the
difference between include and extend in Ruby. My goal is to document
the questions that arise as I catch up to the Practicing Ruby newsletter
and post what I find here. That way I can have it documented here to
look back to, I can share what I learn with others, and if I am wrong,
people can point that out and correct me through comments. Let's hope I
can keep this up :).

**UPDATE:** Since writing this post, Greg has made a tough decision and
**the [practicing ruby newsletter](http://letter.ly/practicing-ruby) is
going to be discontinued** in the coming weeks. Therefore, I suggest
that you **only subscribe if you are interested in receiving the back
issues and/or supporting RMU**. I also would like to remind you that if
you wish to support RMU, there is a
[pledgie](http://pledgie.com/campaigns/13580) set up and you can help
ensure that RMU continues to run sustainably by donating however much
you can. Thank you for your support.
