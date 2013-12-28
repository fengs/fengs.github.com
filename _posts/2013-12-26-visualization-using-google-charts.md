---
layout: post
title: "Visualization and Queries Using Google Charts"
description: ""
category: "technical"
tags: [javascript, queries, visualization, google charts, diet, health]

---
{% include JB/setup %}

I have been shedding some pounds since November, about the same time as I launched this blog. My approach is pretty straightforward:
- Cutting off carbonhydrages. 
- Running for an hour every day. 

And it works for me. It feels awesome to see the scale drop and pants become loose. There are controversies with regard to the low-carb diet, which I'm not going into details about. Just for this specific scenario, what if I'd like to visualize my progress, and blog it by the way.

The [matplotlib] (http://matplotlib.org/) of Python is a first try. But I googled something better. Yup, the [Google Charts] (https://developers.google.com/chart/?hl=fr). Not only because it is *very* pretty, but also for the interactive capability of Javascript. 

Take a look at this **Column Chart**, which looks very similar to a histogram chart but it does not deal with bins or frequencies. It is just a basic plot with bars instead of dots and lines. If you hover the mouse over one of the bars, the corresponding date automatically displays. Nice job, Google!

<script type="text/javascript">
  alert("This post demonstrates the usage of Javascript on Jekyll.")
</script>

<script type="text/javascript" src="https://www.google.com/jsapi">
</script>

<script type="text/javascript">
   google.load("visualization", "1", {packages:["corechart"]});
</script>

<script type="text/javascript">
  var visualization;

  function drawVisualization() {
    // To see the data that this visualization uses, browse to
    // http://spreadsheets.google.com/ccc?key=pCQbetd-CptGXxxQIG7VFIQ
    var query = new google.visualization.Query(
      'https://docs.google.com/spreadsheet/ccc?key=0AiA3av6cH1otdHlUMGQxcDhHOU0xX004QV9DWmlESGc&usp=sharing');
    query.setQuery('select A, B');
  
    // Send the query with a callback function.
    query.send(handleQueryResponse);
  }
  
  function handleQueryResponse(response) {
    if (response.isError()) {
    alert('Error in query: ' + response.getMessage() + ' ' + response.getDetailedMessage());
    return;
    }
  
    var data = response.getDataTable();
    var options = {
    title: "Weight History",
    width: 700,
    height: 500,
    bar: {groupWidth: "50%"},
    legend: { position: "none" },
    };
    visualization = new google.visualization.ColumnChart(document.getElementById('visualization'));
    visualization.draw(data, options);
  }
  

  google.setOnLoadCallback(drawVisualization);
</script>

<div id="visualization">
</div>

The data was not hard-coded into the scripts. Queries are sent to get the 'real-time' updated data in the table to keep the monitoring going. Say I'll add an entry later this week if the scale drops again (I wish). The insertion will be reflected in the current fetch. Use query to populate data is no doubt the right way to do things. Hard-coding NO. 

Here is how to query to draw google charts. First, you need a table, say a google spreadsheet. Like this one I just created.

![] (https://raw.github.com/fengs/fengs.github.com/master/Fig/google_spreadsheet.png)

Make sure not to set the visibility as private. With the [link] (https://docs.google.com/spreadsheet/ccc?key=0AiA3av6cH1otdHlUMGQxcDhHOU0xX004QV9DWmlESGc&usp=sharing#gid=0) of the spreadsheet we are good to go to the next step.

    <script type="text/javascript">
    var visualization;

    function drawVisualization() {
      // To see the data that this visualization uses, browse to
      // http://spreadsheets.google.com/ccc?key=pCQbetd-CptGXxxQIG7VFIQ
      var query = new google.visualization.Query(
          'https://docs.google.com/spreadsheet/ccc?key=0AiA3av6cH1otdHlUMGQxcDhHOU0xX004QV9DWmlESGc&amp;usp=sharing');
      query.setQuery('select A, B');
    
      // Send the query with a callback function.
      query.send(handleQueryResponse);
    }
    
    function handleQueryResponse(response) {
      if (response.isError()) {
        alert('Error in query: ' + response.getMessage() + ' ' + response.getDetailedMessage());
        return;
      }
    
      var data = response.getDataTable();
      var options = {
        title: "Weight History",
        width: 700,
        height: 500,
        bar: {groupWidth: "95%"},
        legend: { position: "none" },
      };
      visualization = new google.visualization.ColumnChart(document.getElementById('visualization'));
      visualization.draw(data, options);
    }
    
    google.setOnLoadCallback(drawVisualization);
    </script>

Compared with hard-coding data, the difference is only a few lines:

    var query = new google.visualization.Query(
          'https://docs.google.com/spreadsheet/ccc?key=0AiA3av6cH1otdHlUMGQxcDhHOU0xX004QV9DWmlESGc&amp;usp=sharing');
    query.setQuery('select A, B');
    
    // Send the query with a callback function.
    query.send(handleQueryResponse);

'select A, B' is a SQL statement without FROM, which fetches Column A and B of the spreadsheet. The rest is self explanory. 

Pretty cool huh. New skill get√. There are pie charts, geography intensity charts, 3D plot, a bunch of cool stuff. Cannot get bored.

A few more words on running javascript on Jekyll. Just pay attention to:
1. Markdown is white-space sensitive, align &lt;scripts&gt;&lt;/scripts&gt; properly and eliminate unnecessary spaces.
2. Each &lt;script&gt;&lt;/script&gt; must be seperated by a blank line, otherwise the latter wont't executed. The same rule applies to &lt;div&gt;&lt;/div&gt; and other blocks.
3. Ampersand is NOT allowed in code block, even in url you have to escape it by `&amp;`.

Or, just rake a empty post and try Hello World.

    <script>
        alert("Hello World!");
    <script>

You'll figure out. 


