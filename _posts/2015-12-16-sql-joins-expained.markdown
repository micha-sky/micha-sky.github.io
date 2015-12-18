---
layout: post
title:  "sql joins explained"
date:   2015-12-16 19:38:58 +0200
categories: deployment
---

here i want to explain the difference between inner, left, right joins in sql.
saying left and right you have to think of tables to the left and right sides of join expression.

{% highlight sql %}
inner join
{% endhighlight %}
inner join returns records from left table that are present in right table.

{% highlight sql %}
left join
{% endhighlight %}
left join is similar to inner, but if there is no related records in right table, it will return nulls.

{% highlight sql %}
right join
{% endhighlight %}
returns all record from the right table that are present in the left one.

{% highlight sql %}
full join
{% endhighlight %}
there's also a full join that returns all records from all tables and puts nulls where records does'nt exist.