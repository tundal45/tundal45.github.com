---
layout: post
title: Oracle External Table woes
---

The issue, which I have been working on for a while, is that when I run a query that creates an external table in Oracle, it works swimmingly. However, when I ran the same query using a Perl script, I was receiving the following error:

<pre>KUP-01005: syntax error found "identifier": expecting one of: "number, plussign"</pre>

I printed the query to the screen as well as to a file and it would look exactly the same as the query that worked when manually executed using PL/SQL. However, I realized, by accident of course, that if I change the ":" to a "-" in the ACCESS PARAMETERS where I provide range for columns (I am working with a fixed width file), it magically works.

Here is an Example:

*QUERY THAT DOES NOT WORK IN PERL:*

{% highlight sql %}

--Query that does not work in Perl

CREATE TABLE ex.emp
(
  emp_no varchar(255),
  emp_title varchar(255),
  emp_name varchar(255),
  emp_address varchar(255)
)
ORGANIZATION external
(
  TYPE oracle_loader
  DEFAULT DIRECTORY empdata
  ACCESS PARAMETERS
  (
      RECORDS DELIMITED BY 0X\'0A\'
      READSIZE 1048576
      FIELDS LRTRIM
      MISSING FIELD VALUES ARE NULL
      REJECT ROWS WITH ALL NULL FIELDS
      (
        emp_no (1:5)
        emp_title varchar (6:20)
        emp_name varchar (21:51)
        emp_address varchar(52:92)
      )
  ) location('emp_info.txt')
)REJECT LIMIT UNLIMITED;

{% endhighlight %}

{% highlight sql %}

--Query that works in Perl

CREATE TABLE ex.emp
(
  emp_no varchar(255),
  emp_title varchar(255),
  emp_name varchar(255),
  emp_address varchar(255)
)
ORGANIZATION external
(
  TYPE oracle_loader
  DEFAULT DIRECTORY empdata
  ACCESS PARAMETERS
  (
      RECORDS DELIMITED BY 0X\'0A\'
      READSIZE 1048576
      FIELDS LRTRIM
      MISSING FIELD VALUES ARE NULL
      REJECT ROWS WITH ALL NULL FIELDS
      (
        emp_no (1-5)
        emp_title varchar (6-20)
        emp_name varchar (21-51)
        emp_address varchar(52-92)
      )
  ) location('emp_info.txt')
)REJECT LIMIT UNLIMITED;

{% endhighlight %}

I basically spent two days a while back on a similar issue for another script a while back and half a day today before I found this solution. However, its one of those very dissatisfying resolution because you feel what you were doing SHOULD WORK. If anyone has a satisfying answer to why this makes sense, I would love to hear it. As for now, the only satisfaction I can get out of this situation is that it will help me keep moving forward with this script as well as the script I stopped working on couple of months back because of this error.
