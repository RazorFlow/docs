<meta>
{
    "title": "Chart Drill into Modal",
    "subtitle": "",
    "index": 9,
    "id": "chart_drill_into_modal"
}
</meta>

### Chart Drill into Modal

First create a regular chart.

~~~
	var chart = new ChartComponent();
    chart.setDimensions (4, 4);
    chart.setCaption("2011 Sales"); 
    chart.setLabels (["Beverages", "Vegetables"])
    chart.addSeries ("sales", "Sales", [1343, 7741]);
    chart.addSeries ("quantity", "Quantity", [76, 119]);
~~~

Then create a chart Drill into Modal by creating a chart to be drilled and then hide it, by using the {{ linkApi("js", "Component", "hideComponent") }} function. 

~~~
    var chart1 = new ChartComponent('someid');
    chart1.setDimensions (4, 4);
    chart1.setCaption("Expenses incurred on Food Consumption by Year");
    chart1.setLabels (["2009", "2010", "2011"]);
    chart1.addSeries ("beverages", "Beverages", [1355, 1916, 1150]);
    chart1.addSeries ("packaged_foods", "Packaged Foods", [1513, 976, 1321]);
    chart1.hideComponent();
~~~

Add both the chart to Dashboard.

~~~
    db.addComponent (chart);
    db.addComponent (chart1);
~~~

Set a javaScript callback when an item on the chart has been clicked, by using the {{ linkApi("js", "ChartComponent", "onItemClick") }} function. Within this callback we need to show the chart in the modal, by using the {{ linkApi("js", "Component", "showAsModal") }}.

~~~
    chart.onItemClick(function(params) {
        chart1.showAsModal();
    });
~~~

### Complete example

{{embedExample("js", "chart_drill_into_modal")}}