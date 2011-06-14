---
layout: post
title: Get it working before you make it better | tundal45@github:~
short_title: Get it working before you make it better
date: 2011-06-01 6:42:23
---

Post commit hook was one of the things that I had heard about before but
not really something that I had the opportunity to play with much. At
work, we have started to move towards using [Pivotal
Tracker](http://www.pivotaltracker.com/) for some of our stories while
we still work with Trac for older tickets. What that meant for me was
that I had the opportunity to write the script for the post-commit hook
to hook into Pivotal Tracker. Since we already have something for Trac,
I figured that it would be a cool little project for me to do. I
researched for a little bit & found a nice little
[snippet](http://www.pivotaltracker.com/help/api?version=v3#subversion_post_commit_example)
for me to work off of.

Now, a more experienced person in my shoes would have known to just run
with this example and not think too far ahead but unfortunately, I had
big plans for my first post commit hook. I was going to make it AWESOME!
Towards that purpose, I started looking for gems that interact with the
Pivotal Tracker API so that I could write a cool little ruby script that
I could call from the post commit bash script that was in place.

Then the issue came to be on how I was going to differentiate a commit
against a Trac ticket vs a Tracker ticket. I noticed that the ticket
numbers for one had more digits than the others so I was going to make a
decision based on that but for me to do that, I need to know how to do
regular expressions in bash. So I started looking into that and was read
somewhere that I should really be using sed or awk and all of a sudden I
found myself going through man pages and had to catch myself.

The other issue that I also realized was that the svn server did not
have ruby installed on it & installing ruby on there just for one post
commit hook seemed unnecessary. At this point I had spent a few hours on
this & I basically was where I had started. Then it occurred to me that,
while not an elegant or a robust solution, I would let the post commit
hook try and update Trac as it has been doing and just append the code
to handle pivotal tracker piece afterwards. Since it was based on ticket
IDs and since the ticket ID for two systems were unique, running both
meant that only one would succeed & that was fine. It may not be the
cleanest solution but it would work.

I posted this on campfire with the concern that it may not be the most
robust solution and my boss reminded me that I should get it working
before I worry about making it better. While I feel bad for not taking
that approach to begin with, it was definitely a good reminder that it
is (almost) always good to get something quick and dirty working first and focus
on cleaning up afterwards.
