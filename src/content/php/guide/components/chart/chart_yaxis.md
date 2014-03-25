<meta>
{
    "title": "Configuring the Y-Axis of the chart",
    "subtitle": "",
    "index": 3,
    "id": "chart_yaxis"
}
</meta>

Some charts with a Y Axis can be configured. The aspects of the Y Axis that can be currently customized are:

1. The name of the Y-Axis
2. The number formatting of the Y AXis.

To do this, you will need to use the {{ linkApi("php", "ChartComponent", "setYAxis") }} function.

~~~
    $chart->setYAxis("Sales", array(
      "numberPrefix" => "$ "
    ));
~~~

1. The first parameter is the name of the Y Axis
2. The second optional parameter is an object containing **Standard number formatting properties**.

### Complete example

{{ embedExample ('php', 'chart_yaxis') }}
