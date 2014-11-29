---
layout: post
title:  "Learning Python and pandas"
date:   2014-10-02
categories: random
---


using np.where() as a sort of if then else for updating values to a dataframe/series
{% highlight python %}
np.where(new_tasks['Weight']==2,1,new_tasks['Weight'])
#to replace nulls
tasks.Task_Effort = np.where(tasks.Task_Effort.notnull(),tasks.Task_Effort,0)
{% endhighlight %}

Series.value_counts() groups by values and provides a count. It can easily be combined with plot as shown below to create a histogram.
{% highlight python %}
new_tasks['Weight'].value_counts().plot(kind='bar')
#with reindex to reorder
tasks.Build_Bucket.value_counts().reindex(xrange(1,8)).plot(kind='bar')
{% endhighlight %}

using df.groupby() sets the stage for aggregating data simply as shown below. 
{% highlight python %}
grp = new_tasks.groupby('Workflow')
{% endhighlight %}

.agg([]) makes .sort() possible
{% highlight python %}
grp['Weight'].agg(['sum']).sort('sum',ascending=False)
{% endhighlight %}

accessing a single group by name
{% highlight python %}
nt_apps.get_group('ADT')[['Effort','Weight']]
{% endhighlight %}

list comprehensions are ideal equivalent to a 'for each' construct and can be very terse. In this case combined with a dictionary
{% highlight python %}
effort_to_weight = {'low':1, 'medium':5, 'high':10}
[effort_to_weight[x] for x in new_tasks['Effort']]
{% endhighlight %}

and can also be used with an if else
{% highlight python %}
[x.lower() if x is not nan else '' for x in new_tasks['Effort']]
{% endhighlight %}

Series.describe() is perfect for a quick summary of the data
{% highlight python %}
new_tasks['Effort'].describe()
{% endhighlight %}

Series.unique() provides a list of unique values for a series
{% highlight python %}
newtasks['Effort'].unique()
{% endhighlight %}

DataFrame.columns gives a list of columns
{% highlight python %}
new_tasks.columns
{% endhighlight %}

DataFrame.rename()

all columns using lambda, which is similar to JavaScript's function(x) { return +x; }
{% highlight python %}
new_tasks.rename(columns=lambda x: x.strip(),inplace=True)
{% endhighlight %}

a single column (or multiple) with a dictionary
{% highlight python %}
new_tasks.rename(columns={'Menu/Path':'MenuPath'},inplace=True)
{% endhighlight %}

Using DataFrame.loc[]
{% highlight python %}
new_tasks.loc[10:20,'Effort']
new_tasks.loc[10:20:5,['Effort','Weight']]
{% endhighlight %}

Using DataFrame.iloc[], same as above
{% highlight python %}
new_tasks.iloc[10:20:5,[8,14]]
{% endhighlight %}

and .ix[], which accepts index or label with some quirks
{% highlight python %}
new_tasks.ix[::100,['Effort','Weight']]
new_tasks.ix[::100,[8,14]]
{% endhighlight %}

dropping unneeded columns using drop
{% highlight python %}
new_tasks.drop(['DenominatorforBuildComplete','NumeratorforBuildComplete'],axis=1,inplace=True)
{% endhighlight %}