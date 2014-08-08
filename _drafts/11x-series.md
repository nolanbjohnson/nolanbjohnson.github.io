---
layout: post
title:  "11x Series"
date:   2014-06-28
categories: project
---

<p>This was my <a target="_blank" href="http://bl.ocks.org/nolanbjohnson/7592473">first project</a> to learn D3.js and is based on <a href="http://www.stefanieposavec.co.uk/">Stefanie Posavec</a>'s <a href="http://www.stefanieposavec.co.uk/data/#/11-x-series-multiplication-waterfall/">11x series.</a></p>

<p>Biggest hurdles:
<ul>
  <li>Dealing with (really) big numbers</li>
  <li>Learning D3, JavaScript, and Web Development at on</li>
  <li>Stop trying to learn and just do</li>
</ul>
</p>
<p>Building some simple <code>inputs</code>:</p>
{% highlight javascript %}
    for ( i = 0; i < multiplicands; i++ ) {
      //add number to end of array of the same length as the last, 
      //comprised of ones (e.g., if 121 add 111)
      inputs.push(+Array((inputs[inputs.length - 1]+"").length + 1).join(1)); 
      inputs.push(inputs[i] * inputs[i + 1]);
    }
{% endhighlight %}
<p id="first">
<script>
var w = 200,
    h = 400,
    margin = {top: 20, right: 20, bottom: 40, left: 40},
    radius = 10,
    offset = radius * 2 + 2
    multiplicands = 3;

var svg = d3.select('#first')
      .append("svg")
      .attr("width", w - margin.left - margin.right )
      .attr("height", h - margin.top - margin.bottom );

var inputs = [];

inputs.push(11);

for ( i = 0; i < multiplicands; i++ ) {
  inputs.push(+Array((inputs[inputs.length - 1]+"").length + 1).join(1));
  inputs.push(inputs[i] * inputs[i + 1]);
}

inputs = inputs.map( function(value) { return (value+"").split(""); })

var g = svg.selectAll(".row")
         .data(inputs)
         .enter()
         .append("g")
         .attr("class", "row")
          .attr("transform", function(d, i) { 
                return "translate(0, " + (i * offset) + ")";
              });

var circle = g.selectAll("circle")
              .data( function( d, i ) { return d ; } )
              .enter()
              .append("circle")
              .attr("r", radius)
              .attr("cx", function( d, i ) { return w - margin.left - margin.right - offset * (i + 1) ; } )
              .attr("cy", offset)
              .attr("fill", "black")
              .attr("stroke", "none");

</script>
</p>

{% gist /nolanbjohnson/7592473 %}
