<meta>
{
    "title": "Chart Drill into Modal",
    "subtitle": "",
    "index": 9,
    "id": "chart_drill_into_modal"
}
</meta>

### Chart Drill into Modal

You can create a chart Drill into Modal by creating a chart to be drilled and then hide it, by using the {{ linkApi("js", "Component", "hideComponent") }} function. 

~~~
	var chart = new ChartComponent();
    chart.setDimensions (4, 4);
    chart.setCaption("My First Chart"); 
    chart.setLabels (["Jan", "Feb", "Mar"]);
    chart.addSeries ("beverages", "Beverages", [1355, 1916, 1150]);
    chart.addSeries ("packaged_foods", "Packaged Foods", [1513, 976, 1321]);
    chart.hideComponent();
    db.addComponent (chart);
~~~

Then create a regular chart by setting a javaScript callback when an item on the chart has been clicked, by using the {{ linkApi("js", "ChartComponent", "onItemClick") }} function. Within this callback we need to show the chart in the modal, by using the {{ linkApi("js", "Component", "showAsModal") }}.

~~~
	var chart1 = new ChartComponent();
    chart1.setDimensions (4, 4);
    chart1.setCaption("My First Chart"); 
    chart1.setLabels (["Jan", "Feb", "Mar"]);
    chart1.addSeries ("beverages", "Beverages", [1355, 1916, 1150]);
    chart1.addSeries ("packaged_foods", "Packaged Foods", [1513, 976, 1321]);
    db.addComponent (chart1);


	chart1.onItemClick(function(params) {
        chart.showAsModal();
    });
~~~

### Complete example

{{embedExample("js", "chart_drill_into_modal")}}