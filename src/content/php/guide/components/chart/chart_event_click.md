<meta>
{
    "title": "Chart click events",
    "subtitle": "",
    "index": 5,
    "id": "chart_event_click"
}
</meta>

You can execute a PHP function when an item on the chart has been clicked, by using the {{ linkApi("php", "Component", "bindToEvent") }} function. This function is executed whenever an item (like a line chart circle, column chart rectangle, etc.) is clicked.

~~~
$chart->bindToEvent ("itemClick", array($chart), "handleItemClick");

private function handleItemClick($source, $target, $params){
  $chart = $this->getComponentByID("chart1");
  echo "Chart Label: $params->label";
  echo "Chart Value: $params->value";
}
~~~

In your function, declare three arguments called `$source`, `$target` and `$params` The `$params` contains the  properties:

* **value**: The value of the item that was clicked (purely numeric, this will not contain formatted values like number prefix/suffix, etc)
* **label**: The x-axis label that corresponds to the item that was clicked.
* **labelIndex**: The index of the label (starting from 0) that corresponds to the item that was clicked.
