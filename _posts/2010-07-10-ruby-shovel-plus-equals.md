---
layout: post
title: Shovel vs. Plus Equals operator in Ruby | tundal45@github:~
short_title: Shovel vs. Plus Equals operator in Ruby
date: 2010-07-10 8:28:45
---

This is going to be first of what I hope to be many blog posts
documenting my foray into Ruby programming. Foray might be a bad choice
of word given that this is not my first attempt at learning the
language. However, the approach that I am taking this time around is
more active than my previous attempts so I am hopeful. Like any other
endeavor, this too has a goal and a specific one at that - being able to
build a foundation in Ruby in time for [Lone Star Ruby
Conference](http://lonestarrubyconf.com/) at the end of August.

The approach this time is to follow [Mike
Clark](http://twitter.com/clarkware)'s
[ad](http://www.clarkware.com/cgi/blosxom/2005/03/18/RLT1)[vice](http://www.clarkware.com/cgi/blosxom/2005/03/18/RLT2)
and build tests as I delve into different features of Ruby while reading
[The Well Grounded Rubyist](http://www.manning.com/black2/) by [David A.
Black](http://twitter.com/david_a_black).

The reason I am optimistic about this approach is because I am currently
working through the wonderful [Ruby
Koans](http://github.com/edgecase/ruby_koans) created by the good folks
over at [EdgeCase](http://edgecase.com/home). Ruby Koans was what
introduced me to Mike Clark's approach on learning different facets of
Ruby. This is a great starting point for anyone who is new to Ruby as it
introduces both the core concepts or Ruby while introducing the idea of
testing. Since we are not writing code, it is not test-first-development
but more of an inquiry into the ruby interpreter through test cases. The
best part about Ruby Koans so far is the question that are posed that
forces you to move away from the hows that the tests focus on to more of
the whys. I am going to focus on one such whys on this post.

The question posed in one of the Koans was in regards to String
modification. The tests were for the shovel (`<<`) and plus equals
(`+=`) operators. The question was:

>Ruby programmers tend to favor the shovel operator (`<<`) over the plus
>equals operator (`<<`) when building up strings. Why?

At first, I did not pay attention to this and was about to move to the
next failing test. However, since I wanted to do proper justice to my
learning experience, I decided to think a little bit about the the two
operators in relation to the question being posed. My gut feeling told
me that it probably had to do with the fact that the shovel (`<<`)
operator modifies the actual object while the plus equals (`+=`)
operator created a new object altogether.

Of course, I was afraid of being wrong and wanted to verify this. I was
about to fire up IRB to test it out when I remembered Mike Clark's
approach to learning and thought I should write a test to see if what I
was thinking was the answer was true. So, I decided to write a quick
test:

{% highlight ruby %}

require 'test/unit'

class StringTest < Test::Unit::TestCase

  def test_plus_equals_creates_new_object
    original_string = "Hello, "
    hi = original_string
    assert_equal original_string.object_id, hi.object_id
    there = "World"
    hi += there
    assert_not_equal original_string.object_id, hi.object_id
  end

  def test_shovel_does_not_create_new_object
    original_string = "Hello, "
    hi = original_string
    assert_equal original_string.object_id, hi.object_id
    there = "World"
    hi << there
    assert_equal original_string.object_id, hi.object_id
  end
end

{% endhighlight %}

The test proved my initial hunch. I was going to leave it at that but
then I remembered that Array also use both operators. So I wrote another
test to verify that the behavior is the same for Arrays:

{% highlight ruby %}

require 'test/unit'

class ArrayTest < Test::Unit::TestCase

  def test_plus_equals_creates_new_object
    original_string = ["Hello"]
    hi = original_string
    assert_equal original_string.object_id, hi.object_id
    there = ["World"]
    hi += there
    assert_not_equal original_string.object_id, hi.object_id
  end

  def test_shovel_does_not_create_new_object
    original_string = ["Hello"]
    hi = original_string
    assert_equal original_string.object_id, hi.object_id
    there = ["World"]
    hi << there
    assert_equal original_string.object_id, hi.object_id
  end

end

{% endhighlight %}

So long story short, the reason why Ruby programmers prefer the shovel
operator (`<<`) over the plus equals (`+=`) operator when building
strings is to avoid creating multiple objects during the process. If
there are subtleties that I am missing or if I am completely wrong, I
would love to hear from people and improve upon what I have learned so
far.
