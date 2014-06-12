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
    $chart = new ChartComponent("my_first_chart");
    $chart->setCaption("Expenses incurred on Food Consumption by Year");
    $chart->setDimensions (4, 4);
    $chart->setLabels (["2009", "2010", "2011"]);
    $chart->addSeries ("beverages", "Beverages", [1355, 1916, 1150]);
    $chart->addSeries ("packaged_foods", "Packaged Foods", [1513, 976, 1321]);
~~~

Then create a chart Drill into Modal by creating a chart to be drilled and then hide it, by using the {{ linkApi("php", "Component", "hideComponent") }} function. 

~~~
    $chart1 = new ChartComponent("2011_sales");
    $chart1->setCaption("2011 Sales");
    $chart1->setDimensions (4, 4);
    $chart1->setLabels (["Beverages", "Vegetables"]);
    $chart1->addSeries ("sales", "Sales", [1343, 7741]);
    $chart1->addSeries ("quantity", "Quantity", [76, 119]);
    $chart1->hideComponent();
~~~

Add both the chart to Dashboard.

~~~
    $this->addComponent ($chart);
    $this->addComponent ($chart1);
~~~

Set a javaScript callback when an item on the chart has been clicked, by using the {{ linkApi("php", "ChartComponent", "onItemClick") }} function. Within this callback we need to show the chart in the modal, by using the {{ linkApi("php", "Component", "showAsModal") }}.

~~~
    $chart->onItemClick (array($chart, $chart1), "handleItemClick", $this);

    public function handleItemClick ($source, $targets, $params) {
        $chart1 = $this->getComponentByID('2011_sales');
        $chart1->showAsModal();
    }
~~~

### Complete example

{{embedExample("php", "chart_drill_into_modal")}}
